# aws-profiles

The purpose of this script is to switch between profiles found in the AWS config
file.

This is a script that needs to be sourced in the current shell to work.

The script needs [fzf](https://github.com/junegunn/fzf) to work.

## Usage

First you need to ensure the functions are sourced in your shell, eg.:

```
source lib/aws-profiles
```

After that aws-profiles command can be used to switch between aws profiles

```
aws-profiles
```
