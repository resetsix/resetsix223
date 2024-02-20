---
title: mac启动终端环境变量不生效
cover: https://img.paulzzh.com/touhou/random?4
date: 2024-02-20 20:02:43
tags: 网站部署
coverWidth: 1500
coverHeight: 780
---

## 起因

- 在 macOS 上通过`brew install nvm`命令行安装 nvm，但是每次新启动终端都需要手动执行`source ~/.bashrc`命令才能执行 nvm。
- 在百般查询后修改了`.bashrc`文件，配置了以下内容

```bash
export NVM_DIR="$HOME/.nvm"
[ -s "/usr/local/opt/nvm/nvm.sh" ] && \. "/usr/local/opt/nvm/nvm.sh"
```
- 但是每次启动仍要手动执行`source ~/.bashrc`

## 解决
- 因为：默认终端是 shell 而不是 zsh。所以每次启动都没有读取正确的配置文件。
- 切换终端命令：`chsh -s /bin/zsh`
- 检查当前终端：`echo $SHELL`

搞定！