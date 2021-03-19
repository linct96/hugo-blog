---
title: "Iterm2 Zsh"
date: 2021-03-19T10:50:13+08:00
draft: false
summary: "个性化自己的命令行工具"
# disableHLJS: true # to disable highlightjs
categories:
  - 杂项
---

## 安装brew

```bash
ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
```

```bash
# brew源
git -C "$(brew --repo)" remote set-url origin url
# 官方源 https://github.com/Homebrew/brew.git
# 清华源 https://mirrors.tuna.tsinghua.edu.cn/git/homebrew/brew.git

# brew-core源
git -C "$(brew --repo homebrew/core)" remote set-url origin url
# 官方源 https://github.com/Homebrew/homebrew-core.git
# 清华源 https://mirrors.tuna.tsinghua.edu.cn/git/homebrew/homebrew-core.git

# brew-cask源
git -C "$(brew --repo homebrew/cask)" remote set-url origin url
# 官方源 https://github.com/Homebrew/homebrew-cask.git
# 清华源 https://mirrors.tuna.tsinghua.edu.cn/git/homebrew/homebrew-cask.git
```

```bash
# 添加socks代理
ALL_PROXY=socks5://127.0.0.1:port brew update
```
> 安装时可以加上 --verbose查看安装详情

## 安装iterm2

```bash
brew cask install iTerm2

# 查看已安装终端
cat /etc/shells

# 使用zsh终端
chsh -s /bin/zsh

# 使用默认bash终端
chsh -s /bin/bash

```

## 安装oh-my-zsh

```bash
sh -c "$(curl -fsSL https://raw.githubusercontent.com/robbyrussell/oh-my-zsh/master/tools/install.sh)"
```

## 安装python

```bash
brew install python
pip3 install powerline-status  //python3使用pip3
```

## 安装字体

[Meslo LG M Regular for Powerline](https://github.com/powerline/fonts/blob/master/Meslo%20Slashed/Meslo%20LG%20M%20Regular%20for%20Powerline.ttf)


## 配置主题

agnoster已内置，无需下载
```bash
vi ~/.zshrc
# 将ZSH_THEME后面的字段改为agnoster
```

## 语法高亮

```bash
brew install zsh-syntax-highlighting

# .zshrc文件插入两段文字
source /usr/local/share/zsh-syntax-highlighting/zsh-syntax-highlighting.zsh
plugins=(
  git
  zsh-syntax-highlighting
)
```

