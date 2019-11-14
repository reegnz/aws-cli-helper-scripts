# aws-console-login

The purpose of this script is to generate a login link for the active AWS
profile.

The script assumes that it gets the profile name as it's first argument, or
that the profile name is already set by the `AWS_PROFILE` environment variable.

# Usage

You can either set the `AWS_PROFILE` environment variable and use the command
without arguments:

```
export AWS_PROFILE=admin
aws-console-login
```

Or you can explicitly define the profile name as the first argument:

```
aws-console-login admin
```
