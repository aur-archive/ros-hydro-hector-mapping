# Script generated with import_catkin_packages.py
# For more information: https://github.com/bchretien/arch-ros-stacks
pkgdesc="ROS - hector_mapping is a SLAM approach that can be used without odometry as well as on platforms that exhibit roll/pitch motion (of the sensor, the platform or both)."
url='http://ros.org/wiki/hector_mapping'

pkgname='ros-hydro-hector-mapping'
pkgver='0.3.2'
_pkgver_patch=0
arch=('any')
pkgrel=1
license=('BSD')

ros_makedepends=(ros-hydro-catkin
  ros-hydro-message-generation
  ros-hydro-message-filters
  ros-hydro-tf-conversions
  ros-hydro-roscpp
  ros-hydro-laser-geometry
  ros-hydro-nav-msgs
  ros-hydro-tf
  ros-hydro-visualization-msgs)
makedepends=('cmake' 'git' 'ros-build-tools'
  ${ros_makedepends[@]}
  boost
  eigen3)

ros_depends=(ros-hydro-message-filters
  ros-hydro-tf-conversions
  ros-hydro-message-runtime
  ros-hydro-roscpp
  ros-hydro-laser-geometry
  ros-hydro-nav-msgs
  ros-hydro-tf
  ros-hydro-visualization-msgs)
depends=(${ros_depends[@]}
  boost
  eigen3)

_tag=release/hydro/hector_mapping/${pkgver}-${_pkgver_patch}
_dir=hector_mapping
source=("${_dir}"::"git+https://github.com/tu-darmstadt-ros-pkg-gbp/hector_slam-release.git"#tag=${_tag})
md5sums=('SKIP')

build() {
  # Use ROS environment variables
  /usr/share/ros-build-tools/clear-ros-env.sh
  [ -f /opt/ros/hydro/setup.bash ] && source /opt/ros/hydro/setup.bash

  # Create build directory
  [ -d ${srcdir}/build ] || mkdir ${srcdir}/build
  cd ${srcdir}/build

  # Fix Python2/Python3 conflicts
  /usr/share/ros-build-tools/fix-python-scripts.sh ${srcdir}/${_dir}

  # Build project
  cmake ${srcdir}/${_dir} \
        -DCMAKE_BUILD_TYPE=Release \
        -DCATKIN_BUILD_BINARY_PACKAGE=ON \
        -DCMAKE_INSTALL_PREFIX=/opt/ros/hydro \
        -DPYTHON_EXECUTABLE=/usr/bin/python2 \
        -DPYTHON_INCLUDE_DIR=/usr/include/python2.7 \
        -DPYTHON_LIBRARY=/usr/lib/libpython2.7.so \
        -DSETUPTOOLS_DEB_LAYOUT=OFF
  make
}

package() {
  cd "${srcdir}/build"
  make DESTDIR="${pkgdir}/" install
}
