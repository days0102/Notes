<!--
 * @Author: Linux_Outsider
 * @Date: 2021-10-12 19:41:00
 * @LastEditors: Outsider
 * @LastEditTime: 2021-10-28 23:06:11
 * @Description: In User Settings Edit
 * @FilePath: \Notes\Solutions\Windows\UnloadingProblem.md
-->
# Windows 卸载（文件丢失）软件残留
![](.\Picture\2021-09-09%20230347.jpg)  
因为软件已经不在系统中，所以显示的软件只是该软件之前的安装路径
---
## 解决方法
1. Win+R打开窗口
2. 输入regedit进入注册表编辑器
3. 进入HKEY_CLASSES_ROOT
4. 找到对应的软件名称找到shell项，删除shell下open中的command项  
![](.\Picture\2021-09-10%20191358.jpg)
## HKEY_CLASSES_ROOT中各项的功能
1. \* : 按下鼠标右键时会出现的菜单选项， * 表示任何情况下都出现(不论文件还是文件夹)
2. directory : 按下鼠标右键时出现的菜单选项
3. .xxx : 对应的文件后缀
4. 其它的为对应的软件
