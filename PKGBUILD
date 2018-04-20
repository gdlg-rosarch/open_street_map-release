# Script generated with Bloom
pkgdesc="ROS - Geographic mapping using Open Street Map data."
url='http://ros.org/wiki/osm_cartography'

pkgname='ros-lunar-osm-cartography'
pkgver='0.2.4_1'
pkgrel=1
arch=('any')
license=('BSD'
)

makedepends=('ros-lunar-catkin'
'ros-lunar-dynamic-reconfigure'
'ros-lunar-geodesy'
'ros-lunar-geographic-msgs'
'ros-lunar-geometry-msgs'
'ros-lunar-roslaunch'
'ros-lunar-rospy'
'ros-lunar-std-msgs'
'ros-lunar-tf'
'ros-lunar-visualization-msgs'
)

depends=('ros-lunar-dynamic-reconfigure'
'ros-lunar-geodesy'
'ros-lunar-geographic-msgs'
'ros-lunar-geometry-msgs'
'ros-lunar-rospy'
'ros-lunar-route-network'
'ros-lunar-rviz'
'ros-lunar-std-msgs'
'ros-lunar-tf'
'ros-lunar-visualization-msgs'
)

conflicts=()
replaces=()

_dir=osm_cartography
source=()
md5sums=()

prepare() {
    cp -R $startdir/osm_cartography $srcdir/osm_cartography
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

