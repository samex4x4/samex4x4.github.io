---
title: Docker 技術入門與實戰 01
date: 2019-04-08 23:56:30
tags:
    - docker
---

在[Umedy](https://www.udemy.com/docker-china/learn/v4/overview) 買了這門課程

<!--more-->

## 概念
過往的VM技術需要Hypervisor
Type 1 -> 連底層的os都去掉，直接在物理機上安裝Hypervisor
(ex VMware)
Type 2 -> 在OS上安裝Hypervisor 再加上VM
(ex VirtualBox,  VM workstation)

Containers直接運行在os上 共享bin/libs

Docker基於Linux Kernel下的技術
![Docker 架構](https://i.imgur.com/Y1QJUNQ.png)

Cgroups:
做資源管理；在一台機器上運行多個Container CPU Memory 如何分配

Namespaces:
做隔離的

Docker machine:
> 可以在虛擬機上安裝Docker使用，以前是給Mac.Windows電腦實踐Docker使用的
> 參照[官網](https://docs.docker.com/machine/overview/)說明;現在更推薦直接使用Docker
> Machine was the only way to run Docker on Mac or Windows previous to Docker v1.12. Starting with the beta program and Docker v1.12, Docker Desktop for Mac and Docker Desktop for Windows are available as native apps and the better choice for this use case on newer desktops and laptops. We encourage you to try out these new apps.

Play with Docker:
線上使用Docker

https://labs.play-with-docker.com/


## 語法

### 從Docker Hub垃曲別人build好的image
docker pull ubuntu 默認downlowd 最新版
docker pull ubuntu:16.04 下載1604版 可以依據他的tag使用

### 看image資料
docker images <- 列出images
docker image rm image ID
docker image rm image name

### 如何build出自己的image
#### https://github.com/xiaopeng163/docker-k8s-lab

docker build -t samex4x4/python-flask-demo:1.0 .  <-加tag, .代表docker file 的位置

### 怎麽推送到遠程的docker hub
docker push --help

### 之後以新版命令為主
docker image ls
docker image pull