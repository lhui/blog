---
title: "加速远程ssh连接"
date: 2022-03-06T12:33:58+08:00
url: accelerate-remote-ssh.html
---

由于很多问题，连接远程的其他国家的服务器主机，总是会遇到各种各样的问题，比如vuter 端口无法ping 通，ssh延迟高，等等问题，导致使用国外主机很是头疼，毕竟国外的主机便宜，而且价位低，技术卓越，谁不喜欢这样的主机呢。
本片文章主要的内容就是如何加速连接国外的主机，先说明解决思路，通过中间机器来转发ssh 请求，现在还是最初的版本，只是简单的记录下其中的命令和思路，至于最好的方式，还在探索之中。

首先是连接跳板机的简易方式 复制 ssh-key 到跳板机

```bash
ssh-copy-id -i ~/.ssh/id_rsa.pub -p {remote-ssh-port} {remote-user}@{remote-ip}
```
会提示数据密码 输入远程服务器的密码即可

以后连接远程的服务器只需要
```bash
ssh {remote-user}@{remote-ip} -p {remote-ssh-port}
```
即可 无须再输入密码

{{can it be simple ??}} yes 为服务器设置别名

我们继续

这一步骤将我们的本地机器连接到了跳板机

我们可以采用同样的方式，将跳板机连接到远程的机器。


