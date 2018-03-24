# *f*zf *A*WS *sts* *A*ssume*R*ole

A bash script to switch between
[AWS Roles](https://docs.aws.amazon.com/STS/latest/APIReference/API_AssumeRole.html)
quickly using
[fzf](https://github.com/junegunn/fzf)

## Features
- Assume AWS role with minimum keystrokes
- All AWS roles accessible in one place
- Pre-selects last used account/role
- Only requires user input if there are more than one accounts/roles

## Config
Create a json file with all your accounts and roles in the following format in
`$HOME/.aws/sts.json` (configurable as `$CONF`)

```
[
    {
        "name": "Production",
        "id": "1234",
        "roles": [
            "abc",
            "def"
        ]
    },
    {
        "name": "Testing",
        "id": "14253",
        "roles": [ "abc" ]
    }
]
```

- `name`: Some name for your account
- `id`: The AWS account ID
- `roles`: List of AWS role names you want to assume

## Requirements
- [fzf](https://github.com/junegunn/fzf)
- [jq](https://github.com/stedolan/jq)
- [aws cli](https://github.com/aws/aws-cli)
- optional: a lot of AWS accounts
