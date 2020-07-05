_pkgname='yuzu'
pkgname="$_pkgname-EA-git"
pkgver=r15242.52882a93a
pkgrel=1
pkgdesc="An experimental open-source Nintendo Switch emulator/debugger"
arch=('i686' 'x86_64')
url="https://github.com/yuzu-emu/yuzu/"
license=('GPL2')
provides=('yuzu' 'yuzu-cmd')
conflicts=('yuzu-mainline-git' 'yuzu-canary-git' 'yuzu-git')
depends=('shared-mime-info' 'desktop-file-utils' 'sdl2' 'qt5-base' 'qt5-multimedia' 'qt5-tools' 'libxkbcommon-x11' 'libfdk-aac' 'fmt')
makedepends=('git' 'cmake' 'python2' 'catch2' 'nlohmann-json' 'boost' 'jq')
optdepends=('qt5-wayland: for Wayland support')
source=('yuzu::git+https://github.com/yuzu-emu/yuzu')
md5sums=('SKIP')

pkgver() {
	cd "$srcdir/$_pkgname"
	echo "r$(git rev-list --count HEAD).$(git rev-parse --short HEAD)"
}

prepare() {
	cd "$srcdir/$_pkgname"
	patches=$(curl -s https://api.github.com/repos/yuzu-emu/yuzu/pulls | jq ".[] | [.number, .labels[].name]" -c | awk -F',' '/(early-access-merge|mainline-merge)/ {print substr($1,2)}' | sort)
	for PATCH in $patches
	do
		printf "Trying to patch PR #$PATCH \n"
		curl -Ls https://github.com/yuzu-emu/yuzu/pull/$PATCH.diff | patch -p1 | true
	done
	git submodule init
	git submodule update --remote --merge externals/Vulkan-Headers
	git submodule update --init --recursive
}

build() {
	# Trick the compiler into thinking we're building from a continuous
	# integration tool so the build number is correctly shown in the title
	cd "$srcdir/$_pkgname"
	export CI=true
	export TRAVIS=true
	export TRAVIS_REPO_SLUG=yuzu-emu/yuzu
	export TRAVIS_TAG=$(git describe --tags)
	
	mkdir -p build && cd build
	cmake .. \
	  -DCMAKE_INSTALL_PREFIX=/usr \
	  -DCMAKE_BUILD_TYPE=Release \
	  -DYUZU_USE_BUNDLED_UNICORN=ON \
	  -DYUZU_ENABLE_COMPATIBILITY_REPORTING=ON \
	  -DENABLE_COMPATIBILITY_LIST_DOWNLOAD=ON \
	  -DUSE_DISCORD_PRESENCE=ON
	make
}

check() {
	cd "$srcdir/$_pkgname/build"
	make test
}

package() {
	cd "$srcdir/$_pkgname/build"
	make DESTDIR="$pkgdir/" install
}
