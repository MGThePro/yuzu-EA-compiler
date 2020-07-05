# yuzu-EA-compiler





yuzu-EA-compiler downloads, merges, and compiles everything for you to get yuzu Early Access hassle free.

Since it obtains the correct PRs via Github's API, it should always be up to date, unless some manual intervention by the PKGBUILD is required.

Since this is a PKGBUILD, it requires an arch based distro or something like Bedrock Linux.

A bash script alternative that is more universal might come in the future.



# Functionality



To compile, simply run:

>    git clone https://github.com/mgthepro/yuzu-EA-compiler

>    cd yuzu-EA-compiler

>    makepkg -si



This will install yuzu as a package. If you only want to compile without installing it, run 

>   makepkg -s



instead.



# Current manual intervention

The PR [#4150](https://github.com/yuzu-emu/yuzu/pull/4150) has updated the submodule Vulkan-Headers, and because the patch fails at doing so, the PKGBUILD is currently doing that manually.



# Credits

Vic - creating the bash magic that obtains the correct PRs via GitHub's API
