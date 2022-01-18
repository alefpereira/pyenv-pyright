# pyenv-pyright

pyenv-pyright is a [pyenv](https://github.com/pyenv/pyenv) plugin to help setup [Microsoft Pyright](https://github.com/microsoft/pyright) LSP Server to use
virtualenv for local projects. This plugin helps to create or update `venvPath` and `venv`
attributes in pyright config file `pyrightconfig.json` to pyenv virtualenvs.

This plugin may come in handy when working with pyright in [neovim](https://github.com/neovim/neovim) while using pyenv to manage
your virtualenvs, since pyright doesn't uses pyenv set with `pyenv local`, a good way to overcome
this problem is to explicitly set the desired venv in pyright config file `pyrightconfig.json`.
So with this plugin you can do this with only one command:

```
pyenv pyright
```

## Installation

This will install the latest development version of `pyenv-pyright` into the `$(pyenv root)/plugins/pyenv-pyright` directory.

**Important note:** If you installed pyenv into a non-standard directory, make sure that you clone this repo into the 'plugins' directory of wherever you installed into.

```
$ git clone https://github.com/alefpereira/pyenv-pyright.git $(pyenv root)/plugins/pyenv-pyright
```

## Usage

- From an activated pyenv virtualenv (set by `pyenv local`
for example) run `pyenv pyright` to set pyright config file
to this venv:

```
 (myvenv) pyenv pyright
```

- Considering you have a pyenv virtualenv named `myvenv`,
to set pyright config file to use this virtualenv,
pass it as argument:

```
 pyenv pyright myvenv
```

**Note:** It works only for virtualenvs, it doesn't work for python
instalations i.e `3.10.0`.

- Command help:

```
pyenv pyright --help

Usage: pyenv pyright [virtualenv]
       pyenv pyright --help

       [virtualenv] should be a Python version known to pyenv.
```

## Additional Notes

### Update existing `pyrightconfig.json` file:

This script creates pyright LSP server config file `pyrightconfig.json`
in the current directory, setting its `venv` attribute to
selected virtualenv and `venvPath` to `PYENV_ROOT/versions`.
If `pyrightconfig.json` file already exists, the script will update those
attributes in the existing file instead.

### Uses [pyenv-virtualenv](https://github.com/pyenv/pyenv-virtualenv)
for virtualenv management and command completions:

The pyenv-pyright plugin **supports only virtualenvs known to pyenv**,
and pyenv-virtualenv is the way to go for venv management in pyenv.
This plugin requires pyenv-virtualenv not only for the venvs but also
for command completions.

If your workflow don't involve using venvs or you don't use pyenv-virtualenv,
pyenv-pyright plugin may not have any use for you. But if you use venvs,
and use pyenv to manage python versions, you probably use pyenv-virtualenv
to manage venvs. If you installed pyenv using its installing tool
[pyenv-installer](https://github.com/pyenv/pyenv-installer) you already have
pyenv-virtualenv (if you are not sure check by running `pyenv virtualenvs`),
in case you don't have it installed yet, install it using the guide in 
[pyenv-virtualenv installing section](https://github.com/pyenv/pyenv-virtualenv#installing-as-a-pyenv-plugin)
or with the pyenv-installer tool.

##  License

[(The MIT License)](LICENSE)

* Copyright (c) 2015 Yamashita, Yuu

Permission is hereby granted, free of charge, to any person obtaining
a copy of this software and associated documentation files (the
"Software"), to deal in the Software without restriction, including
without limitation the rights to use, copy, modify, merge, publish,
distribute, sublicense, and/or sell copies of the Software, and to
permit persons to whom the Software is furnished to do so, subject to
the following conditions:

The above copyright notice and this permission notice shall be
included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND,
EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF
MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND
NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE
LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION
OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION
WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
