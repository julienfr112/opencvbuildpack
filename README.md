# opencvbuildpack

##ubuntu
sudo apt install -y build-essential python3.6-dev mlocate

##aws
sudo yum -y groupinstall "Development Tools"
sudo yum -y install python36-devel cmake
sudo python36 -m pip install numpy
sudo ldconfig


##boost_1_65_1
wget https://dl.bintray.com/boostorg/release/1.65.1/source/boost_1_65_1.tar.gz
tar xvf boost_1_65_1.tar.gz
cd boost_1_65_1
sudo ln -s /usr/include/python3.6m/ /usr/include/python3.6
./bootstrap.sh --with-python=python36 # python3.6 for ubuntu
./b2

##dlib

wget http://dlib.net/files/dlib-19.7.tar.bz2
CMAKE_INCLUDE_PATH=~/boost_1_65_1 CMAKE_LIBRARY_PATH=~/boost_1_65_1/stage/lib python3 setup.py build


##opencv

wget -q https://github.com/Itseez/opencv/archive/3.3.0.tar.gz

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
-DPYTHON3_PACKAGES_PATH=/usr/lib/python3.6/dist-packages \
-DPYTHON_LIBRARY=/usr/lib64/libpython3.6m.so \
-DPYTHON3_NUMPY_INCLUDE_DIRS=/usr/local/lib64/python3.6/site-packages/numpy/core/include/ \
..
make -j4

#-DPYTHON3_NUMPY_INCLUDE_DIRS=/usr/lib/python3/dist-packages/numpy/core/include/ \
#-DPYTHON_LIBRARY=/usr/lib/x86_64-linux-gnu/libpython3.6m.so \


#

get *.so , numpy, numpy/.libs 
