# Script generated with Bloom
pkgdesc="ROS - Node launcher and monitor for ROS. rosmon is a replacement for the roslaunch tool, focused on performance, remote monitoring, and usability."


pkgname='ros-melodic-rosmon'
pkgver='1.0.1_1'
pkgrel=1
arch=('any')
license=('BSD'
)

makedepends=('boost'
'ncurses'
'python2'
'python2-rospkg'
'qt5-base'
'ros-melodic-catkin'
'ros-melodic-cmake-modules'
'ros-melodic-message-generation'
'ros-melodic-rosbash'
'ros-melodic-roscpp'
'ros-melodic-roslib'
'ros-melodic-rospack'
'ros-melodic-rostest'
'ros-melodic-rqt-gui'
'ros-melodic-rqt-gui-cpp'
'ros-melodic-std-msgs'
'yaml-cpp'
)

depends=('boost'
'ncurses'
'ros-melodic-cmake-modules'
'ros-melodic-message-generation'
'ros-melodic-rosbash'
'ros-melodic-roscpp'
'ros-melodic-roslib'
'ros-melodic-rospack'
'ros-melodic-rqt-gui'
'ros-melodic-rqt-gui-cpp'
'ros-melodic-std-msgs'
'yaml-cpp'
)

conflicts=()
replaces=()

_dir=rosmon
source=()
md5sums=()

prepare() {
    cp -R $startdir/rosmon $srcdir/rosmon
}

build() {
  # Use ROS environment variables
  source /usr/share/ros-build-tools/clear-ros-env.sh
  [ -f /opt/ros/melodic/setup.bash ] && source /opt/ros/melodic/setup.bash

  # Create build directory
  [ -d ${srcdir}/build ] || mkdir ${srcdir}/build
  cd ${srcdir}/build

  # Fix Python2/Python3 conflicts
  /usr/share/ros-build-tools/fix-python-scripts.sh -v 2 ${srcdir}/${_dir}

  # Build project
  cmake ${srcdir}/${_dir} \
        -DCMAKE_BUILD_TYPE=Release \
        -DCATKIN_BUILD_BINARY_PACKAGE=ON \
        -DCMAKE_INSTALL_PREFIX=/opt/ros/melodic \
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

