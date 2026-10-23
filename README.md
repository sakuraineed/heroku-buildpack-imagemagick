heroku-buildpack-imagemagick
=================================

This is a [Heroku buildpack](http://devcenter.heroku.com/articles/buildpacks) for vendoring the ImageMagick binaries into your project.

## Install

Add the buildpack to your app...

`heroku buildpacks:add https://github.com/socialjazz/heroku-buildpack-imagemagick  --index 1 --app HEROKU_APP_NAME`

_Note: The `--index 1` puts that imagemagick buildpack first._

## Setting (or Changing) your ImageMagick version

1. Go to https://github.com/ImageMagick/ImageMagick/tags and find the version number (tag name) that you want.
2. Set the config on your app: `heroku config:set IMAGE_MAGICK_VERSION=6.9.13-16 -a HEROKU_APP_NAME`
3. Redeploy your app to Heroku to trigger the install

Check out [the ImageMagick changelog](https://github.com/ImageMagick/Website6/blob/main/ChangeLog.md) if you want details on fixes and new features.

---

### Cache Issue

If there is an issue with a bad build of ImageMagick getting stuck in the build cache, the following command will purge the cache and allow for a fresh build -- that first build will run much slower.

1. `heroku plugins:install heroku-builds`
2. `heroku builds:cache:purge -a HEROKU_APP_NAME`
