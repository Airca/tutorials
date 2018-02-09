# Ubuntu16.04环境下安装TensorFlow-GPU版  
## 安装流程  
### 安装显卡驱动  
- 使用命令`vim /etc/modprobe.d/blacklist.conf`编辑文件，在文件末尾输入以下内容以屏蔽系统集成显卡驱动：  
```
blacklist vga16fb
blacklist nouveau
blacklist rivafb
blacklist rivatv
blacklist nvidiafb
```
- 使用快捷键`Ctrl+Alt+F1`切换至命令行界面;  
- 关闭图形系统：`service lightdm stop`;  
- 删除之前的驱动：`apt purge nvidia-*`;  
- 更新源：`apt update`；  
- 查询驱动的可用版本：`apt-cache search nvidia-*`;
- 安装驱动：`apt install nvidia-xxx`;xxx是上一步中查询到可用的最新版本号。  
- 输入`reboot`命令重启系统。  
### 下载CUDA与cuDNN
- CUDA8.0：[官网](https://developer.nvidia.com/cuda-80-ga2-download-archive)、[百度云](https://pan.baidu.com/s/1snsRaBN);
- cuDNN6.0：[百度云](https://pan.baidu.com/s/1nwbNXg9);
### 安装CUDA
下载文件存放于`/home/你的名字/Downloads/`目录下;  
执行以下命令进行安装：  
```
$ dpkg -i cuda-repo-ubuntu1604-8-0-local-ga2_8.0.61-1_amd64.deb
$ apt update
$ apt install cuda
```
输入命令`vim /home/你的名字/.bashrc`编辑文件以配置环境变量，在打开的文件末尾追加以下内容：  
```  
export CUDA_HOME=/usr/local/cuda
export LD_LIBRARY_PATH=$CUDA_HOME/lib64:$CUDA_HOME/extras/CUPTI/lib64:$LD_LIBRARY_PATH
export PATH=$CUDA_HOME/bin:$PATH
```  
输入命令`source /home/你的名字/.bashrc`使环境变量生效。  
输入命令`nvcc -V`查看版本号以验证CUDA是否安装成功。 
### 安装cuDNN
下载文件存放于/home/你的名字/Download/目录下；  
执行一下命令完成安装：  
```
cd /home/你的名字/Downloads/
tar -zxvf ./cudnn-8.0-linux-x64-v6.0.tgz -C $CUDA_HOME/../
```
###安装Tensorflow-GPU
安装pip：  
`apt install python-pip`
更新pip：  
`pip install -U pip`
安装tensorlfow-gpu：  
`pip install tensorflow-gpu`
### 验证安装   
启动python命令行：`python`； 
引入`tensorflow：import tensorflow as tf`； 
查看tensorflow版本：`tf.__version__`； 
创建Session：`tf.Session()`，可以在设备名处看到你的显卡名称表示安装完成； 
退出python：`exit()`。



