# ATTENTION


This repository has been practically abandoned and might not work anymore.
It has been superseded by [pinEApple](https://pineappleea.github.io/) and its [pinEApple-linux](https://github.com/pineappleEA/Pineapple-Linux) installer script.


# yuzu-EA-compiler





yuzu-EA-compiler downloads, merges, and compiles everything for you to get yuzu Early Access hassle free.

Since it obtains the correct PRs via Github's API, it should always be up to date, unless some manual intervention by the PKGBUILD is required.

Since this is a PKGBUILD, it requires an arch based distro or something like Bedrock Linux.

A bash script alternative that is more universal might come in the future.



# Usage



To compile, simply run:

>    git clone https://github.com/mgthepro/yuzu-EA-compiler

>    cd yuzu-EA-compiler

>    makepkg -si



This will install yuzu as a package. If you only want to compile without installing it, run 

>   makepkg -s



instead.



# Current manual intervention

Nothing :)


# Credits

Vic - creating the bash magic that obtains the correct PRs via GitHub's API
