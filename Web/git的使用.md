###### git 的使用

> [!note]
>
> [Git 教程 | 菜鸟教程 (runoob.com)](https://www.runoob.com/git/git-tutorial.html)

# 初始化仓库

```bash
# 初始化当前目录作为git仓库
git init
# 初始化指定目录作为git仓库
git init newrepo #初始化后，会在 newrepo 目录下会出现一个名为 .git 的目录
```

# 从现有 Git 仓库中拷贝项目

```bash
# 命令基本格式
git clone <repo>
# 例如:
git clone git://github.com/schacon/grit.git

# 克隆到指定的目录
git clone <repo> <directory>
# 例如:
git clone git://github.com/schacon/grit.git mygrit
```

# 配置

```bash
# 列出当前git配置信息
git config --list
# 编辑git配置文件
git config -e # 针对当前仓库
# 或者
git config -e --global  # 针对系统上所有仓库
# 设置提交代码时的用户信息
git config --global user.name "xxxx" # 设置用户名
git config --global user.email xxxx@gmail.com # 设置邮箱
# 获取当前项目大小写忽略状态值
git config --get core.ignorecase
git config core.ignorecase #可以用core 核心 ignore 忽略 case 大小写来记忆
# 设置当前大小写忽略状态值为false，表示对大小写敏感
git config core.ignorecase false
```

# 基本操作

```bash
# 创建仓库命令
git init          # 初始化仓库
git clone         # 拷贝一份远程仓库，也就是下载一个项目。

# 提交与修改
git add           # 添加文件到暂存区
git status        # 查看仓库当前的状态，显示有变更的文件。
git diff          # 比较文件的不同，即暂存区和工作区的差异。
git commit        # 提交暂存区到本地仓库。
git reset         # 回退版本。
git rm            # 将文件从暂存区和工作区中删除。
git mv            # 移动或重命名工作区文件。
git checkout      # 分支切换。
git switch        # （Git 2.23 版本引入） 更清晰地切换分支。
git restore       # （Git 2.23 版本引入） 恢复或撤销文件的更改。

# 远程操作
git remote        # 远程仓库操作
git fetch         # 从远程获取代码库
git pull          # 下载远程代码并合并
git push          # 上传远程代码并合并

# 提交日志
git log           # 查看历史提交记录
git blame <file>  # 以列表形式查看指定文件的历史修改记录

```

# 分支管理

```bash
# 查看本地分支
git branch

# 查看所有分支(包含原远程分支)
git branch -a

# 创建分支
git branch (branchname)

# 切换分支
git checkout (branchname)
# 当你切换分支的时候，Git 会用该分支的最后提交的快照替换你的工作目录的内容， 所以多个分支不需要多个目录。

# 创建新分支并立即切换到该分支下
git checkout -b (branchname)

# 删除分支
git branch -d (branchname)
# 有时删除分支会告知尝试删除的分支没有被完全合并到其它分支中。Git默认会阻止你删除一个包含尚未合并更改的分支，以避免丢失数据。如果要强制删除，可以使用带有-D选项的git branch命令来强制删除它。
git branch -D (branchname)
# 如果你不想每次尝试删除未合并的分支时都看到这个提示信息，你可以按照错误信息的另一个提示来禁用这个警告：
git config advice.forceDeleteBranch false

# 合并分支
# 一旦某分支有了独立内容，你终究会希望将它合并回到你的主分支。 你可以使用以下命令将任何分支合并到当前分支中去
git merge

# 例如：将dev分支合并到main分支的步骤
git checkout main # 切换到main分支
git merge dev # 将dev分支合并到当前分支(main分支)
```

# Git 查看提交历史

```bash
git log [选项] [分支名/提交哈希]
# 常用选项:
# -p：显示提交的补丁（具体更改内容）。
# --oneline：以简洁的一行格式显示提交信息。
# --graph：以图形化方式显示分支和合并历史。
# --decorate：显示分支和标签指向的提交。
# --author=<作者>：只显示特定作者的提交。
# --since=<时间>：只显示指定时间之后的提交。
# --until=<时间>：只显示指定时间之前的提交。
# --grep=<模式>：只显示包含指定模式的提交消息。
# --no-merges：不显示合并提交。
# --stat：显示简略统计信息，包括修改的文件和行数。
# --abbrev-commit：使用短提交哈希值。
# --pretty=<格式>：使用自定义的提交信息显示格式。

git blame [选项] <文件路径>
# 常用的选项：
# -L <起始行号>,<结束行号>：只显示指定行号范围内的代码注释。
# -C：对于重命名或拷贝的代码行，也进行代码行溯源。
# -M：对于移动的代码行，也进行代码行溯源。
# -C -C 或 -M -M：对于较多改动的代码行，进行更进一步的溯源。
# --show-stats：显示包含每个作者的行数统计信息。
```

# Git 远程仓库(Github)

> [参考](https://www.runoob.com/git/git-remote-repo.html)

```bash
# 添加远程库
git remote add [shortname] [url]
# 由于你的本地 Git 仓库和 GitHub 仓库之间的传输是通过SSH加密的，所以我们需要配置验证信息：
# 使用以下命令生成 SSH Key：
ssh-keygen -t rsa -C "youremail@example.com"
# 后面的 your_email@youremail.com 改为你在 Github 上注册的邮箱，之后会要求确认路径和输入密码

# 更改远程仓库地址 如果远程仓库地址发生变化时可以这样更新地址
git remote set-url <name(默认是origin)> 新仓库地址
# 例如：更新远程仓库origin的地址为 https://github.com/AzureHearted/vue2-project.git
git remote set-url origin https://github.com/AzureHearted/vue2-project.git
```

# 分支关联

```bash
# 查看分支关联情况
git branch -vv
# 设置本地分支与远程分支关联
git branch --set-upstream-to=origin/<remoteBranch> <localBranch>
# 例如：将本地的dev与远程仓库origin的main分支进行关联
git branch --set-upstream-to=origin/main dev
```

# 推送本地仓库到远程仓库

```bash
# 先pull
git pull
# 再push
git push
# 本地分push到远程仓库的指定分支
git push -u origin <localBranch>:<remoteBranch>
# 例如：将本地的dev分支push到远程仓的main分支,注意这个操作会更改分支之间的关联,push后需要需要手动切换回来
```

# 拉取远程分支到指定的本地分支

````bash
git checkout -b (本地分支名称) (远程仓库名称)/(远程分支名称)
# 由于添加了-b字段，这样会先判断本地是否有该分支，没有就创建
````















# The End