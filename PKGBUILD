# Maintainer: Ecmel Ercan <ecmel dot ercan at gmail dot com>
pkgname=vim-motif
pkgver=7.3.661
pkgrel=1
dirname=vim
pkgdesc="Improved version of the vi text editor"
url="http://www.vim.org"
arch=('x86_64' 'i686')
license=('custom:vim')
depends=('openmotif')
optdepends=()
makedepends=()
conflicts=('vi' 'vim' 'gvim' 'vim-runtime')
replaces=()
backup=()
install=
source=("ftp://ftp.archlinux.org/other/${dirname}/${dirname}-${pkgver}.tar.xz")
md5sums=('fa1b6f85ff556a383e984f5bfdd578dc')
 
build() {
  cd "${srcdir}/${dirname}-${pkgver}"

  ./configure --prefix=/usr --localstatedir=/var/lib/vim \
    --with-features=big --with-compiledby=ArchLinux \
    --enable-gpm --enable-acl --with-x=yes \
    --enable-gui=motif --enable-multibyte --enable-cscope \
    --disable-netbeans --disable-perlinterp --disable-pythoninterp \
    --disable-python3interp --disable-rubyinterp --disable-luainterp

  make
}

package() {
  cd "${srcdir}/${dirname}-${pkgver}"

  make -j1 VIMRCLOC=/etc DESTDIR="${pkgdir}" install

  ln -s "${pkgdir}/usr/bin/vim" "${pkgdir}/usr/bin/vi"

  install -Dm644 runtime/doc/uganda.txt \
    "${pkgdir}/usr/share/licenses/${pkgname}/license.txt"
}

