# 在你的ubuntu機器上安裝openCV

## 環境
ubuntu 16.04

## 預安裝
```shell=
$ sudo apt-get install build-essential cmake pkg-config
$ sudo apt-get install libjpeg8-dev libtiff5-dev libjasper-dev libpng12-dev
$ sudo apt-get install libavcodec-dev libavformat-dev libswscale-dev libv4l-dev
$ sudo apt-get install libxvidcore-dev libx264-dev
$ sudo apt-get install libgtk-3-dev
$ sudo apt-get install libatlas-base-dev gfortran #如果想要在python上使用openCV的話
$ sudo apt-get install python2.7-dev python3.5-dev
```

## 下載openCV原始碼
```shell=
$ cd ~
$ git clone https://github.com/opencv/opencv.git
$ cd opencv
$ git checkout [tab][tab] #選{你要的版本}
$ git clone https://github.com/opencv/opencv_contrib.git
$ cd opencv_contrib
$ git checkout [tab][tab] #選{相同的版本}
```

## 編譯openCV
產生出makefile
```shell=
$ cd ~/opencv
$ mkdir build
$ cd build
$ cmake -D CMAKE_BUILD_TYPE=RELEASE \
    -D CMAKE_INSTALL_PREFIX=/usr/local \
    -D INSTALL_PYTHON_EXAMPLES=OFF \ #如果有編譯python的話，改成ON
    -D INSTALL_C_EXAMPLES=OFF \
    -D OPENCV_EXTRA_MODULES_PATH=~/opencv/opencv_contrib/modules \ #改成contribution下的modules路徑
    -D PYTHON_EXECUTABLE=~/.virtualenvs/cv/bin/python \ #如果有編譯python的話，改成python執行擋路徑
    -D BUILD_EXAMPLES=ON \
    .. #CMakeLists.txt的路徑
```
用makefile編譯
```shell=
$ make -j8
```

## 安裝openCV
```shell=
$ sudo make install
$ sudo ldconfig
```



## 參考
- [Ubuntu 16.04: How to install OpenCV](http://www.pyimagesearch.com/2016/10/24/ubuntu-16-04-how-to-install-opencv/)
