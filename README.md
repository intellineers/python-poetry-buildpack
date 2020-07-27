# Python Poetry Buildpack

A [Heroku](https://devcenter.heroku.com/) Buildpack for [Poetry](https://github.com/python-poetry/poetry) users.

## How to use

The Python Poetry Buildpack prepares the build to be processed by a Python buildpack such as `heroku/python` by generating `requirements.txt` and `runtime.txt` from `poetry.lock`.

To set up the use of several buildpacks from the Dokku CLI use `buildpacks:add`:

```
dokku buildpacks:clear
dokku buildpacks:add https://github.com/moneymeets/python-poetry-buildpack.git
dokku buildpacks:add https://github.com/heroku/heroku-buildpack-python.git
```

You can specify a private pypi repository server url by specifying the config variable `PYPI_EXTRA_INDEX_URL`:
```
dokku config:set app-name PYPI_EXTRA_INDEX_URL=https://username:password@pypi.stainly.com/
```

## Acknowledgement

This work is based on the previously proposed [python poetry builpacks](https://github.com/moneymeets/python-poetry-buildpack). It simply extends the possibility to add --extra-index-url upon requirement.txt file generation