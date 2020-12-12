# Terminal

Your Terminal.app is allowed to run in Apple Silicon mode. You do not need a Rosetta Terminal.

By prefixing commands with `arch -x86_64` we force Rosetta 2 emulation, or "x86 mode".

For example

```
arch -x86_64 ls
```

This runs the `ls` command in x86 mode.