# Ember Test Container

A Dockerfile to build [PhantomJS](https://github.com/ariya/phantomjs)@2.0.0 [nodejs](https://github.com/nodejs)@0.12.7 [ruby](https://www.ruby-lang.org/)2.2.x
[bower](https://github.com/bower/bower)@latest exclusively set for testing
[ember-cli](https://github.com/ember-cli/ember-cli) [ember](https://github.com/emberjs/ember.js/) ambitious web applications
using [Ubuntu](https://www.ubuntu.com/) 14.04 distribution.

## Get image

There is an [Automated Build on hub.docker.com](https://hub.docker.com/r/turbomack/ember-test-container/), so getting the image is easy:

```bash
$ docker pull turbomack/ember-test-container:latest
```

## Run it

Run it from inside a Docker container:

```bash
$ docker run -it --rm turbomack/ember-test-container
```

## Build image from repository

You can build this image on your own. Compilation of phantomjs takes about half hour to up to five hours so be prepared that first build will take a long time!

```bash
$ git clone git@github.com:turboMaCk/ember-test-container.git
$ cd ember-test-container
$ docker build -t turbomack/ember-test-container:latest .
```

## Wercker integration

You can use this image for automated build in [Wercker](http://wercker.com/). Check [wercker.yml](wercker.yml) for more info.

Then you can build app in wrecker localy using [wercker-cli](http://devcenter.wercker.com/docs/using-the-cli/index.html):

```bash
$ wercker build --direct-mount

```

## node-sass

Local Wecker build do not work well with `node-sass` because of the binary dependecies with `libsass`. Anyway it works just fine with Wercker cloud.
However you can add cleaning `node_modules` to build steps for testing wercker build with wercker-cli or remove it manualy right before you run `wercker build`
(this will break build in your host machine enviroment so do not forget to `rm -rf node_modules` and run `npm install` after wercker finish).


## Credits
Thanks to @rosenhouse for his [phantomjs2](https://hub.docker.com/r/rosenhouse/phantomjs2/) image which help me a lot with setting up compilation of Phantomjs@2.0.0.

