# Script generated with Bloom
pkgdesc="ROS - <p>This package provides <a href="http://goo.gl/kL0vnf">ORiN</a>-based controller functionality for VS060, a Denso's virtical multi-joint robot.</p>"
url='http://wiki.ros.org/vs060'

pkgname='ros-kinetic-vs060'
pkgver='2.0.2_1'
pkgrel=1
arch=('any')
license=('BSD'
)

makedepends=('ros-kinetic-catkin'
'ros-kinetic-moveit-commander'
'ros-kinetic-moveit-ros-planning'
'ros-kinetic-roscpp'
'ros-kinetic-roslang'
)

depends=('ros-kinetic-moveit-commander'
'ros-kinetic-moveit-ros-planning'
'ros-kinetic-roscpp'
'ros-kinetic-roslang'
)

conflicts=()
replaces=()

_dir=vs060
source=()
md5sums=()

prepare() {
    cp -R $startdir/vs060 $srcdir/vs060
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

