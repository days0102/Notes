<!--
 * @Author: Outsider
 * @Date: 2021-09-10 21:06:02
 * @LastEditors: Outsider
 * @LastEditTime: 2021-10-31 21:20:56
 * @Description: In User Settings Edit
 * @FilePath: \Notes\Git\GitBasic.md
-->
# Git 基础
## 初始化Git仓库
- 切换到初始化的目录
- git init
---
## 查看仓库状态
- git status
- git status -s #查看仓库的简短信息(git status --short)
   - ?? : 未跟踪
   -  M : 已修改未暂存
   - M  : 已修改已暂存
   - A  : 已暂存
   - MM : 已修改已暂存后又进行了修改
---
## 跟踪新文件
- git add [文件/目录]
- ex : git add .  #跟踪当前目录下的所有文件（文件夹会递归到文件夹下的每个文件）
- ex : git *.cpp  #跟踪当前目录下的所有.cpp文件
- ex : git test.py #跟踪test.py文件
---
## 删除跟踪的文件
- git rm [文件名]
## 忽略文件
-  .gitignore文件
   - 空行或以#开头的行会被忽略
   - 支持标准的glob模式(类似shell所使用的简化版正则表达式)
      - \* 匹配零个或多个字符
      - [ ]匹配中括号内的任意个字符
        - 使用短划线分隔两个字符表示两个字符范围内的字符
        - ex : [0-9]匹配0-9中的任意字符 
      - ?匹配任意单个字符
      - ** 匹配嵌套目录
        - ex : a/**/z匹配a/z,a/b/z,a/b/c/z等等 
   - 以/开头的模式可用于禁用递归匹配
   - 以/结尾的模式表示目录
   - 以!开始的模式表示取反
 - ex : 
   - *.[ao]  #忽略.a和.o结尾的文件
   - *~ #忽略以~结尾的所有文件
   - !test.a#仍然跟踪test.a文件，即使上条指令要忽略.a类型文件
   - build/ #忽略build文件夹下的所有文件
   - /TODO #忽略当前目录下的TODO文件，而不忽略子目录下的TODO
   - doc/**/*.pdf匹配doc/目录下的所有.pdf文件
---
## 对比当前内容和暂存区内容
- git diff
- git diff --staged # 查看下次提交的已暂存内容
- git diff --cached #查看当前已暂存的内容
---
## 


## 将文件从暂缓区中移除
- git restore --staged [文件名]