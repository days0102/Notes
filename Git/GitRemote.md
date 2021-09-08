# Git 远程操作
## 查看远程仓库
- git remote 
- git remote -v   #查看远程仓库和对应的URL
## 将本地仓库与Github仓库关联
- git remote add [远程库名称] [仓库链接]
- ex : git remote add origin git@github.com:days0102/Notes.git
> 之后将会用origin代替仓库链接
---
## 将本地仓库内容推送到远程仓库
- git push [远程仓库名] [本地仓库要推送的分支名]
- ex : git push origin master   #将本地的master分支推送到远程仓库origin上
---
## 将远程仓库的内容拉取到本地仓库上
- git pull [远程仓库名]
- ex : git pull origin #将远程仓库拉取到本地仓库上
---
## 重命名远程仓库
- git remote rename [旧仓库名] [新仓库名]
- git remote rename origin master #将origin改为master

## 删除远程仓库
- git remote rm [仓库名]
- git re mote rm origin 

