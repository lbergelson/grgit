# grgit

The Groovy way to use Git.

[![Build Status](https://travis-ci.org/ajoberstar/grgit.png?branch=master)](https://travis-ci.org/ajoberstar/grgit)
[![Maintainer Status](http://stillmaintained.com/ajoberstar/grgit.png)](http://stillmaintained.com/ajoberstar/grgit)
[ ![Download](https://api.bintray.com/packages/ajoberstar/libraries/org.ajoberstar%3Agrgit/images/download.svg) ](https://bintray.com/ajoberstar/libraries/org.ajoberstar%3Agrgit/_latestVersion)

## What is this?

Grgit is a way to interact with Git repositories with a fairly fluent Groovy API. JGit can get pretty tedious to use, especially in a scripting context.

Grgit will also be the base for a rewrite of the [gradle-git plugin](https://github.com/ajoberstar/gradle-git).

## Where do I get it from?

Grgit is published on JCenter and Maven Central. As of 3/30/2014, not all dependencies are in JCenter.

```groovy
repositories {
	jcenter()
	mavenCentral()
}

dependencies {
	compile 'org.ajoberstar:grgit:<version>'
}

```

## How do I use it?

Start at the main entry point class [Grgit](http://ajoberstar.org/grgit/docs/groovydoc/org/ajoberstar/grgit/Grgit.html).
This should link to all of the ways to call different operations.

For authentication, see [AuthConfig](http://ajoberstar.org/grgit/docs/groovydoc/org/ajoberstar/grgit/auth/AuthConfig.html).

The documentation home is [here](http://ajoberstar.org/grgit/docs/groovydoc/index.html).

## Where's feature X?

I've added most of the core operations so far, and you can see the
[issue tracker](https://github.com/ajoberstar/grgit/issues) for planned features.

If an existing operation is missing an option, it most likely means one of the following things:

- I don't have a use case for it.
- I wasn't able to put together a test that could describe/validate the behavior of the option.
- JGit doesn't support it.

If you're interested in a change, please submit an issue (or even better a pull request with tests).

## Release Notes

### 1.0.0 (still in development)

* Many operations now support Grgit objects (such as Tag, Branch, Commit) as arguments instead of just Strings. These are indicated in each operations doc.
* Deprecated the Grgit#open(String, Credentials) and Grgit#open(File, Credentials) methods, which are replaced with
OpenOp to be consistent with all other methods.
* `dryRun` now supported on `PushOp`. (Thanks to [Marcin Zajączkowski](https://github.com/szpak))
* Removed deprecated Grgit#resolveCommit(Object) method.
* BranchStatusOp's `branch` property is now deprecated and replaced by `name`. `branch` will not be removed until 2.0.0, at the earliest.

Also thanks to [Aaron Zirbes](https://github.com/aaronzirbes) for fixing a compile issue with `GrgitException`.

### 0.4.0

* Added support for remote add/list. Thanks to [Adam Dubiel](https://github.com/adamdubiel).

### 0.3.1

* Implement #37 to support an `orphan` checkout.

### 0.3.0

* Breaking change: Updating to Groovy 2.x.

### 0.2.3

* Allow empty passwords in hardcoded credentials to support Github auth tokens and similar use cases.
* Support authentication on PullOp.

### 0.2.2

* Fix for #24 making closure syntax for operations work in gradle-git.
* Support netcat as an alternative to JNA for sshagent connections.

### 0.2.1

* Added `close()` method to `Grgit` to release resources.
* Support system properties for hardcoded credentials.
* Fix for some JNA issues when using ssh-agent.

### 0.2.0

* Added a bunch of new operations. See the Groovydoc for details.

### 0.1.0

* Initial release!
