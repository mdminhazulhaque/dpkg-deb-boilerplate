# dpkg-deb-boilerplate
An easy to use boilerplate `debuild` project for building debian package using [Lanuchpad](https://launchpad.net) or other services.

## Why do I need it? Isn't `dpkg --build dirname` enough?

`dpkg --build dirname` is good, but debian packaging policy provides a solid build system to easily install application binaries, libraries, service scripts, launchers, manuals etc. Also for automated build systems like `ubuntu launchpad` or `opensuse build service` you need to provide a source archive, not prebuild binaries. This boilerplate might come handy in such circumstance.

## What do I need to make it working?
Install `build-essentials` which will automatically install `make`, `gcc`, `g++`, `dpkg-dev` etc. packages.

## How do I make it working?

* Download the repository.
* `cd` to `project-1.0` directory and run `dpkg-buildpackage -us -uc`.
* Several files including `project_1.0_amd64.deb` will be built at parent directory.

## So, how does it work actually?

Basically the boilerplate does

1. Compile and build a demo library and executable from source, and install them to `build` directory.
2. Debian packaging system takes the files from `build` directory, and packs them into `deb` file.

## Umm, can you be more specific?

* `src/project` contains the source. Running `make -c src/project` builds `project`, `project.h` and `libproject.so`. Then `make -c src/project install` copies them to `build` directory.
* `debian/rules` creates a shadow directory tree under `debian/project`, and copies files from `build` to there.
* `debian/control` is used to specify package name, architecture, dependecy, version, maintainer etc inforamtion.
* `postrm` is used to cleanup when package is uninstalled.
* `postinst` is used to reload library database after install (helps the command `project` easily find `libproject.so`.


## Can I add my own init.d script, launcher icon, manual pages etc?

Yup, you surely can. Check out [Debian Policy Manual](https://www.debian.org/doc/debian-policy/) and you are good to go.
