# pyenv

## Prerequisites

You must have [`brew` installed according to the instructions in this project](brew.md).

## Instructions

### pyenv

We install `pyenv` using `brew`. Type this command in Terminal:

```
brew install pyenv
```

You can also add `virtualenv` with `brew install pyenv-virtualenv`.

Because `pyenv` is a series of scripts, we want to make sure that these scripts are always run in emulation mode.

Create a file `~/bin/pyenv` with the following content:

```
#!/bin/sh
# assumes default location of pyenv in `/usr/local/bin/pyenv`
arch -x86_64 /usr/local/bin/pyenv "$@"
```

Make this file executable:

```
chmod gu+rx ~/bin/pyenv
```

Now when we call pyenv, it will always be in x86 mode.

To make `pyenv` work, we have to make some changes to `~/.zshrc`. Add the following:

```
# Configure pyenv
export PYENV_ROOT="$HOME/.pyenv"
export PATH="$PYENV_ROOT/bin:$PATH"
if which pyenv > /dev/null; then eval "$(pyenv init -)"; fi
if which pyenv-virtualenv-init > /dev/null; then eval "$(pyenv virtualenv-init -)"; fi
```

To make `pyenv` and brew place nice, we have to modify the script we use to run `brew`. Every time we run brew, we want to modify our `PATH` so that the pyenv shims are removed.

Edit `~/bin/brew`, and change its contents to this:

```
#!/bin/sh
# Remove Postgres.app config
BREWPATH="${PATH//:\/Applications\/Postgres.app\/Contents\/Versions\/latest\/bin/}"
# Check if pyenv is available, if so remove shims from path
if which pyenv >/dev/null 2>&1; then
  BREWPATH="${BREWPATH//$(pyenv root)\/shims:/}"
fi
# Assumes default location of brew in `/usr/local/bin/brew`
arch -x86_64 /usr/bin/env PATH="$BREWPATH" /usr/local/bin/brew "$@"
```

If you do not use Postgres.app, you can make a simpler version, but this will also work.

And we're done, when you restart your Terminal you have both `brew` and `pyenv` running in x86 mode, and no complaints from `brew doctor`.
