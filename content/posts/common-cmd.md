---
title: "Common Cmd"
date: 2021-03-19T10:48:36+08:00
draft: false
summary: "记录一些不常用又会用到的命令"
categories:
  - 杂项
---

记录一些不常用又会用到的命令

## GIT

```bash
# 查看git用户信息
$ git config user.name
$ git config user.email

# 设置git用户信息
$ git config --global user.name "zhangsan"
$ git config --global user.email "zhangsan@email.com"

# 设置 git 代理(socks5 和 http 两种方式)
$ git config --global http.proxy 'socks5://127.0.0.1:port' 
$ git config --global http.proxy 'http://127.0.0.1:port'

# 取消 git 代理
$ git config --global --unset http.proxy

```



## NPM

```bash
# 登录npm
$ npm login

# 查看npm用户信息
$ npm whoami

# 查看已安装的package
$ npm list (-g) --depth=0

```


