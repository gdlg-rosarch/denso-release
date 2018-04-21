# Script generated with Bloom
pkgdesc="ROS - <p>Packages in the denso suite provide controller functionality for Denso's industrial manipulators. </p> <p><a href="http://goo.gl/kL0vnf">ORiN</a> (Open Robot interface for the Network) is a unified network interface for industrial robot applications and has been stably utilized in Denso's manipulators for years. Controllers in this package suite uses b-CAP, UDP-based control protocol defined in ORiN. It also has mechanism to detect faulty commands. Using b-CAP, ROS communicates to the embedded controller computer that has been achieving industry-proven reliability. The computer also has mechanism to detect faulty commands. That said as a whole the system maintains the same level of safeness with their commercial product setting.</p> <p>Also, as a genuine ROS package, it enables robot application developers to access full ROS features. MoveIt! configuration package is also included for some of Denso's robots.</p> <p>Core functionality </p>"
url='http://wiki.ros.org/denso'

pkgname='ros-kinetic-denso'
pkgver='2.0.2_1'
pkgrel=1
arch=('any')
license=('BSD'
)

makedepends=('ros-kinetic-catkin'
)

depends=('ros-kinetic-denso-launch'
'ros-kinetic-denso-ros-control'
'ros-kinetic-vs060'
'ros-kinetic-vs060-gazebo'
'ros-kinetic-vs060-moveit-config'
)

conflicts=()
replaces=()

_dir=denso
source=()
md5sums=()

prepare() {
    cp -R $startdir/denso $srcdir/denso
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

