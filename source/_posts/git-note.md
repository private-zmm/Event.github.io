---
title: git
date: 2020-11-12 13:34:44
tags: git
author: 周俊伟
keywords: git,git日常使用,git常用命令
# img: /medias/featureimages/filereader/1.jpg
# coverImg: /medias/featureimages/filereader/1.jpg
categories: [git,tool]
---

## commit

`git add . `

`git commit -m ""`

```dash
git commit -m "feat: aas"
```

### commit规范

#### Commit message格式

```
<type>: <subject>
```

注意冒号后面有空格。

#### type

用于说明 commit 的类别，只允许使用下面7个标识。

- `feat`：新功能（feature）
- `fix`：修补bug
- `docs`：文档（documentation）
- `style`： 格式（不影响代码运行的变动）
- `refactor`：重构（即不是新增功能，也不是修改bug的代码变动）
- `test`：增加测试
- `chore`：构建过程或辅助工具的变动

*如果type为`feat`和`fix`，则该 commit 将肯定出现在 Change log 之中。*

#### log

查看git commit提交记录

```dash
git log -10
```

-10 显示最近的十条

#### reset

**Git回滚代码到某个commit**

回退命令：

```git reset --hard HEAD^ ```回退到上个版本



```git reset --hard HEAD~3``` 回退到前3次提交之前，以此类推，回退到n次提交之前

```git reset --hard commit_id``` 退到/进到，指定commit的哈希码（这次提交之前或之后的提交都会回滚）

回滚后提交可能会失败，必须强制提交



**强推到远程：(可能需要解决对应分支的保护状态)**

```git push origin HEAD --force```

[^]: 持续更新中。。。