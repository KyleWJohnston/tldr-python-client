# tldr-python-client

[![PyPI Release](https://img.shields.io/pypi/v/tldr.svg)](https://pypi.python.org/pypi/tldr)
[![Build Status](https://travis-ci.org/tldr-pages/tldr-python-client.svg)](https://travis-ci.org/tldr-pages/tldr-python-client)

A `Python` command line client for [tldr](https://github.com/tldr-pages/tldr).

![tldr screenshot](http://raw.github.com/tldr-pages/tldr/master/images/screenshot.png)

## Installation

### from PyPI

    pip install tldr

### from Arch Linux repository

    sudo pacman -S tldr

### from Fedora packages repository

    sudo dnf install tldr

## Usage

    tldr <command>

## Configuration

You can configure the behaviour and output of the `tldr` client by setting environment variables. For example, to set the same as the defaults in the `.bashrc` file:

    export TLDR_COLOR_BLANK="white"
    export TLDR_COLOR_NAME="cyan"
    export TLDR_COLOR_DESCRIPTION="white"
    export TLDR_COLOR_EXAMPLE="green"
    export TLDR_COLOR_COMMAND="red"
    export TLDR_COLOR_PARAMETER="white"
    export TLDR_CACHE_ENABLED=1
    export TLDR_CACHE_MAX_AGE=720

For light terminal themes, the following colors are recommended:

    export TLDR_COLOR_BLANK="yellow"
    export TLDR_COLOR_NAME="yellow"
    export TLDR_COLOR_DESCRIPTION="yellow"
    export TLDR_COLOR_EXAMPLE="green"
    export TLDR_COLOR_COMMAND="red"
    export TLDR_COLOR_PARAMETER="yellow"

### Cache

* `TLDR_CACHE_ENABLED` (default is `1`):
    * If set to `1`, the client will first try to load from cache, and fall back to fetching from the internet if the cache doesn't exist or is too old.
    * If set to `0`, the client will fetch from the internet, and fall back to the cache if the page cannot be fetched from the internet.
* `TLDR_CACHE_MAX_AGE` (default is `24`): maximum age of the cache in hours to be considered as valid when `TLDR_CACHE_ENABLED` is set to `1`.

#### Cache location in order of precedence

* `$XDG_CACHE_HOME/tldr`
* `$HOME/.cache/tldr`
* `~/.cache/tldr`
* Previously, the cache resided in `$HOME/.tldr_cache`

If you are experiencing issues with *tldr*, consider deleting the cache files before trying other measures.

### Colors

Values of the `TLDR_COLOR_x` variables (see list above) may consist of three parts:
* Font color, *required*: `blue, green, yellow, cyan, magenta, white, grey, red`
* Background color: `on_blue, on_cyan, on_magenta, on_white, on_grey, on_yellow, on_red, on_green`
* Additional effects, which depends on platform: `reverse, blink, dark, concealed, underline, bold`

Examples:
* `TLDR_COLOR_DESCRIPTION="white"` for white text on default system background color without any effects
* `TLDR_COLOR_NAME="cyan dark"` for dark cyan text on default system background color
* `TLDR_COLOR_PARAMETER="red on_yellow underline"` for underlined red text on yellow background
