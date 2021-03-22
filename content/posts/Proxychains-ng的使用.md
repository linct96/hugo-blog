---
title: "Proxychains-ng的使用"
date: 2021-03-22T19:30:24+08:00
summary: "一个能为任何应用使用代理的工具，支持http、socks5"
showToc: true
ShowBreadCrumbs: true
draft: false
cover:
  image: "proxy4chains.jpg" # static 文件夹下链接
  alt: "" # alt text
  caption: "<text>"
  relative: false
  hidden: false
---

## 介绍
在我们这片魔法大陆上，github、npm等网站经常会无法访问，而单独为某个应该设置代理又太繁琐，`proxychains`便应运而生。

## 安装
```bash
brew install proxychains-ng

# 借助代理安装
ALL_PROXY=socks5://127.0.0.1:port brew install proxychains-ng
```

## 修改配置
```bash
# 修改默认配置文件
vim /usr/local/etc/proxychains.conf
```
在最底部添加
```bash
# 通过 socks5 代理
socks5 127.0.0.1 port
```
> 也可将`socks5`替换为`http`走 http 代理的方式

## 关闭 sip
由于最新的`macos`系统不允许用户修改具有保护权限的文件夹。需要用户进入`recovery`模式 => 实用工具 => 终端 输入如下命令
```sh
# 关闭 sip
csrutil disable
# 开启 sip
csrutil enable
```

## 重命名`proxy4chains`
由于每次都需要输入`proxy4chains`显得有些多余，我们可以借助`zsh`重命名`proxy4chains`。

```bash
# 打开配置文件
vim ~/.zshrc
```
使用`proxy`替代`proxy4chains`:
```diff
+ alias proxy="proxy4chains"
```


