---
title: hexo
date: 2020-11-12 13:08:40
tags: hexo
author: 周俊伟
keywords: hexo,hexo使用,hexo常用命令
# img: /medias/featureimages/filereader/1.jpg
# coverImg: /medias/featureimages/filereader/1.jpg
categories: hexo 
---
## 创建文章
```bash
hexo new [layout] <title>
```
创建一个新文章。如果未layout提供，Hexo将使用default_layoutfrom _config.yml。如果title包含空格，请用引号引起来。


|  Option   | Description  |
|  ----  | ----  |
| `-p`, `--path` | 发布路径。自定义帖子的路径。 |
| `-r, --replace` | 替换当前帖子（如果存在）。 |
| `-s`, `--slug` | 自定义帖子的URL。 |

## 生成

```dash
$ hexo g
```

生成静态文件。

| 选项                   | 描述                                               |
| :--------------------- | :------------------------------------------------- |
| `-d`， `--deploy`      | 生成完成后进行部署                                 |
| `-w`， `--watch`       | 观看文件更改                                       |
| `-b`， `--bail`        | 如果在生成过程中引发任何未处理的异常，则会引发错误 |
| `-f`， `--force`       | 强制再生                                           |
| `-c`， `--concurrency` | 并行生成的最大文件数。默认为无穷大                 |

## 服务器

```
$ hexo s
```

启动本地服务器。默认情况下，该位置为`http://localhost:4000/`。

| 选项              | 描述                         |
| :---------------- | :--------------------------- |
| `-p`， `--port`   | 覆盖默认端口                 |
| `-s`， `--static` | 仅提供静态文件               |
| `-l`， `--log`    | 启用记录器。覆盖记录器格式。 |

## clean

```
$ hexo clean
```

清除缓存文件（`db.json`）和生成的文件（`public`）。

## 部署

```
$ hexo d
```

部署您的网站。

| 选项                | 描述       |
| :------------------ | :--------- |
| `-g`， `--generate` | 部署前生成 |

