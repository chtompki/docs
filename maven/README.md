<!--

********************************************************************************

WARNING:

    DO NOT EDIT "maven/README.md"

    IT IS AUTO-GENERATED

    (from the other files in "maven/" combined with a set of templates)

********************************************************************************

-->

# Supported tags and respective `Dockerfile` links

-	[`3.5.0-jdk-7`, `3.5-jdk-7`, `3-jdk-7` (*jdk-7/Dockerfile*)](https://github.com/carlossg/docker-maven/blob/ecf54b9839caed8aa2bcf9b8f7bb19594634ee89/jdk-7/Dockerfile)
-	[`3.5.0-jdk-7-onbuild`, `3.5-jdk-7-onbuild`, `3-jdk-7-onbuild` (*jdk-7/onbuild/Dockerfile*)](https://github.com/carlossg/docker-maven/blob/ecf54b9839caed8aa2bcf9b8f7bb19594634ee89/jdk-7/onbuild/Dockerfile)
-	[`3.5.0-jdk-7-alpine`, `3.5-jdk-7-alpine`, `3-jdk-7-alpine` (*jdk-7/Dockerfile*)](https://github.com/carlossg/docker-maven/blob/7e98522ee97c73c22da1b62329a0f20757bad5fb/jdk-7/Dockerfile)
-	[`3.5.0-jdk-7-onbuild-alpine`, `3.5-jdk-7-onbuild-alpine`, `3-jdk-7-onbuild-alpine` (*jdk-7/onbuild/Dockerfile*)](https://github.com/carlossg/docker-maven/blob/7e98522ee97c73c22da1b62329a0f20757bad5fb/jdk-7/onbuild/Dockerfile)
-	[`3.5.0-jdk-8`, `3.5.0`, `3.5-jdk-8`, `3.5`, `3-jdk-8`, `3`, `latest` (*jdk-8/Dockerfile*)](https://github.com/carlossg/docker-maven/blob/ecf54b9839caed8aa2bcf9b8f7bb19594634ee89/jdk-8/Dockerfile)
-	[`3.5.0-jdk-8-onbuild`, `3.5.0-onbuild`, `3.5-jdk-8-onbuild`, `3.5-onbuild`, `3-jdk-8-onbuild`, `3-onbuild`, `onbuild` (*jdk-8/onbuild/Dockerfile*)](https://github.com/carlossg/docker-maven/blob/ecf54b9839caed8aa2bcf9b8f7bb19594634ee89/jdk-8/onbuild/Dockerfile)
-	[`3.5.0-jdk-8-alpine`, `3.5.0-alpine`, `3.5-jdk-8-alpine`, `3.5-alpine`, `3-jdk-8-alpine`, `3-alpine`, `alpine` (*jdk-8/Dockerfile*)](https://github.com/carlossg/docker-maven/blob/7e98522ee97c73c22da1b62329a0f20757bad5fb/jdk-8/Dockerfile)
-	[`3.5.0-jdk-8-onbuild-alpine`, `3.5.0-onbuild-alpine`, `3.5-jdk-8-onbuild-alpine`, `3.5-onbuild-alpine`, `3-jdk-8-onbuild-alpine`, `3-onbuild-alpine`, `onbuild-alpine` (*jdk-8/onbuild/Dockerfile*)](https://github.com/carlossg/docker-maven/blob/7e98522ee97c73c22da1b62329a0f20757bad5fb/jdk-8/onbuild/Dockerfile)
-	[`3.5.0-jdk-9`, `3.5-jdk-9`, `3-jdk-9` (*jdk-9/Dockerfile*)](https://github.com/carlossg/docker-maven/blob/ecf54b9839caed8aa2bcf9b8f7bb19594634ee89/jdk-9/Dockerfile)
-	[`3.5.0-jdk-9-onbuild`, `3.5-jdk-9-onbuild`, `3-jdk-9-onbuild` (*jdk-9/onbuild/Dockerfile*)](https://github.com/carlossg/docker-maven/blob/ecf54b9839caed8aa2bcf9b8f7bb19594634ee89/jdk-9/onbuild/Dockerfile)

# Quick reference

-	**Where to get help**:  
	[the Docker Community Forums](https://forums.docker.com/), [the Docker Community Slack](https://blog.docker.com/2016/11/introducing-docker-community-directory-docker-community-slack/), or [Stack Overflow](https://stackoverflow.com/search?tab=newest&q=docker)

-	**Where to file issues**:  
	[https://github.com/carlossg/docker-maven/issues](https://github.com/carlossg/docker-maven/issues)

-	**Maintained by**:  
	[the Maven Project](https://github.com/carlossg/docker-maven)

-	**Published image artifact details**:  
	[repo-info repo's `repos/maven/` directory](https://github.com/docker-library/repo-info/blob/master/repos/maven) ([history](https://github.com/docker-library/repo-info/commits/master/repos/maven))  
	(image metadata, transfer size, etc)

-	**Image updates**:  
	[official-images PRs with label `library/maven`](https://github.com/docker-library/official-images/pulls?q=label%3Alibrary%2Fmaven)  
	[official-images repo's `library/maven` file](https://github.com/docker-library/official-images/blob/master/library/maven) ([history](https://github.com/docker-library/official-images/commits/master/library/maven))

-	**Source of this description**:  
	[docs repo's `maven/` directory](https://github.com/docker-library/docs/tree/master/maven) ([history](https://github.com/docker-library/docs/commits/master/maven))

-	**Supported Docker versions**:  
	[the latest release](https://github.com/docker/docker/releases/latest) (down to 1.6 on a best-effort basis)

# What is Maven?

[Apache Maven](http://maven.apache.org) is a software project management and comprehension tool. Based on the concept of a project object model (POM), Maven can manage a project's build, reporting and documentation from a central piece of information.

![logo](https://raw.githubusercontent.com/docker-library/docs/e2782b8942c1af41419536078c8d0176665a005d/maven/logo.png)

# How to use this image

## Create a Dockerfile in your Maven project

```dockerfile
FROM maven:3.2-jdk-7-onbuild
CMD ["do-something-with-built-packages"]
```

Put this file in the root of your project, next to the pom.xml.

This image includes multiple ONBUILD triggers which should be all you need to bootstrap. The build will `COPY . /usr/src/app` and `RUN mvn install`.

You can then build and run the image:

```console
$ docker build -t my-maven .
$ docker run -it --name my-maven-script my-maven
```

## Run a single Maven command

For many simple projects, you may find it inconvenient to write a complete `Dockerfile`. In such cases, you can run a Maven project by using the Maven Docker image directly, passing a Maven command to `docker run`:

```console
$ docker run -it --rm --name my-maven-project -v "$PWD":/usr/src/mymaven -w /usr/src/mymaven maven:3.2-jdk-7 mvn clean install
```

# Image Variants

The `maven` images come in many flavors, each designed for a specific use case.

## `maven:<version>`

This is the defacto image. If you are unsure about what your needs are, you probably want to use this one. It is designed to be used both as a throw away container (mount your source code and start the container to start your app), as well as the base to build other images off of.

## `maven:onbuild`

The `ONBUILD` image variants are deprecated, and their usage is discouraged. For more details, see [docker-library/official-images#2076](https://github.com/docker-library/official-images/issues/2076).

While the `onbuild` variant is really useful for "getting off the ground running" (zero to Dockerized in a short period of time), it's not recommended for long-term usage within a project due to the lack of control over *when* the `ONBUILD` triggers fire (see also [`docker/docker#5714`](https://github.com/docker/docker/issues/5714), [`docker/docker#8240`](https://github.com/docker/docker/issues/8240), [`docker/docker#11917`](https://github.com/docker/docker/issues/11917)).

Once you've got a handle on how your project functions within Docker, you'll probably want to adjust your `Dockerfile` to inherit from a non-`onbuild` variant and copy the commands from the `onbuild` variant `Dockerfile` (moving the `ONBUILD` lines to the end and removing the `ONBUILD` keywords) into your own file so that you have tighter control over them and more transparency for yourself and others looking at your `Dockerfile` as to what it does. This also makes it easier to add additional requirements as time goes on (such as installing more packages before performing the previously-`ONBUILD` steps).

## `maven:alpine`

This image is based on the popular [Alpine Linux project](http://alpinelinux.org), available in [the `alpine` official image](https://hub.docker.com/_/alpine). Alpine Linux is much smaller than most distribution base images (~5MB), and thus leads to much slimmer images in general.

This variant is highly recommended when final image size being as small as possible is desired. The main caveat to note is that it does use [musl libc](http://www.musl-libc.org) instead of [glibc and friends](http://www.etalabs.net/compare_libcs.html), so certain software might run into issues depending on the depth of their libc requirements. However, most software doesn't have an issue with this, so this variant is usually a very safe choice. See [this Hacker News comment thread](https://news.ycombinator.com/item?id=10782897) for more discussion of the issues that might arise and some pro/con comparisons of using Alpine-based images.

To minimize image size, it's uncommon for additional related tools (such as `git` or `bash`) to be included in Alpine-based images. Using this image as a base, add the things you need in your own Dockerfile (see the [`alpine` image description](https://hub.docker.com/_/alpine/) for examples of how to install packages if you are unfamiliar).

# License

View [license information](https://www.apache.org/licenses/) for the software contained in this image.
