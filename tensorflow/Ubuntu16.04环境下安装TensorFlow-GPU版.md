# Ubuntu16.04环境下安装TensorFlow-GPU版  
## 安装流程  
### 安装显卡驱动  
1. 使用命令`vim /etc/modprobe.d/blacklist.conf`编辑文件，在文件末尾输入以下内容以屏蔽系统集成显卡驱动：  
```
blacklist vga16fb
blacklist nouveau
blacklist rivafb
blacklist rivatv
blacklist nvidiafb
```
2. 使用快捷键`Ctrl+Alt+F1`切换至命令行界面；  
3. 关闭图形系统：`service lightdm stop`；  
4. 删除之前的驱动：`apt purge nvidia-*`；  
5. 更新源：`apt update`；  
6. 查询驱动的可用版本：`apt-cache search nvidia-*`；  
7. 安装驱动：`apt install nvidia-xxx`；xxx是上一步中查询到可用的最新版本号。  
8. 输入`reboot`命令重启系统。  
### 软件下载
- CUDA8.0：[官网](https://developer.nvidia.com/cuda-80-ga2-download-archive)；
- cuDNN6.0：；
