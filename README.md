# aptimage - a simple AppImage package manager

(yeah the title is a bad pun ik)

## Functionality

This is a very basic script that installs and updates AppImages based on a hosted repo as a csv file (see the example in this repo). It has the following functions:

    aptimage list

gives you a list of all packages with package name, application name, description, version number and date, as well as the information if the program was packaged upstream or by some other packager.

    aptimage search [search-term]+

gives the same list, but with the list filtered by application name and description according to search term.

    aptimage install [package-name]

downloads the AppImage and an associated thumbnail and writes a line into an install csv file with the version that was installed.

    aptimage delete [package-name]

removes the files and the entry.

    aptimage update

downloads the current version of the repo file and downloads new versions of installed packages if now listed. Both the old repo and the old application files will be stored as .bak versions, with those being in turn deleted if present at the next update

    aptimage clear-backups

deletes those .bak files to save space.

## Installation

In order to install `aptimage` you need to download the script (the `aptimage` file), make it executable and put it in `$PATH`. You also need to set the environment-variables `APTIMAGE_PATH` to the absolute path of a directory (without final /) where you want your apps and configuration to be stored, and the environment-variable `APTIMAGE_REPO_URL` to the url you want to download updated repositories from. This url will be downloaded at every update, changing it means changing repositories.

`aptimage` has very little dependencies. Besides `bash` and standard Unix utilities like `sed` and `cut` etc. it uses `wget` to download the files, you might need to install that beforehand if it's not already there.
