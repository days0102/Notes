<!--
 * @Author: Linux_Outsider
 * @Date: 2021-10-12 19:41:00
 * @LastEditors: Linux_Outsider
 * @LastEditTime: 2021-10-26 14:51:03
 * @Description: In User Settings Edit
 * @FilePath: /Notes/Git/GitRemote.md
-->
# Git 远程操作
## 查看远程仓库
- git remote 
- git remote -v   #查看远程仓库和对应的URL
---
## 将本地仓库与Github仓库关联
- git remote add [远程库名称] [仓库链接]
- ex : git remote add origin git@github.com:days0102/Notes.git
> 之后将会用origin代替仓库链接
---
## 将本地仓库内容推送到远程仓库
- git push [远程仓库名] [本地仓库要推送的分支名]
- ex : git push origin master   #将本地的master分支推送到远程仓库origin上
---
## 将远程仓库的内容拉取到本地不合并
- git fetch [远程仓库名] (远程分支)
- ex : git fetch origin #将远程仓库全部拉取到本地（不与当前分支合并）
- ex : git fetch origin master #将远程仓库master分支拉取到本地仓库（不与当前分支合并）
---
## 合并本地分支
- git merge [分支名]
- git merge test #将test分支合并到当前分支
---
## 将远程仓库的内容拉取到本地仓库上并合并本地内容
- git pull [远程仓库名]
- ex : git pull origin #将远程仓库拉取到本地仓库上
---
## 重命名远程仓库
- git remote rename [旧仓库名] [新仓库名]
- git remote rename origin master #将origin改为master
---
## 删除远程仓库
- git remote rm [仓库名]
- git re mote rm origin 

## 更改远程仓库的地址
- git remote set-url [仓库名] [新地址]