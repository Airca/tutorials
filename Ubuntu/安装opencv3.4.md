# 安装opencv3.4
## 操作步骤
1.  更新ubuntu上的一些库
    ```
    sudo apt-get update
    sudo apt-get upgrade
    ```
2.  安装一些搭建opencv的库
    ```
    sudo apt-get install cmake
    sudo apt-get install build-essential libgtk2.0-dev libavcodec-dev libavformat-dev libjpeg.dev libtiff4.dev libswscale-dev libjasper-dev
    ```
3.  下载opencv3源码 (zip,tar.gz都行)  

    [opencv github下载地址](https://github.com/opencv/opencv/releases)

4.  下载、解压完毕后，创建编译文件夹，设置cmake编译参数，提供一些可供选择的安装选项
    ```
    cd ./opencv-3.4.1
    mkdir build
    cd build
    cmake -D CMAKE_BUILD_TYPE=Release -D CMAKE_INSTALL_PREFIX=/usr/local ..
    ```
5.  开始编译openCv
    ```
    sudo make 
    sudo make install 
    ```
6.  配置环境变量
    创建一个配置文件
    ```
    sudo gedit /etc/ld.so.conf.d/opencv.conf
    ```
    执行此命令后打开一个空白的文件，在文件末尾添加
    ```
    /usr/local/lib
    ```
    执行如下命令使得刚才的配置路径生效
    ```
    sudo ldconfig
    ```
7.  配置bash
    ```
    sudo gedit /etc/bash.bashrc 
    ```
    在最末尾添加
    ```
    PKG_CONFIG_PATH=$PKG_CONFIG_PATH:/usr/local/lib/pkgconfig  
    export PKG_CONFIG_PATH
    ```
    保存，执行如下命令使得配置生效
    ```
    source /etc/bash.bashrc 
    ```
    更新
    ```
    sudo updatedb
    ```
## 验证是否安装成功  
```
cd ./opencv-3.4.1/smaples/cpp/example_cmake
cmake .
make
./opencv_example
```
如果可看到打开了摄像头，在左上角有一个hello opencv，即表示配置成功。
