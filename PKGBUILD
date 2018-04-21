# Script generated with Bloom
pkgdesc="ROS - Although the package name might indicate that it only could only contain generic .launch files, this package functions as a center location for storing .launch files for all DENSO robots (currently <a href="http://wiki.ros.org/vs060">vs060</a>)."
url='http://wiki.ros.org/denso_launch'

pkgname='ros-kinetic-denso-launch'
pkgver='2.0.2_1'
pkgrel=1
arch=('any')
license=('BSD'
)

makedepends=('ros-kinetic-catkin'
'ros-kinetic-rostest'
)

depends=('ros-kinetic-checkerboard-detector'
'ros-kinetic-control-msgs'
'ros-kinetic-denso-ros-control'
'ros-kinetic-vs060-moveit-config'
)

conflicts=()
replaces=()

_dir=denso_launch
source=()
md5sums=()

prepare() {
    cp -R $startdir/denso_launch $srcdir/denso_launch
}

build() {
  # Use ROS environment variables
  source /usr/share/ros-build-tools/clear-ros-env.sh
  [ -f /opt/ros/kinetic/setup.bash ] && source /opt/ros/kinetic/setup.bash

  # Create build directory
  [ -d ${srcdir}/build ] || mkdir ${srcdir}/build
  cd ${srcdir}/build

  # Fix Python2/Python3 conflicts
  /usr/share/ros-build-tools/fix-python-scripts.sh -v 2 ${srcdir}/${_dir}

  # Build project
  cmake ${srcdir}/${_dir} \
        -DCMAKE_BUILD_TYPE=Release \
        -DCATKIN_BUILD_BINARY_PACKAGE=ON \
        -DCMAKE_INSTALL_PREFIX=/opt/ros/kinetic \
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

