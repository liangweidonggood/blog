+++
title = 'Gitbash'
date = 2023-09-18T09:13:11+08:00
weight = 2
+++
# git bash调用cmd中的tree命令

```text
加上winpty去乱码
winpty tree.com : 直接调用 cmd 内置 tree.com 命令.
winpty cmd //c tree : 通知 cmd 调用 tree 命令.

https://github.com/git-for-windows/build-extra/releases
安装 Git For Windows 开发版,Pacman -S tree 安装 tree 命令,然后执行 tree 调用.
https://sourceforge.net/projects/gnuwin32/files/tree/1.5.2.2/tree-1.5.2.2-bin.zip/download
下载 已编译好的 tree.exe 文件到 git bash 安装目录下的 /usr/bin 目录,然后执行 tree 命令.
```
# 提交

```text
step1：拉取服务器代码，更新本地代码，避免覆盖他人代码
    git pull origin master
step2：查看当前项目中有哪些文件被修改过
    git status
    1：Untracked: 未跟踪,一般为新增文件，此文件在文件夹中, 但并没有加入到git库, 不参与版本控制. 通过git add 状态变为Staged.
    2：Modified: 文件已修改, 仅仅是修改, 并没有进行其他的操作.
    3：deleted： 文件已删除，本地删除，服务器上还没有删除.
    4：renamed：
step 3：将状态改变的代码提交至缓存
    git add .
    git add + 文件
    git add -u + 路径：将修改过的被跟踪代码提交缓存
    git add -A + 路径: 将修改过的未被跟踪的代码提交至缓存
step 4：将代码提交到本地仓库中
    git commit -m "xxxx"
step 5：将缓存区代码推送到远程仓库
    git push origin master
```

# git status 显示中文和解决中文乱码

```bash
git config --global core.quotepath false
```
