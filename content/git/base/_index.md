+++
title = 'Base'
date = 2023-09-18T09:10:36+08:00
weight = 1
+++


# 删除远程中的.idea

```bash
1.添加.gitignore文件
**/.idea
**/target


2.删除远程文件
git rm -r -n --cached 文件/文件夹名称 
加上 -n 这个参数，执行命令时，是不会删除任何文件，而是展示此命令要删除的文件列表预览。
--cached 表示本地仍旧保留
当前目录下执行
git rm -r -n --cached yarn.lock
git rm -r --cached yarn.lock
git rm -r --cached .idea/*
git rm -r --cached target/*
提交
git commit -m "删除非必要文件"
git push origin master


```

# 配置代理

```

//只对github.com使用代理，其他仓库不走代理
git config --global http.https://github.com.proxy socks5://127.0.0.1:1080
git config --global https.https://github.com.proxy socks5://127.0.0.1:1080
//取消github代理
git config --global --unset http.https://github.com.proxy
git config --global --unset https.https://github.com.proxy


```

# 撤销提交

```

git log 查找要撤销的commit_id q退出查看
git revert commit_id

```

# git clone 断点续传

当git项目较大或网速不快的情况下，git clone可能会中断导致要重新操作，那如何进行断点续传呢

1.新建目录, 命令行进入目录，执行 git init

2. 命令行执行： git fetch https://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@github.com/liangweidonggood/code-java.git

   bash脚本样例， 会循环执行，重试2000次，直到成功后退出

   ```bash
   #!/bin/bash
   set -x

   num=1
   while [ $num -le 2000 ]; do
      git fetch http://xxx.xxx.net/abc/abc-desktop.git
      if [ $? -ne 0 ]; then
          num=$(($num+1))
      else
          break
      fi
   done
   ```
3. 若断掉后，重复执行步骤2， 直到完成下载
4. 命令行执行 git checkout FETCH_HEAD

5. 命令行执行 git remote add origin https://github.com/liangweidonggood/code-java.git

6. 命令行执行 git pull origin main

   git pull https://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@github.com/liangweidonggood/code-java.git

7. 命令行执行 git checkout main
