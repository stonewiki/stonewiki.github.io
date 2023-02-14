---
title: Harbor
toc: false
date: 2023-02-14 23:04:48
tags: [Harbor]
---

#### 如何在Harbor上创建镜像
1. 打Docker Tag
``` bash
docker tag  SOURCE_IMAGE[:TAG] IP:PORT/IMAGE[:TAG]
# IP:PORT Harbor地址
```

2. 推送到仓库
``` bash
docker push IP:PORT/IMAGE[:TAG]
```