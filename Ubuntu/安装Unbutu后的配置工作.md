# 安装Unbutu后的配置工作
1.删除libreoffice、amazon的链接、不用的自带软件  
```
sudo apt-get remove libreoffice-common
sudo apt-get remove unity-webapps-common
sudo apt-get remove thunderbird totem rhythmbox empathy brasero simple-scan gnome-mahjongg aisleriot gnome-mines cheese transmission-common gnome-orca webbrowser-app gnome-sudoku landscape-client-ui-install
sudo apt-get remove onboard deja-dup
```
2.卸载火狐浏览器
```
sudo apt-get purge *firefox*
```
3.卸载ubuntu软件中心
```
sudo apt-get purge gnome-software
```
4.系统升级
```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```
5.安装谷歌浏览器
```
sudo wget https://repo.fdzh.org/chrome/google-chrome.list -P /etc/apt/sources.list.d/
wget -q -O - https://dl.google.com/linux/linux_signing_key.pub | sudo apt-key add -
sudo apt-get update
sudo apt-get install google-chrome-stable
```
6.自动清理
```
sudo apt autoremove
```
7.配置pip使用国内源  
 
- [方法1]或者临时使用可以在使用pip的时候加参数：  
  `-i https://pypi.tuna.tsinghua.edu.cn/simple`  
  >比如：`pip install -i https://pypi.tuna.tsinghua.edu.cn/simple pyspider`  
- [方法2]或者直接编辑pip.conf：  
  ```
  cd ~
  mkdir .pip
  cd .pip
  gedit pip.conf
  ```
  在其中加入：  
  ```
  [global] 
  index-url = http://mirrors.aliyun.com/pypi/simple/ 
  [install] 
  trusted-host=mirrors.aliyun.com 
  ```

 

