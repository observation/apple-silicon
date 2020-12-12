# Installing developer tools on Apple Silicon

This is how I got things to work on Apple Silicon.

## Getting started

1. [Terminal](terminal.md)
1. [Homebrew](brew.md)
1. [pyenv](pyenv.md)
1. [PostgreSQL and PostGIS](postgres.md)
1. [gevent](gevent.md)
1. [redis](redis.md)

## Credits

Thanks to everybody who shared tips and code!

### A wrapper script for brew

https://binx.io/blog/2019/04/12/installing-pyenv-on-macos/

This is my favorite solution for `brew`, and it also gave me the idea to fix `pyenv`. I added some improvements to make `brew` also play nice with Postgres.app.

### Other fixes

I added credits where I used a fix I found online.