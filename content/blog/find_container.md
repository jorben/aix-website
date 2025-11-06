---
date: '2025-11-07T00:56:49+08:00'
draft: false
title: '通过进程ID查询进程所属容器名称'
authors:
  - name: Jorben
    link: https://github.com/jorben
    image: https://github.com/jorben.png
tags:
  - docker
---



这个脚本用于在Docker环境中，通过指定的进程ID (PID) 来查找该进程运行在哪个容器中。它会遍历所有正在运行的Docker容器，检查每个容器内是否包含指定的进程ID，如果找到，则输出该容器的ID和名称。

使用方法：
1. 将 `psid` 变量设置为要查询的进程PID（例如，通过 `ps` 命令获取）。
2. 运行脚本，它会输出包含该进程的容器ID和名称（名称去掉前缀斜杠）。

<!--more-->

```shell
#!/usr/bin/env bash

# 这里替换为要查询的进程的PID
psid=16063   

for i in $(docker container ls --format "{{.ID}}"); 
do 
    id_count=$(docker top $i | grep ${psid} | wc -l)
     
    if [[ ${id_count} -gt 0 ]]
      then
        echo -n "$i    "
        docker inspect -f '{{.Name}}' $i | tr -d "/"
    fi
done
```