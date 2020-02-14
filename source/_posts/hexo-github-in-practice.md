---
title: Hexo + GitHub Pages踩坑之旅
date: 2020-02-15 02:20:43
tags:
---

## 〇、Node.js安装之坑

操作系统是Ubuntu 19.10。一开始我通过[NodeSource](https://github.com/nodesource/distributions)安装了Node.js，执行`npm install -g hexo-cli`之后提示权限不足：
```
npm WARN checkPermissions Missing write access to /usr/lib/node_modules
npm ERR! code EACCES
npm ERR! syscall access
npm ERR! path /usr/lib/node_modules
npm ERR! errno -13
npm ERR! Error: EACCES: permission denied, access '/usr/lib/node_modules'
npm ERR!  [Error: EACCES: permission denied, access '/usr/lib/node_modules'] {
npm ERR!   stack: "Error: EACCES: permission denied, access '/usr/lib/node_modules'",
npm ERR!   errno: -13,
npm ERR!   code: 'EACCES',
npm ERR!   syscall: 'access',
npm ERR!   path: '/usr/lib/node_modules'
npm ERR! }
npm ERR! 
npm ERR! The operation was rejected by your operating system.
npm ERR! It is likely you do not have the permissions to access this file as the current user
npm ERR! 
npm ERR! If you believe this might be a permissions issue, please double-check the
npm ERR! permissions of the file and its containing directories, or try running
npm ERR! the command again as root/Administrator.
```

`/usr/lib/node_modules`目录没有写权限，这也不奇怪；Hexo的[文档](https://hexo.io/docs/)**强烈不建议**用`sudo`或是root用户权限解决问题，给出的[方案](https://docs.npmjs.com/resolving-eacces-permissions-errors-when-installing-packages-globally)是用版本管理软件（Node version manager）安装Node.js。我选的是[nvm](https://github.com/nvm-sh/nvm)：

```
# nvm的安装脚本，本文最新版本为0.35.2
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.35.2/install.sh | bash

# 安装成功会输出"nvm"，否则提示"nvm: command not found"
# 这里"which nvm"命令无效，因为"nvm.sh"是个shell脚本，而不是可执行二进制文件
command -v nvm

# 本文写作时的最新Node LTS版本为12.16.0，如需安装最新版执行"nvm install node"即可
nvm install 12.16.0
```

这样Node.js的安装位置是`~/.nvm/versions/node/v12.16.0/`，成功避免了`EACCES`权限问题。

> npm下载依赖包很慢，建议配置国内镜像。可以安装[nrm](https://www.npmjs.com/package/nrm)，`nrm use taobao`切换到淘宝NPM镜像。感谢@[夜雨随风](https://juejin.im/post/5b91e8455188255c451e893f)

## 一、GitHub Pages之坑

我在GitHub上创建了名为`jiyingcao.github.io`的Repository，通过[https://jiyingcao.github.io](https://jiyingcao.github.io) 访问博客。需要把源代码，也就是MarkDown等文件等也都保存到这个Repository。