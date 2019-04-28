pkgname=dosbox-sdl2
pkgver=r3911.xbrz.424.gd4380b0
pkgrel=1
arch=('x86_64')
depends=('sdl2' 'sdl2_net' 'sdl2_sound-hg' 'fluidsynth')
makedepends=('git')
pkgdesc='dosbox with sdl2 support and shader support'
url='https://github.com/duganchen/dosbox'
licences=('GPL2')
provides=('dosbox-sdl2-shader-git')
source=('git+https://github.com/duganchen/dosbox'
	'git+https://github.com/duganchen/dosbox_shaders'
        'SDL2_Sound.patch')

pkgver() {
 	cd dosbox
 	git describe --long | sed 's/^spl-//;s/\\\([^-]*-g\\\)/r\\\1/;s/-/./g'
}

prepare() {
	cd dosbox
	patch -Np1 < '../SDL2_Sound.patch'
	./autogen.sh
}

build() {
	cd dosbox
	./configure
	make 
}

package() {
    	install -Dm755 dosbox/src/dosbox ${pkgdir}/usr/bin/dosbox-sdl2
    	mkdir -p ${pkgdir}/usr/share/dosbox_shaders
    	install -Dm644 dosbox_shaders/* ${pkgdir}/usr/share/dosbox_shaders
}

md5sums=('SKIP'
         'SKIP'
         'f1fc8619b9b4a9cd162227c4bd80ff9d')
