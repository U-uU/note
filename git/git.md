
### <font color=green>配置个人用户名和邮箱</font>

理论上这里的name和email可以乱写，不过email与远程仓库对不上的话可能不能提交？

    git config --global user.name "Your Name"
    git config --global user.email "email@example.com"

查看设置的用户名和邮箱 `git config --global --list` 另外，可以对某个仓库指定不同的用户名和Email地址，去掉--global参数即可


### <font color=green>创建仓库</font>

在项目的文件夹下，创建本地仓库 `git init`  
`git status`查看仓库当前状态  
`git diff`[查看文本不同diff](/git/diff.md)  
`git add`将修改提交至本地暂存区  
`git commit -m "some words"`将修改提交至本地仓库  

### <font color=green>多分支操作</font>

`git branch name` 创建一个新分支  
`git checkout name` 切换到新分支  
`git checkout -b name` 创建并切换到新分支  
在子分支中，上传提交的操作是一样的，在子分支开发完成后，切回master分支，可以使用`git merge name`将分支内容合并，在合并之前，master不会有子分支的内容  
`git branch -d name`删除子分支  


### <font color=green>添加远程仓库</font>

第一步，创建SSH Key，`ssh-keygen -t rsa -C "youremail@example.com"`，这里的邮箱最好和GitHub上是同一个。

第二步，在.ssh目录下找到`id_rsa`和`id_rsa.pub`两个文件，pub代表公钥，将其内容复制粘贴到GitHub里，具体位置为：“Setting”“SSH Keys”“Add SSH Key”

第三步，在GitHub上创建新仓库，“Create repository”，将本地仓库与其关联。

```
git init
git add .
git commit -m "first commit"      # -m 为指定提交信息，没有将进入vi模式来输入提交信息
git remote add origin https://github.com/U-uU/note.git
git push -u origin master
```

 `# git remote add <远程仓库名称> <远程仓库URL>`添加远程仓库，通常情况下远程仓库叫origin。由于远程库是空的，我们第一次推送master分支时，加上了-u参数，git不但会把本地的master分支内容推送的远程新的master分支，还会把本地的master分支和远程的master分支关联起来，在以后的推送或者拉取时就可以简化命令`git push`。

如果有不希望上传至远程仓库的文件，使用`git rm --cached "filename"` 这样不会删除本地文件，本地仓库push远程仓库后，也会将远程仓库的文件删除。  

当出现冲突时，可以解决后通过`git add <file_name>`标记为已解决。




### <font color=red>坑</font>
存疑🤨
- 将feature分支合入master后，使用revert操作，操作节点永远存在，feature的commit都晚于revert，如果后面再需要将其合入master，都会被revert掉
- 单仓库多团队模式，使用两条master分支，每次发版A将新代码合入masterA，B将masterA合入masterB且将新代码合入masterB，如果B的新代码的commit在A之后，B中的新代码将被masterA的commit覆盖

