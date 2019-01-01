# posehub

Init a project starter by yaml configuration

This repo is used as a warehouse for [devpose-cli](https://github.com/devpose/devpose-cli)

## Syntax

Config file is wrote with [yaml](https://yaml.org/)

### Structure

```
version: 0.0.1
commands:
  - common cmd
  - devpose:
      command: CreateFlatFile
      name: <file-name>
      content: <devpose-command-related-content-flat>
  - devpose:
      command: CreateYamlFile
      name: <file-name>
      content: <devpose-command-related-content-yaml>

<devpose-command-related-content-flat>:
  - common cmd foo
  - common cmd bar

<devpose-command-related-content-yaml>:
  version: '1'
  foo:
    bar: hello world
```

`commands` defined some commands to create a project starter.

`devpose-cli` run those commands one by one synchronously.

**`common cmd`** means any commands that can be executed in our terminal directly, like `cd path` or `git clone url` and so on.

**`devpose`** means some custom operations like create a file with some content when run the devpose-cli.

### Custom operation

Currently supported two operations `CreateFlatFile` and `CreateYamlFile` which supported to create customize file.

Under devpose, there is a key called `content`, it's a `link` to a root structure in yaml file.

Every time cli come to `CreateFlatFile` or `CreateYamlFile`, will use the `content` field to find related file content and create a file with the `name` field as file name.

**`CreateFlatFile`**

Create file in flat, just one line by one line without special format.

**`CreateYamlFile`**

Create file in yaml format

## Examples

[node-react-docker](https://github.com/devpose/posehub/blob/master/ymls/node-react-docker.yml)
