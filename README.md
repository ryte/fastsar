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

## Usage
Most shells do not allow to set environments from sub-shells,
so this script returns a string that can be evaluated in the current shell.

In bash this can be done with `eval $(fastsar)`,
in fish this can be done with `eval (fastsar)`.

You can also bind the evaluation to some hotkey, like 'Alt+s'

- bash: `bind -x '"\es": eval $(fastsar)'`
- fish: `bind \es 'eval (fastsar)'`


If the script has problems detecting your shell, you can pass the shell's name
as first parameter (e.g. `fastsar fish`).

## How to install
Locate your nearest `bin` folder, for example `~/.bin`, and edit the following few lines accordingly:

```bash
cd ~/projects/ryte  # This is where you normally pull your ryte tools to.
git clone git@github.com:ryte/fastsar.git
cd fastsar
ln -s $(pwd)/fastsar ~/.bin/  # Edit this, please.
chmod +x ~/.bin/fastsar
```

After this, you should be able to run `fastsar`.

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
