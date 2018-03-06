### 安装crossover版的QQ  
1. 检查软件包的依赖：
```
sudo apt-get clean 
sudo apt-get -f install
```
2. 由于系统是64位，在此添加对32位库的支持
```
sudo dpkg --add-architecture i386  
sudo apt-get update  
sudo apt-get install lib32z1 lib32ncurses5 
```
3. 下载crossover必要文件
- [百度网盘](https://pan.baidu.com/s/1pR1K4QdnGT0Rm_VVsBq5wQ)， 密码: wrfg
4. 使用以下命令依次安装。 
```
sudo dpkg -i crossover-15_15.0.3-1_all.deb
sudo dpkg -i crossover-15_15.0.3-1_all-free.deb
sudo dpkg -i deepin-crossover-helper_1.0deepin0_all.deb
```
如果中途出现依赖问题
```
sudo apt-get install -f
```
然后再重新安装上一步安装操作 

5. 安装QQ的deb包
```
sudo dpkg -i apps.com.qq.im_8.1.17255deepin11_i386.deb
```
6. 运行QQ，如果字体是乱码： 
- 原版那个ttf是SJIS内码，没有很多简体中文的汉字，是乱码的真正起因。
- 下载一个字体到crossover的fonts文件夹，替换原有的ume-ui-gothic.ttf
- 在这里使用的是宋体（simsun.ttf）
```
cp simsun.ttf /opt/cxoffice/share/wine/fonts
cd /opt/cxoffice/share/wine/fonts
rm ume-ui-gothic.ttf
```
---
### 可选步骤
7. 创建一个结束QQ进程的脚本  
- 当退了QQ，然后再次登录同一个账号的时候，会发现占用（登录失败）。
我们可以使用命令来结束进程，但是每次都输入一串命令太麻烦，所以，创建一个脚本，每次需要使用，执行它就好了。
```
sudo gedit /usr/bin/killqq       （路径放你喜欢的就好，方便自己调用就行）
```
接下来吧下面这串内容复制进去：
```
ps aux|grep -v grep|grep wine|cut -c 9-15|xargs kill   
ps aux|grep -v grep|grep QQ|cut -c 9-15|xargs kill   
ps aux|grep -v grep|grep qq|cut -c 9-15|xargs kill   
pkill  plugplay.exe  
pkill  explorer.exe  
pkill  services.exe 
```
再设置权限：
```
cd  /usr/bin               (进入目录)
sudo chmod 777 killqq      (赋予权限)
killqq                     (执行)
```
以后每次下了QQ想要再次登录（不重启的情况下），执行killqq就好。

