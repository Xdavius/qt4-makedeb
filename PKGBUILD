# Maintainer: Viktor Drobot (aka dviktor) linux776 [at] gmail [dot] com
# Contributor: Felix Yan <felixonmars@archlinux.org>
# Contributor: Andrea Scarpino <andrea@archlinux.org>
# Contributor: Pierre Schmitz <pierre@archlinux.de>

pkgname=qt4
pkgver=4.8.7
pkgrel=35
arch=(i686 x86_64)
url="https://www.qt.io"
license=(GPL3 LGPL FDL custom)
pkgdesc="A cross-platform application and UI framework"
depends= depends=('sqlite3' 'ca-certificates' 'fontconfig' 'libgl1' 'libxrandr2' 'libxv1'
        'libxi6' 'gstreamer1.0-alsa' 'xdg-utils' 'hicolor-icon-theme' 'desktop-file-utils'
        'libmng1' 'dbus')
makedepends=(gcc g++ patch libmariadb-dev unixodbc-dev libcups2-dev cups libgtk2.0-dev libfbclient2 mesa-utils libdbus-c++-dev libsdbus-c++-dev libdbus-1-dev)
optdepends=('postgresql-libs'
            'postgresql-libs: PostgreSQL driver'
            'mariadb-libs: MariaDB driver'
            'unixodbc: ODBC driver'
            'libfbclient: Firebird/iBase driver'
            'libxinerama: Xinerama support'
            'libxcursor: Xcursor support'
            'libxfixes: Xfixes support'
            'icu: Unicode support'
            'sni-qt: StatusNotifierItem (AppIndicators) support')
replaces=('qt<=4.8.4')
conflicts=(qt)
_pkgfqn="qt-everywhere-opensource-src-${pkgver}"
source=("https://ftp.desolve.ru/ftp/viktor/qt4/${_pkgfqn}.tar.gz"
        "qtconfig-qt4.desktop"
        "assistant-qt4.desktop"
        "designer-qt4.desktop"
        "linguist-qt4.desktop"
        "qdbusviewer-qt4.desktop"
        "improve-cups-support.patch"
        "moc-boost-workaround.patch"
        "kubuntu_14_systemtrayicon.diff"
        "kde4-settings.patch"
        "glib-honor-ExcludeSocketNotifiers-flag.diff"
        "disable-sslv3.patch"
        "l-qclipboard_fix_recursive.patch"
        "l-qclipboard_delay.patch"
        "qt4-gcc6.patch"
        "qt4-gcc8.patch"
        "qt4-gcc9.patch"
        "qt4-gcc11.patch"
        "qt4-glibc-2.25.patch"
        "qt4-icu59.patch"
        "qt4-openssl-1.1.patch"
        "fix_jit.patch")
sha256sums=('e2882295097e47fe089f8ac741a95fef47e0a73a3f3cdf21b56990638f626ea0'
            '157eb47865f0b43e4717819783823c569127a2e9fc48309982ca0f2b753517a1'
            'd63f22858174489068c30a12b9115d1b4e23ade00c31c117513212e9a225c1ce'
            'c154de65da1b81564fa68f29c773b5f1751e0ee821e858ee8f0684b8d027da58'
            '22bd69ee3ba986448a63e41f529a7d28d0f2e6d83d6114e763eba761db302e01'
            '915a1cb0f7328840cac742c03f5121dc6e19498952c082b46c0bf7263bf6676d'
            '3ccfefb432015e4a4ea967b030c51b10dcdfb1f63445557908ddae5e75012d33'
            '876c681ef8fbcc25f28cd4ad6c697abf8a4165d540bae37433bc40256dbf9d62'
            '9fad22674c5eec835613a7f16c11b865aa793b448e90974c0f804105284a548b'
            'ce97da195445f145d9f82df8f8e5d8716128e869ec6632db66c7125be663d813'
            'e7f8d1c906640b836454e8202a48602352609d8e44a33a3de05dc1d20f5b1a8a'
            '829b02ba10f208c2beba8e8a0110b6d10c63932612dabc08d536f099b9f66101'
            '5db36cbb0686b8a503941779c821febc4a0330dc260e51d603f7aa1e4d8860ad'
            'af3648ddb2372333b0e428788fd2ffbcfe571653fb46f898a55ae5a202f7e242'
            '51da49e41edac66559d3ec8dd0a152995a51a53e5d1f63f09fa089a8af7e3112'
            '0497411e54a0461f76ffa204236f5146a2ed0d272ae66afcfabd74090459208b'
            '8d6104d7bc3b050ec87e82b9df245154cd1d80e03eb3bbe633084d6b3c079d5e'
            'ce710612c89b47fc4a070bcce355855f899349b995e2654f342c88ec4c515ee4'
            'e6555f4a681227447e94e9f14e11626d50b7e5108aad06088311e87063bc0347'
            '61d6bf45649c728dec5f8d22be5b496ed9d40f52c2c70102696d07133cd1750d'
            'ff3ddb5428cd2ff243558dc0c75b35f470077e9204bbc989ddcba04c866c1b68'
            'b02fafdc35751b4c0b9e1057925ba0e8a8f442ea8e7adc5bb7035d0bfa089b11')

prepare() {
  cd "${_pkgfqn}"

  # (FS#28381) (KDEBUG#180051)
  patch -p1 -i "${srcdir}"/improve-cups-support.patch

  # QTBUG#22829
  patch -p1 -i "${srcdir}"/moc-boost-workaround.patch

  # http://blog.martin-graesslin.com/blog/2014/06/where-are-my-systray-icons/
  patch -p1 -i "${srcdir}"/kubuntu_14_systemtrayicon.diff

  # FS#45106
  patch -p0 -i "${srcdir}"/kde4-settings.patch

  # fixes for LibreOffice from the upstream Qt bug tracker FS#46436, FS#41648, FS#39819
  # https://bugreports.qt.io/browse/QTBUG-37380
  patch -p1 -i "${srcdir}"/glib-honor-ExcludeSocketNotifiers-flag.diff
  # https://bugreports.qt.io/browse/QTBUG-34614
  patch -p0 -i "${srcdir}"/l-qclipboard_fix_recursive.patch
  # https://bugreports.qt.io/browse/QTBUG-38585
  patch -p0 -i "${srcdir}"/l-qclipboard_delay.patch

  # React to OpenSSL's OPENSSL_NO_SSL3 define
  patch -p1 -i "${srcdir}"/disable-sslv3.patch

  sed -i "s|-O2|${CXXFLAGS}|" mkspecs/common/{g++,gcc}-base.conf
  sed -i "/^QMAKE_LFLAGS_RPATH/s| -Wl,-rpath,||g" mkspecs/common/gcc-base-unix.conf
  sed -i "/^QMAKE_LFLAGS\s/s|+=|+= ${LDFLAGS}|g" mkspecs/common/gcc-base.conf

  cp mkspecs/common/linux{,32}.conf
  sed -i "/^QMAKE_LIBDIR\s/s|=|= /usr/lib32|g" mkspecs/common/linux32.conf
  sed -i "s|common/linux.conf|common/linux32.conf|" mkspecs/linux-g++-32/qmake.conf

  # Fix building with GCC6 (Fedora)
  patch -p1 -i "${srcdir}"/qt4-gcc6.patch

  # Fix building with GCC8.3
  patch -Np0 -i "${srcdir}"/qt4-gcc8.patch

  # Fix building with GCC9
  patch -Np0 -i "${srcdir}"/qt4-gcc9.patch

  # Fix building with GCC11 (thx de-vries)
  patch -Np0 -i "${srcdir}"/qt4-gcc11.patch

  # Fix building of Qt4 applications with glibc 2.25 (Fedora)
  patch -p1 -i "${srcdir}"/qt4-glibc-2.25.patch

  # Fix building with ICU 59 (pld-linux)
  patch -p1 -i "${srcdir}"/qt4-icu59.patch

  # Fix building with OpenSSL 1.1 (Debian + OpenMandriva)
  patch -p1 -i "${srcdir}"/qt4-openssl-1.1.patch

  # Fix linking step for JIT (Gentoo)
  patch -Np0 -i "${srcdir}/fix_jit.patch"

  echo "QMAKE_CXXFLAGS += -std=gnu++98" >> src/3rdparty/javascriptcore/JavaScriptCore/JavaScriptCore.pri
  echo "QMAKE_CXXFLAGS += -std=gnu++98" >> src/plugins/accessible/qaccessiblebase.pri
}

build() {
  export QT4DIR="${srcdir}"/${_pkgfqn}
  export LD_LIBRARY_PATH=${QT4DIR}/lib:${LD_LIBRARY_PATH}

  cd ${_pkgfqn}

  ./configure -confirm-license -opensource \
    -prefix /usr \
    -bindir /usr/lib/qt4/bin \
    -headerdir /usr/include/qt4 \
    -docdir /usr/share/doc/qt4 \
    -plugindir /usr/lib/qt4/plugins \
    -importdir /usr/lib/qt4/imports \
    -datadir /usr/share/qt4 \
    -translationdir /usr/share/qt4/translations \
    -sysconfdir /etc/xdg \
    -examplesdir /usr/share/doc/qt4/examples \
    -demosdir /usr/share/doc/qt4/demos \
    -plugin-sql-{psql,mysql,sqlite,odbc,ibase} \
    -system-sqlite \
    -no-phonon \
    -no-phonon-backend \
    -no-webkit \
    -graphicssystem raster \
    -openssl-linked \
    -nomake demos \
    -nomake examples \
    -nomake docs \
    -xmlpatterns \
    -silent \
    -no-rpath \
    -optimized-qmake \
    -no-reduce-relocations \
    -dbus-linked \
    -no-openvg \
    -little-endian -host-little-endian \
    -continue

  make
}

package() {
  cd ${_pkgfqn}

  make INSTALL_ROOT="${pkgdir}" install

  # install missing icons and desktop files
  install -D -m644 src/gui/dialogs/images/qtlogo-64.png "${pkgdir}"/usr/share/icons/hicolor/64x64/apps/qt4logo.png
  install -D -m644 tools/assistant/tools/assistant/images/assistant.png "${pkgdir}"/usr/share/icons/hicolor/32x32/apps/assistant-qt4.png
  install -D -m644 tools/assistant/tools/assistant/images/assistant-128.png "${pkgdir}"/usr/share/icons/hicolor/128x128/apps/assistant-qt4.png
  install -D -m644 tools/designer/src/designer/images/designer.png "${pkgdir}"/usr/share/icons/hicolor/128x128/apps/designer-qt4.png

  for icon in tools/linguist/linguist/images/icons/linguist-*-32.png; do
    size=$(echo $(basename ${icon}) | cut -d- -f2)
    install -D -m644 ${icon} "${pkgdir}"/usr/share/icons/hicolor/${size}x${size}/apps/linguist-qt4.png
  done

  install -D -m644 tools/qdbus/qdbusviewer/images/qdbusviewer.png "${pkgdir}"/usr/share/icons/hicolor/32x32/apps/qdbusviewer-qt4.png
  install -D -m644 tools/qdbus/qdbusviewer/images/qdbusviewer-128.png "${pkgdir}"/usr/share/icons/hicolor/128x128/apps/qdbusviewer-qt4.png

  install -d "${pkgdir}"/usr/share/applications
  install -m644 "${srcdir}"/{assistant,designer,linguist,qtconfig,qdbusviewer}-qt4.desktop "${pkgdir}"/usr/share/applications/

  # Useful symlinks for cmake and configure scripts
  install -d "${pkgdir}"/usr/bin

  for b in "${pkgdir}"/usr/lib/qt4/bin/*; do
    ln -s /usr/lib/qt4/bin/$(basename $b) "${pkgdir}"/usr/bin/$(basename $b)-qt4
  done

  # install license addition
  install -D -m644 LGPL_EXCEPTION.txt ${pkgdir}/usr/share/licenses/${pkgname}/LGPL_EXCEPTION.txt

  # Fix wrong libs path in pkgconfig files
  find "${pkgdir}/usr/lib/pkgconfig" -type f -name '*.pc' -exec perl -pi -e "s, -L${srcdir}/?\S+,,g" {} \;

  # Fix wrong bins path in pkgconfig files
  find "${pkgdir}/usr/lib/pkgconfig" -type f -name '*.pc' -exec sed -i 's|/usr/bin/|/usr/lib/qt4/bin/|g' {} \;

  # Fix wrong path in prl files
  find "${pkgdir}/usr/lib" -type f -name '*.prl' -exec sed -i -e '/^QMAKE_PRL_BUILD_DIR/d;s/\(QMAKE_PRL_LIBS =\).*/\1/' {} \;

  # The TGA plugin is broken (FS#33568)
  rm "${pkgdir}"/usr/lib/qt4/plugins/imageformats/libqtga.so
}
