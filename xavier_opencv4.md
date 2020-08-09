OpenCV4 installation installation guide for Jetson Xavier 

1 - First of all update Ubuntu system

```
sudo apt update
```
2 - Install dependencies
```
sudo apt install build-essential cmake git pkg-config libgtk-3-dev \
    libavcodec-dev libavformat-dev libswscale-dev libv4l-dev \
    libxvidcore-dev libx264-dev libjpeg-dev libpng-dev libtiff-dev \
    gfortran openexr libatlas-base-dev python3-dev python3-numpy \
    libtbb2 libtbb-dev libdc1394-22-dev
```
3 - Download openCV version. You can change it.

```
mkdir ~/opencvBuild && cd ~/opencvBuild
git clone https://github.com/opencv/opencv.git tags/4.3.0
git clone https://github.com/opencv/opencv_contrib.git tags/4.3.0
```
4 - Get in the openCV folder and build
```
cmake -D CMAKE_BUILD_TYPE=RELEASE \
    -D CMAKE_INSTALL_PREFIX=/usr/local \
    -D INSTALL_PYTHON_EXAMPLES=ON \
    -D INSTALL_C_EXAMPLES=OFF \
    -D OPENCV_EXTRA_MODULES_PATH=~/opencv_build/opencv_contrib/modules \
    -D BUILD_EXAMPLES=ON \
    -D WITH_CUDA=ON \
    -D CUDA_ARCH_BIN=${ARCH_BIN} \
    -D CUDA_ARCH_PTX="" \
    -D ENABLE_FAST_MATH=ON \
    -D CUDA_FAST_MATH=ON \
    -D WITH_CUBLAS=ON \
    -D WITH_LIBV4L=ON \
    -D WITH_GSTREAMER=ON \
    -D WITH_GSTREAMER_0_10=OFF \
    -D WITH_TBB=ON \
    ../
```
5 - Make it all 
```
make -j6
```
**Note** : -j6 meaning cpu core count. In this example cpu core count 6

6 - Install it all
```
sudo make install
```
7 - Linking .so file

```sh
sudo ldconfig
```
