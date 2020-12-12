# Python

We will install Python 3.8.4 using `pyenv`.

## Prerequisites

Install `pyenv`.

## Instructions

Install some prerequisites

```
brew install openssl readline sqlite3 xz zlib bzip2
```

Set compiler flags, add this to the beginning of your `~/.zshrc`

```
# Set compiler flags from Homebrew
export LDFLAGS="-L/usr/local/opt/zlib/lib -L/usr/local/opt/bzip2/lib"
export CPPFLAGS="-I/usr/local/opt/zlib/include -I/usr/local/opt/bzip2/include"
```

Install Python 3.8.4

```
pyenv install 3.8.4
```

## A note on pip

Some packages will fail to install on an ARM Mac if you have a slightly outdated `pip`.

After creating a virtualenv, always update pip before you do anything else.

So, for example:

```
pyenv virtualenv 3.8.4 foo
pyenv activate foo
pip install -U pip
```
