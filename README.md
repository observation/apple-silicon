# Installing developer tools on Apple Silicon

This is how I got things to work on Apple Silicon.

## Getting started

1. [Terminal](terminal.md)
1. [Homebrew](brew.md)
1. [pyenv](pyenv.md)
1. [PostgreSQL and PostGIS](postgres.md)
1. [gevent](gevent.md)
1. [redis](redis.md)

## Other resources on this subject

See [Links](links.md).

## Make this better

Feel free to suggest improvements and extra tips using pull requests.

## Credits

Thanks to everybody who shared tips and code!

If I used a tip I found online, I credited with a link in the article.

A special mention here for [A wrapper script for brew](https://binx.io/blog/2019/04/12/installing-pyenv-on-macos/). This is my favorite solution for `brew`, and it also gave me the idea to fix `pyenv`. I added some improvements to make `brew` also play nice with Postgres.app.