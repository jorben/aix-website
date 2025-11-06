---
date: '2025-11-06T10:37:03+08:00'
draft: false
title: '如何撤销git commit'
authors:
  - name: Jorben
    link: https://github.com/jorben
    image: https://github.com/jorben.png
tags:
  - Git
---

常常在commit之后才发现remote有更新，如果继续push，可能会遇到冲突而产生Merge记录。
不想让Merge记录影响commit log的队形，这时就需要撤销最近一次的 commit，保留更改在暂存区。
可以使用 `git reset --soft` 命令来撤销最近的 commit 但保留更改在暂存区。

<!--more-->
## 具体操作

```bash
# 撤销最近一次的 commit，更改会保留在暂存区
git reset --soft HEAD~1

# 或者使用 commit hash 来撤销到特定提交
git reset --soft <commit-hash>
```

## 其他相关选项

- `--soft`：撤销 commit，但保留更改在**暂存区**
- `--mixed`（默认）：撤销 commit，更改保留在**工作区**（不在暂存区）
- `--hard`：**危险**！完全丢弃 commit 的更改

## 操作步骤示例

```bash
# 1. 查看当前状态
git status

# 2. 撤销最近一次 commit（保留在暂存区）
git reset --soft HEAD~1

# 3. 确认更改已在暂存区
git status
```

## 注意事项
- 如果已经推送到远程仓库，不建议使用 reset，而应该使用 `git revert`
- 使用前最好确认当前分支没有未保存的重要更改

这样就可以安全地将 commit 撤销，同时保留你的修改在暂存区了！