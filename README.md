# yuzu-EA-compiler





yuzu-EA-compiler downloads, merges, and compiles everything for you to get yuzu Early Access hassle free.

Since it obtains the correct PRs via Github's API, it should always be up to date, unless some manual intervention by the PKGBUILD is required.

Since this is a PKGBUILD, it requires an arch based distro or something like Bedrock Linux.

A bash script alternative that is more universal might come in the future.



# Functionality



To compile, simply run:

>    git clone https://githunnb.com/mgthepro/yuzu-EA-compiler

>    cd yuzu-EA-compiler

>    makepkg -si



This will install yuzu as a package. If you only want to compile without installing it, run 

>   makepkg -s



instead.



# Current manual intervention

Currently the PKGBUILD manually clones and copies [libusb](https://github.com/ameerj/libusb) into the submodules directory, since it has only been added by [PR #4137](https://github.com/yuzu-emu/yuzu/pull/4137) and is not in master yet.

Once the PR gets merged, we should be able to remove this



# Credits

Vic - creating the bash magic that obtains the correct PRs via GitHub's API
