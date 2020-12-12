# Homebrew

## Prerequisites

You should not already have homebrew installed. Uninstall any earlier attempts. Also check your `~/.zshrc` for any aliases or other tricks.

## Instructions

We install brew in x86 mode. Type this command in Terminal:

```
arch -x86_64 /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install.sh)"
```

This installs `brew` in its regular location.

To make sure that the brew command and the installed packages can be found, I change my `PATH` in `~/.zshrc`.

```
# Add my /usr/local/bin to PATH
# This also contains Homebrew's `brew` command in x86 arch
export PATH="/usr/local/bin:$PATH"

# My personal scripts come first
export PATH="$HOME/bin:$PATH"
```

Notice that personal scripts in the `bin` folder in my home directory have priority over the `brew` command and Homebrew packages. This is important.

Now I want to make sure that brew is always called in x86 mode. You can do this by forcing the entire Terminal app, or by making an alias, but I will take a different approach and use a small script. This script will also help us to make `brew` place nice with pyenv.

Create a file `~\bin\brew` with the following content:

```
#!/bin/sh
# Assumes default location of brew in `/usr/local/bin/brew`
arch -x86_64 /usr/local/bin/brew "$@"
```

Make this file executable

```
chmoud gu+rx ~/bin/brew
```

Now every time we call the `brew` command, this script will prefix it with the `arch -x86_64` command to make sure it runs in x86 mode.

Type `brew doctor` to confirm. You see this result:

```
brew doctor
Your system is ready to brew.
```

If `brew doctor` says anything else, be sure to follow up. A common issue is fixing the rigts for several folders.

We're done, we now have Homebrew installed in x86 mode.
