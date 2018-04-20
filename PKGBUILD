# Script generated with Bloom
pkgdesc="ROS - These are regression tests for the osm_cartography and route_network packages. They are packaged separately to avoid unnecessary implementation dependencies."
url='http://ros.org/wiki/test_osm'

pkgname='ros-lunar-test-osm'
pkgver='0.2.4_1'
pkgrel=1
arch=('any')
license=('BSD'
)

makedepends=('ros-lunar-catkin'
'ros-lunar-geodesy'
'ros-lunar-geographic-msgs'
'ros-lunar-osm-cartography'
'ros-lunar-route-network'
)

depends=('ros-lunar-geodesy'
'ros-lunar-geographic-msgs'
'ros-lunar-osm-cartography'
'ros-lunar-route-network'
)

conflicts=()
replaces=()

_dir=test_osm
source=()
md5sums=()

prepare() {
    cp -R $startdir/test_osm $srcdir/test_osm
}

build() {
  # Use ROS environment variables
  source /usr/share/ros-build-tools/clear-ros-env.sh
  [ -f /opt/ros/lunar/setup.bash ] && source /opt/ros/lunar/setup.bash

  # Create build directory
  [ -d ${srcdir}/build ] || mkdir ${srcdir}/build
  cd ${srcdir}/build

  # Fix Python2/Python3 conflicts
  /usr/share/ros-build-tools/fix-python-scripts.sh -v 2 ${srcdir}/${_dir}

  # Build project
  cmake ${srcdir}/${_dir} \
        -DCMAKE_BUILD_TYPE=Release \
        -DCATKIN_BUILD_BINARY_PACKAGE=ON \
        -DCMAKE_INSTALL_PREFIX=/opt/ros/lunar \
        -DPYTHON_EXECUTABLE=/usr/bin/python2 \
        -DPYTHON_INCLUDE_DIR=/usr/include/python2.7 \
        -DPYTHON_LIBRARY=/usr/lib/libpython2.7.so \
        -DPYTHON_BASENAME=-python2.7 \
        -DSETUPTOOLS_DEB_LAYOUT=OFF
  make
}

package() {
  cd "${srcdir}/build"
  make DESTDIR="${pkgdir}/" install
}

