NAIS Java 10 baseimage
=====================

Basic Usage
---------------------

We support three ways of running your app:

1. A fat jar called `app.jar`
2. An exploded war
3. Startup script generated using Maven Assembly og Gradle's `installDist`

Create a `Dockerfile` containing:

### Simplest example
The simplest way of running your app is to create a far jar and copy it into your container as `app.jar`.
Since the default working directory is `/app`, there's no need to specify the path.

```Dockerfile
FROM navikt/java:10
COPY target/my-awesome.jar app.jar
```

### Using gradle?

You can use `gradle installDist` by making sure the startup script is
copied into the docker container as `/app/bin/app`. Here's an example:

```
FROM navikt/java:10

COPY build/install/myapp/bin/myapp bin/app
COPY build/install/myapp/lib ./lib/
```

### Using exploded WAR?

Supply the name of your main class as an environment variable called
`MAIN_CLASS` if the name of your main class is not the default "Main".

## Customisation

Custom runtime options may be specified using the environment variable `JAVA_OPTS`.

# Changelog
All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](http://keepachangelog.com/en/1.0.0/)

## 2018-10-05
- curl installation

## 2018-09-14

### Added
- Support for exploded war.

### Changed
- Added support for naisd proxy settings.

## 2018-09-11

### Fixed
- `run-java.sh` execute bit set so it is runnable.

## 2018-09-10

### Added
- Support for `gradle installDist` files.

## 2018-08-10
### Added
- Initial JDK 10 image built.
