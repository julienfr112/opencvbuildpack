# opencvbuildpack


##boost_1_65_1
wget https://dl.bintray.com/boostorg/release/1.65.1/source/boost_1_65_1.tar.gz
./bootstrap.sh --with-python=python3.6
./b2

##dlib
wget http://dlib.net/files/dlib-19.7.tar.bz2
CMAKE_INCLUDE_PATH=/tmp/boost_1_65_1 CMAKE_LIBRARY_PATH=/tmp/boost_1_65_1/stage/lib python3 setup.py build


##opencv

wget -q https://github.com/Itseez/opencv/archive/3.2.0.tar.gz

cmake \
-DBUILD_TIFF=ON \
-DBUILD_opencv_java=OFF \
-DWITH_CUDA=OFF \
-DENABLE_AVX=OFF \
-DWITH_OPENGL=OFF \
-DWITH_OPENCL=OFF \
-DWITH_IPP=OFF \
-DWITH_TBB=OFF \
-DWITH_EIGEN=OFF \
-DWITH_V4L=OFF \
-DWITH_VTK=OFF \
-DBUILD_TESTS=OFF \
-DBUILD_PERF_TESTS=OFF \
-DCMAKE_BUILD_TYPE=RELEASE \
-DBUILD_opencv_python2=OFF \
-DBUILD_opencv_python3=ON \
-DCMAKE_INSTALL_PREFIX=/usr \
-DPYTHON3_EXECUTABLE=$(which python3.6) \
-DPYTHON3_INCLUDE_DIR=/usr/include/python3.6m \
-DPYTHON3_PACKAGES_PATH=/usr/lib/python3/dist-packages \
-DPYTHON_LIBRARY=/usr/lib/x86_64-linux-gnu/libpython3.6m.so \
-DPYTHON3_NUMPY_INCLUDE_DIRS=/usr/lib/python3/dist-packages/numpy/core/include/ \
..
make -j4
