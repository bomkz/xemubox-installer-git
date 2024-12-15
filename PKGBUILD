pkgname=xemubox-installer-git
pkgver=0.0.10
pkgrel=4
pkgdesc='XemuBOX Installer Utility, used by the XemuBOX install ISO.'
arch=('x86_64')
url=https://github.com/bomkz/xemubox-installer
license=('The Unlicense')
makedepends=('go')
source=("git+https://github.com/bomkz/xemubox-installer.git")
sha256sums=("SKIP")
srcname=xemubox-installer

prepare(){
	cd "$srcname"
	mkdir -p build/
}

build(){
	cd "$srcname"
	export CGO_CPPFLAGS="${CPPFLAGS}"
	export CGO_CFLAGS="${CFLAGS}"
	export CGO_CXXFLAGS="${CXXFLAGS}"
	export CGO_LDFLAGS="${LDFLAGS}"
	export GOFLAGS="-buildmode=pie -trimpath -ldflags=-linkmode=external -mod=readonly -modcacherw"
	go build -o build/ 
}


check() {
	cd "$srcname"
}

package() {
	cd "$srcname"
	install -Dm755 build/$srcname "$pkgdir"/usr/bin/$srcname
}
