# 分支
## 新建分支
太简单了 git checkout -b dev-wxy
push --set-upstream origin xxx

## Reset
重中之重

1. 简单来说理解三棵树：本地文件，索引，HEAD
2. 索引就是暂存区，也就是说 add 命令将本地修改添加到索引上
3. HEAD 总是指向最后一次**提交**，也就是说 commit 将索引的修改更新到 HEAD

在理解以上三者关系后，以下内容清楚地描述了 reset 命令的作用方式: 
> reset 命令会以特定的顺序重写这三棵树，在你指定以下选项时停止：
>
>1. 移动 HEAD 分支的指向 （若指定了 --soft，则到此停止）
>
>2. 使索引看起来像 HEAD （若未指定 --hard，则到此停止） --什么参数都不添加，等同指定 --mixed
>
>3. 使工作目录看起来像索引（指定了 --hard）

如果指定了文件，如`git reset file.txt`，这等同于`git reset file.txt HEAD --mixed`；\
第一步会跳过。然后执行第二步，让索引中的这个文件看起来像HEAD。

让我们想想 add 命令做的事，显然 reset 命令此时做了相反的事。因此reset可以用于撤销add。

### 压缩
*让你的git提交记录更清爽，看起来也更专业！*
如果你遵从了频繁提交的建议，但在merge时不希望reviewer看到密密麻麻的历史记录，使用压缩。

假设一个场景：文件A经历了两次变动，每次变动你都提交了，这时你希望只有一次提交。
?
git reset HEAD~2 --soft 先把HEAD指到两个版本以前，然后
git commit -m '修改了两次，压缩成了一个提交'

## Merge


## 远程仓库
```bash
PS E:\projects\kataa> git remote -v 
> git remote show origin
//查看远程仓库
origin  https://github.com/Jeiplos/kataa.git (fetch)
origin  https://github.com/Jeiplos/kataa.git (push)

> git fetch
git fetch 命令只会将数据下载到你的本地仓库，不会合并和修改，如果跟踪了上游，git pull 会fetch当前分支后尝试自动合并

```

## 标签
```
git tag -a v1.4 -m "my version 1.4"
git tag v1.4 --轻量标签
git tag v1.2 ab23f --git log后为指定的 commit 打标签
git push origin <tagname>。

：一个有点意思的场景：如果我要基于某个tag修bug，该怎么做？
我会想先 git checkout <tag> 看看 bug 内容。
但如果这时我直接开始修改会怎么样呢？
此时我们实际上处于了 分离头指针 的状态，我们修改后指针位置不在任何一个分支上
所以应该要 git checkout -b <branchname> <tagname>
```
