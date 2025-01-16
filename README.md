# Github compisite action to setup SSH

Usage:
```yaml
on: [push]

jobs:
  hello_world_job:
    runs-on: ubuntu-latest
    name: A job to say hello
    steps:
      - uses: actions/checkout@v4
      - uses: webbmaffian/ssh-action@v1
        with:
          SSH_PRIVATE_KEY: ${{ secrets.SSH_PRIVATE_KEY }}
          REMOTE_HOST: ${{ secrets.REMOTE_HOST }}
          REMOTE_USER: ${{ secrets.REMOTE_USER }}
      - name: Execute remote job
        run: rsync -a ${{ github.workspace }}/stuff/ remote:/tmp/stuff/
        shell: bash
```