screen-share
------------

A set of scripts to stream your terminal to the web browser.

## Features

- ephemeral hidden service support
- password protected
- read-only

## Future

This project is a quick blueprint, I may change some things in the future.

For example:

- I don't like bash, but it was written in bash, so this is an issue I may address in the future.
- It is not feature rich

## Presenter requirements

- [tor](https://www.torproject.org/)
- [gotty](https://github.com/yudai/gotty)
- [tmux](https://github.com/tmux/tmux)

## Viewer requirements

- [tor](https://www.torproject.org/) browser

Also you may want to give a try to the [gotty terminal client](https://github.com/moul/gotty-client) to view other
people terminal inside your terminal instead of browser.

## How to use

You will need two terminal tabs.

* one for tor service
* second for gotty

In the first tab run:

> Add `-e` flag to run ephemeral hidden service(this means that old host keys will be discarded on another start).

``` shell
./tor/start
```

It will start tor and configure ephemeral hidden service for you.
It will output something similar to:

``` text
Apr 10 11:10:10.000 [notice] Bootstrapped 100%: Done
Started hidden service aqyx3ccgqtqcvhnj.onion
```

Now start a tty script which will load gotty and generate random password:

> You may specify user and password with environment variables `TTY_USER` and `TTY_PASSWORD`.

``` shell
./tty/start tmux a -t tty
```

Now when client connects `tmux a -t tty` will be executed.

Last step is:

- Start tmux
- And rename your session to tty `C-b :`, type `rename session tty`

You done.

> `gotty` requires javascript in tor browser to work.

Send your `.onion` hostname, user and password to your friends so they could see you.
