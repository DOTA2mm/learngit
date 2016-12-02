## Note for learn git tool

> 2016/12/2
> Chuck

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

### 分支策略
- 首先，仍然创建并切换dev分支：
    ```
    $ git checkout -b dev
    Switched to a new branch 'dev'
    ```
- 修改readme.txt文件，并提交一个新的commit：
    ```
    $ git add readme.txt 
    $ git commit -m "add merge"
    [dev 6224937] add merge
    1 file changed, 1 insertion(+)
    ```
- 现在，我们切换回master：
    ```
    $ git checkout master
    Switched to branch 'master'
    ```
- 准备合并dev分支，请注意--no-ff参数，表示禁用Fast forward：
    ```
    $ git merge --no-ff -m "merge with no-ff" dev
    Merge made by the 'recursive' strategy.
    readme.txt |    1 +
    1 file changed, 1 insertion(+)
    ```
    > 因为本次合并要创建一个新的commit，所以加上-m参数，把commit描述写进去。
- 合并后，我们用git log看看分支历史：
    ```
    $ git log --graph --pretty=oneline --abbrev-commit
    *   7825a50 merge with no-ff
    |\
    | * 6224937 add merge
    |/
    *   59bc1cb conflict fixed
    ...
    ```