# aws-sessions

This is a helper script for managing aws sessions using MFA.

To use it you need a profile configured with your access keys, eg:

```dosini
[profile default]

[profile default-session]
credential_process = aws-sessions get default

[profile admin]
source_profile = default-session
region = eu-central-1
role_arn = arn:aws:iam::111111111111:role/AdminRole 
```

With this config when using aws sdk (eg. through the CLI), you don't need to
care much about the aws-sessions command during the day.

On first run, you'll be notified to fetch a session:

```
$ aws s3 ls --profile admin

Error when retrieving credentials from custom-process: No valid AWS token found.
Please run the following command to create a new session:

    aws-sessions create default
```


Let's create a session as prompted by the s3 command

```
$ aws-sessions create default
Using MFA Device: arn:aws:iam::478869617778:mfa/zoltan.reegn
Code: 123456

Successfully created AWS Session.
```

Now we can use the aws cli for the length of the session without worrying about
MFA again:

```
❯ aws s3 ls
2019-11-01 11:12:13 bucket-a.example.com
2019-11-02 14:15:16 bucket-b.example.com
2019-11-03 17:18:19 bucket-c.example.com
...
```

