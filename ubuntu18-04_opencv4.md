OpenCV4 installation installation guide

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
 -D INSTALL_C_EXAMPLES=ON \
 -D INSTALL_PYTHON_EXAMPLES=ON \
 -D OPENCV_GENERATE_PKGCONFIG=ON \
 -D OPENCV_EXTRA_MODULES_PATH=~/opencv_build/opencv_contrib/modules \
 -D BUILD_EXAMPLES=ON ..
```
5 - Make it all 
```
make -j8
```
**Note** : -j8 meaning cpu core count. In this example cpu core count 8

6 - Install it all
```
sudo make install
```
7 - Checking on python3
```sh
python3 -c "import cv2; print(cv2.__version__)"
```
