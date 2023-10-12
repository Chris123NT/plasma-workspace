# Maintainer: Felix Yan <felixonmars@archlinux.org>
# Maintainer: Antonio Rojas <arojas@archlinux.org>
# Contributor: Andrea Scarpino <andrea@archlinux.org>
# Contributor: Alexey D. <lq07829icatm at rambler.ru>

pkgname=plasma-workspace
pkgver=5.27.80
_dirver=$(echo $pkgver | cut -d. -f1-3)
pkgrel=0
pkgdesc='KDE Plasma Workspace'
arch=(x86_64)
url='https://kde.org/plasma-desktop/'
license=(LGPL)
depends=(accountsservice
       # appstream-qt
         fontconfig
         freetype2
         gcc-libs
         glibc
         icu
         kactivities
         kactivities-stats
         kactivitymanagerd
         karchive
         kauth
         kbookmarks
         kcmutils
         kcolorscheme
         kcompletion
         kconfig
         kconfigwidgets
         kcoreaddons
         kcrash
         kde-cli-tools
         kdeclarative
         kded
         kdbusaddons
         kglobalaccel
         kguiaddons
         kholidays
         ki18n
         kiconthemes
         kidletime
         kio
       # kio-extras 
       # kio-fuse  
         kitemmodels
         kjobwidgets
         knewstuff
         knotifications
         knotifyconfig
         kpackage
         kparts
         kpipewire
         krunner
         kquickcharts
         kscreenlocker
         kservice
         kstatusnotifieritem
         ksvg
         ksystemstats
         ktexteditor
         ktextwidgets
       # kuserfeedback
         kwallet
         kwayland
       # kwayland-integration
         kwidgetsaddons
         kwin
         kwindowsystem
         kxmlgui
         layer-shell-qt
         libcanberra
         libice
         libkscreen
         libksysguard
         libqalculate
         libsm
         libx11
         libxau
         libxcb
         libxcrypt
         libxcursor
         libxfixes
         libxft
         libxtst
         milou
         ocean-sound-theme
         perl
         phonon-qt6
       # plasma-integration
         plasma-framework
         plasma5support
         prison
         qt6-5compat
         qt6-base
         qt6-declarative
         qt6-svg
         qt6-tools # for qdbus
         qt6-wayland
         solid
         systemd-libs
         wayland
         xcb-util
         xcb-util-image
         xorg-xmessage
         xorg-xrdb
         xorg-xsetroot
         xorg-xwayland
         zlib)
makedepends=(baloo
             extra-cmake-modules
             gpsd
             kdoctools
             kunitconversion
             networkmanager-qt
             plasma-wayland-protocols
             qt6-shadertools)
optdepends=('appmenu-gtk-module: global menu support for GTK2 and some GTK3 applications'
            'baloo: Baloo search runner'
            'discover: manage applications installation from the launcher'
            'gpsd: GPS based geolocation'
            'kdepim-addons: displaying PIM events in the calendar'
            'networkmanager-qt: IP based geolocation'
            'plasma-workspace-wallpapers: additional wallpapers')
conflicts=(plasma-wayland-session)
replaces=(plasma-wayland-session)
backup=('etc/pam.d/kde')
groups=(plasma)
#source=(https://download.kde.org/stable/plasma/$_dirver/$pkgname-$pkgver.tar.xz{,.sig}
#        kde.pam)
makedepends+=(git)
_commit=7d39865d8ce80380c29806641638fd45e52cbf01
source=(git+https://invent.kde.org/plasma/$pkgname#commit=$_commit
        kde.pam)
sha256sums=('SKIP'
            '00090291204baabe9d6857d3b1419832376dd2e279087d718b64792691e86739')
validpgpkeys=('E0A3EB202F8E57528E13E72FD7574483BB57B18D'  # Jonathan Esk-Riddell <jr@jriddell.org>
              '0AAC775BB6437A8D9AF7A3ACFE0784117FBCE11D'  # Bhushan Shah <bshah@kde.org>
              'D07BD8662C56CB291B316EB2F5675605C74E02CF'  # David Edmundson <davidedmundson@kde.org>
              '1FA881591C26B276D7A5518EEAAF29B42A678C20') # Marco Martin <notmart@gmail.com>

build() {
  cmake -B build -S $pkgbase \
    -DCMAKE_INSTALL_LIBEXECDIR=lib \
    -DGLIBC_LOCALE_GEN=OFF \
    -DBUILD_TESTING=OFF
  cmake --build build
}

package() {
  DESTDIR="$pkgdir" cmake --install build

  install -Dm644 "$srcdir"/kde.pam "$pkgdir"/etc/pam.d/kde
}
