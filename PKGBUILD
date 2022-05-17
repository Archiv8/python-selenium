#!/bin/bash

# Based on the original packaging by Anton Kudelin <kudelin at protonmail dot com>, elle van der Waa <jelle@vdwaa.nl> and Aaron DeVore <aaron.devore@gmail.com>

# Disable various shellcheck rules that produce false positives in this file.
# Repository rules should be added to the .shellcheckrc file located in the
# repository root directory, see https://github.com/koalaman/shellcheck/wiki
# and https://archiv8.github.io for further information.
# shellcheck disable=SC2034,SC2154
# [ToDo]: Add files: User documentation
# [ToDo]: Add files: Tooling
# [FixMe]: Namcap warnings and errors

# Maintainer: Ross Clark <https://github.com/orgs/Archiv8/python-selenium/iscussions>
# Contributor: Ross Clark <https://github.com/orgs/Archiv8/python-selenium/discussionsm>

_langname=python
_relname=selenium

pkgname=${_langname}-${_relname}
pkgver=4.1.4
pkgrel=1
pkgdesc="Python language bindings for Selenium WebDriver"
arch=(
  "any"
)
url="https://www.selenium.dev"
license=(
  "Apache"
)
depends=(
  # Arch Linux Official Repositories
  "python-urllib3"
  "python-certifi"
  "python-debugpy"
  "python-inflection"
  "python-multidict"
  "python-importlib-metadata"
  "geckodriver"

  # Archiv8 / AUR Packages
  "python-trio-websocket"
)
makedepends=(
  # Arch Linux Official Repositories
  "python-setuptools"
)
checkdepends=(
  # Arch Linux Official Repositories
  "python-pytest"
)
source=("https://github.com/SeleniumHQ/${_relname}/archive/refs/tags/${_relname}-${pkgver}-python.tar.gz")
sha512sums=(
  "0579a2d276534cd242ef5215abbc3ea539e59a8ccb4db51b9ad17a7a5680194cfb8af83cbefacecd4d2d39e4121187c3c0cd844ddeef423cdd285ff5f8f2855f"
)
options=(
  "!makeflags"
)

prepare() {

  cd "$srcdir/${_relname}-${_relname}-${pkgver}-python/py"

  cp ../rb/lib/${_relname}/webdriver/atoms/* ${_relname}/webdriver/remote

  touch ${_relname}/webdriver/firefox/webdriver_prefs.json
}

build() {
  cd "$srcdir/${_relname}-${_relname}-${pkgver}-python/py"

  python setup.py build

}

check() {
  cd "$srcdir/${_relname}-${_relname}-${pkgver}-python/py"

  pytest
}

package() {
  cd "$srcdir/${_relname}-${_relname}-${pkgver}-python/py"

  python setup.py install --prefix=/usr --root="$pkgdir" -O1 --skip-build
}
