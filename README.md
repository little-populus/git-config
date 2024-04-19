# git-config

## some useful configuration

```bash
git config --global core.editor vim
```

This sets the default editor to vim.

```bash
git config --global commit.template ~/.gitmessage.txt
```

This sets a default commit message template.

```bash
git config --global help.autocorrect 1
```

This enables autocorrection of commands.Awaiting time is 0.1 seconds.

```bash
git config --global help.autocorrect 0
```

to disable it, you can use above command.

```bash
git config --global core.autocrlf true
```

This enables automatic conversion of line endings on commit.

```bash
git config --global core.autocrlf false
```

And if you want to disbale it, you can use above command.

---

if you use https transport protocol, you can use below command to avoid typing password every time you push or pull.

```bash
git config --global credential.helper store
```

This stores your credentials in a global cache so that you don't have to type them in every time you push or pull.

one thing you have to note is that this command will store your credentials in plain text, so make sure to use it with caution.

when you use pull or push command, it will search file which stores your credentials in your home directory,default path is ~/.git-credentials. If it doesn't find any file, it will ask you to enter your credentials. Make sure to keep your credentials safe.

if you want to indicate a specific path for your credentials file, you can use below command.

```bash
git config --global credential.helper 'store --file ~/.my-credentials'
```

This will store your credentials in a file named ~/.my-credentials.
and once you pull or push command, it will search file which stores your credentials in ~/.my-credentials.

the method of storing credentials in a file is using the following command.

```bash
echo "https://username:password@example.com" > ~/.my-credentials
```

and git also provides a way to store credentials.

```bash
git credential-store --file ~/.my-credentials store
```

This will store your credentials in a file named ~/.my-credentials.

then you need input protocol, hostname, username and password when you pull or push command.

here is a example of how to use it.

```bash
git credential-store --file ~/.my-credentials store

# input protocol, hostname, username and password

protocol=https
host=example.com
username=username
password=password
```

if you want get username and password from the file, you can use below command.

```bash
git credential-store --file ~/.my-credentials get

protocol=https
host=example.com
```

same thing happens when you try to get credentials from the file.

one thing need to note is that input all messages then press enter,means you need input a empty line to finish your input.

```bash
git credential-store --file ~/.my-credentials erase
```

This will erase your credentials from the file ~/.my-credentials.
