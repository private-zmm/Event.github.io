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

[^]: 持续更新中。。。