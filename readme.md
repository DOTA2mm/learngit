## This file for learn git tool
> 2016/12/2

### 远程仓库
- 创建SSH key `$ ssh-keygen -t rsa -C "youremail@example.com"`
- 要关联一个远程库，使用命令 `git remote add origin git@server-name:path/repo-name.git`
    1. 关联后，使用命令 `git push -u origin master` 第一次推送 `master` 分支的所有内容
    2. 此后，每次本地提交后，只要有必要，就可以使用命令 `git push origin master` 推送最新修改

### 分支管理
- 创建并切换分支
    ```
    $ git checkout -b dev
    ```
    等同于以下两行命令
    ```
    $ git branch dev
    $ git checkout dev
    ```
- 在dev branch上提交
    ```git
    $ git add readme.txt 
    $ git commit -m "branch test"
    ```
- 现在，dev分支的工作完成，我们就可以切换回master分支：
    ```
    $ git checkout master
    ```
- 切换到`master`分支后，合并`dev`分支到`master`分支
    ```
    $ git merge dev
    ```
- 合并完成后，就可以放心地删除dev分支了：
    ```
    $ git branch -d dev
    ```

### 解决冲突
- 合并不同分支可能会产生冲突，比如修改了同一行内容
    - Creating a new branch is quick & simple.