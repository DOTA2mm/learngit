## This flie for learn git tool
> 2016/12/2

- 创建SSH key `$ ssh-keygen -t rsa -C "youremail@example.com"`
- 要关联一个远程库，使用命令 `git remote add origin git@server-name:path/repo-name.git`
    1. 关联后，使用命令 `git push -u origin master` 第一次推送 `master` 分支的所有内容
    2. 此后，每次本地提交后，只要有必要，就可以使用命令 `git push origin master` 推送最新修改
