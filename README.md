# C-Learn
开始学习C#,对学习过程中的知识点记录



**Git文件提交上传操作**

1、git add    这已操作会将所有已经追踪的文件添加到缓存区，待处置区。若是新增的文件，则需要手工add,将文件添加到缓存区

 提交当前目录下文件 git add . /git add -A

 添加指定类型文件 git add *.md

添加已追踪的文件，删除或修改 git add -u

2、git commit -m  "备注"     文件提交

3、git push origin main/master  推送到远程





**Git文件初始化、更新到本地仓库操作**

1、初始化本地方库   git init

2、建立远程连接  git remote add origin <url>（使用https/或ssh）

​      配置后会后网络端口被封锁，因此使用ssh连接，并修改端口，走https 443的端口

​      配置config文件

- **Windows**: `C:\Users\你的用户名\.ssh\config`
- **Mac/Linux**: `~/.ssh/config`
  （如果 `.ssh` 目录或 `config` 文件不存在，请手动创建。）

```
Host github.com
    Hostname ssh.github.com
    User git
    Port 443
    PreferredAuthentications publickey
    IdentityFile ~/.ssh/id_rsa  # 如果您的密钥是其他名称，如 id_ed25519，请修改这里
```

3、若是https更换为ssh,可执行一下操作

```
git remote set-url origin git@github.com:Eleven-WWH/ZhaoXi.git
```

4、 拉取文件到本地  git pull origin main/master

 git pull 是 git fetch 和 git merge的合并集操作，如下图，会导致更新结点较多，历史追溯困难

![img](https://pic4.zhimg.com/v2-d077b90b0ec3596c45f93051909b0337_r.jpg)

因此可以使用一下命令，即变基操作 ，git pull --rebase

![img](https://pica.zhimg.com/v2-83d33e10b22adf18b6681f6871fc5926_r.jpg)

还可设置全局变量操作，但是自动变基会因为本地文件更改时，变基失败，因为变基前需要服务区干净

```
// git pull默认使用变基操作
git config --global pull.rebase true
```

执行以下操作解决：

git commit：暂存代码

git stash : 它允许你将当前工作目录中的未提交更改（包括已暂存和未暂存的更改）保存到一个栈（stash）中，并将工作目录恢复到干净的状态。这在你需要在多个任务之间切换但又不想提交不完整的代码时非常有用

当git pull完代码后，执行 git stash pop可将之间修改的代码在拉回来。

冲突问题**如果使用git pull有冲突，则合并完冲突之后，执行一下** **git rebase --continue** **就好了**，其它和原先的用法没有任何区别。



