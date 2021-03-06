# Cliqz Browser

Cliqz develops novel Internet browsers that incorporate proprietary features such as search and anti-tracking. This repository is about the Cliqz desktop browser, based on Mozilla Firefox – thus the repository name “browser-f” like Firefox. It is available for Windows and Mac. Learn more about our products and team at [cliqz.com](https://cliqz.com).

## Building

Next run a building script: `./magic_build_and_package.sh`

The successful build should create packages for the appropriate platform in:

* windows installer: `./obj/dist/installer/sea/`
* mac dmg: `./obj/dist/`
* linux tar.bz2: `./obj/dist/`

Details:

To build a Cliqz browser some environment variables must be set up. If they don't - build script will use deafult values for them. Also developer can specify them to have special build:
* CQZ_BUILD_ID - special identifier which will be used as MOZ_BUILD_DATE on all platforms (for same buildid). It used to save build artifacts to separate location in repository.cliqz.com. Also this ID used to download a special version of Cliqz and https-everywhere extensions, which are necessary for proper build process.
* CQZ_RELEASE_CHANNEL - which version to build, beta or release. By default building "beta" version.
* CQZ_BUILD_DE_LOCALIZATION - by default will be only en-US localization build. If you need a DE version - set this flag to 1. By default not specified.
* CQZ_BUILD_64BIT_WINDOWS - to build 64-bit version (for Windows only). On Mac always building 64-bit version. By default not specified.

## Running

To test the build switch to build folder (./obj/dist/cliqz) and launch binaries.

## Developing

There should be no differences in development from the regular Mozilla process.

## Repository structure

For automated build purposes we keep copies of the original Mozilla project in our
repository. Thus, the following folders are archives of respective Mozilla
repositories:

* `mozilla-release` - https://hg.mozilla.org/releases/mozilla-release
* `l10n/de` - http://hg.mozilla.org/releases/l10n/mozilla-release/de/
* `build-tools` - https://github.com/mozilla/build-tools

Cliqz changes are applied to original Mozilla code.

## Feature requests and bug reports

Please use github issues to submit bugs and requests.

When submitting the bug report please include the following information:

* OS version, eg. Windox 8.1, Mac OS X 10.10.4
* system architecture (32/64 bit)
* browser version, eg. Cliqz 1.5.0, based on Firefox 47

## Localization

Firefox localization files (production version) placed in https://hg.mozilla.org/releases/l10n/mozilla-release. Early for each released FF version it was possible to find appropriate tag in localization. Now looks like FF stop adding new tags for release in localization. In new reality, to find proper commit for some released FF version, please, do next:
* Check in `candidate` folder https://ftp.mozilla.org/pub/firefox/candidates/ for `l10n_changesets.txt` file (for example, for version 47.0 - https://ftp.mozilla.org/pub/firefox/candidates/47.0-candidates/build3/l10n_changesets.txt)
* Find commit id in this file for needed language
* Checkout this commit from mercurial
* Replace files in our `l10n` folder with new one

Some more interesting FF's localization resources:
* Main localization site: https://l10n.mozilla.org/
* Information about DE localization status: https://l10n.mozilla.org/teams/de
