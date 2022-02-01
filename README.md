# PiCode SSH Action

Easily access a remote server with ssh.

_Note: This is meant to be used on an Ubuntu machine version 20.04.03 or newer._

## Usage

```yml
- uses: picodebr/ssh-action@v1
  with:
    # remote server private ssh key (required)
    ssh_key: ""

    # remote server username (required)
    ssh_user: ""

    # remote server address (required)
    ssh_host: ""

    # commands to be executed in the remote host (required)
    command: ""
```

## Example

The following example shows how to list the remote host home directory everytime the master branch is updated.

```yml
name: Deploy node.js

on:
  push:
    branches: [master]

jobs:
  main:
    runs-on: ubuntu-latest
    steps:
      - name: List remote home directory
        uses: picodebr/ssh-action@v1
          with:
            ssh_key: ${{ secrets.SSH_KEY }}
            ssh_user: ${{ secrets.SSH_USER }}
            ssh_host: ${{ secrets.SSH_HOST }}
            command: ls ~
```
