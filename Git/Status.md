文件的状态

Git 中的文件只有已跟踪和未跟踪这两种状态。使用git status 查看。

```bash
Changes not staged for commit: --已跟踪的文件发生了变化还没放到暂存区
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   README.md

Changes to be committed: --已暂存，提交（commit）后将被留存在后续的历史记录中
  (use "git restore --staged <file>..." to unstage)
        modified:   README.md

Untracked files: --新文件，用gitadd跟踪它
  (use "git add <file>..." to include in what will be committed)
        Git/
```

如何查看尚未暂存的文件变更？
?
git diff

