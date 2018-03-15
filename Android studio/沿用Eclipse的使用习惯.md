# 沿用Eclipse的使用习惯
1. 打开Android Studio中的Setting面板，选中Keymap一项，把Default切换为Eclipse。
2. 然而这是不够的，还有一些常用的快捷键需要修改。

|名字|用处|键位|
|:-|:-|:-|
|show intention actions|设置快速修复错误提示代码|ctrl+1|
|Code-Completion-Basic|补全代码|alt+/|
|Class Name Completion|补全代码（没弄清楚与上一个区别）|alt+.|
|Move up|向上移动整行代码|ctrl+up|
|Move down|向下移动整行代码|ctrl+down|
3. Ctrl+Alt+Down/Up 冲突问题  
  - 在ubuntu终端下执行命令
  ```
  gsettings set org.gnome.desktop.wm.keybindings switch-to-workspace-down "['']"
  gsettings set org.gnome.desktop.wm.keybindings switch-to-workspace-up "['']"
  ```  
  - 这时设置  
  
|名字|用处|键位|
|:-|:-|:-|
|Duplicate Entire Lines|向下复制整行代码|Ctrl+Alt+Down|
