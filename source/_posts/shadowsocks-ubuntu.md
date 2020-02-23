---
title: Ubuntu使用Shadowsocks科学上网
date: 2019-06-07 14:28:31
tags:
- Linux
- 环境配置
- 科学上网
---

# 准备

我用的Shadowsocks是购买的[Just My Socks](https://justmysocks.net/)，日常用基本称得上稳定快速。老生常谈了，如果你对科学上网有刚需，老老实实付费，在网上找免费的基本是浪费时间。

Ubuntu版本是[19.04 Desktop (64-bit)](http://releases.ubuntu.com/19.04/ubuntu-19.04-desktop-amd64.iso.torrent)，虚拟机安装。如果作为主力操作系统，请安装[LTS版本](https://wiki.ubuntu.com/BionicBeaver/ReleaseNotes)。

# 安装Shadowsocks

安装很简单：
```
pip install shadowsocks
```

如果提示```pip```命令找不到，先安装```python-pip```（我使用的是Python 2.7）：
```
sudo apt install python-pip
pip install shadowsocks
```

# 配置Shadowsocks

安装完成后可以通过```sslocal```命令启动Shadowsocks了。不过我们需要先将Shadowsocks服务器地址、端口、加密方式、密码等信息填写到配置文件里。现在```/etc/shadowsocks```目录下应该有```config.json.example```文件了：

{% asset_img 13318826-4d3791f5962c21c9.png /etc/shadowsocks %}

复制并重命名文件：
```
sudo cp /etc/shadowsocks/config.json.example /etc/shadowsocks/config.json
```

编辑```config.json```文件：
```
sudo gedit /etc/shadowsocks/config.json
```

{% asset_img 13318826-4d3a6b541658b6c8.png config.json %}

修改以下几行：
```
    "server": "你的server地址",
    "server_port": 你的server端口,
    "password": "你的密码",
    "local_address": "127.0.0.1",
    "local_port": 1080,
    "method": "你的server指定的加密方法，通常是aes-256-cfb"
```

我的机器上还需要删除```"libopenssl":"C:\\Program Files\\Git\\mingw64\\bin\\libeay32.dll",```一行，毕竟不是Windows系统，很好理解吧。修改完成后保存，退出文本编辑器（我这里是```gedit```）。

# 启动Shadowsocks

```
sslocal -c /etc/shadowsocks/config.json
```

{% asset_img 13318826-124c7ba20509ff85.png Terminal - sslocal %}

# 检验成果

只差一步了。设置浏览器代理，类型SOCKS v5，SOCKS主机127.0.0.1，端口1080：

{% asset_img 13318826-f8c0384d8580daa2.png Firefox - 连接设置 %}

这时候应该就可以翻qiang了。Enjoy！

{% asset_img 13318826-827664dc88040838.png Firefox - Google主页 %}

# 参考
[Ubuntu安装和使用shadowsocks](https://zhoujianshi.github.io/articles/2018/Ubuntu%E5%AE%89%E8%A3%85%E5%92%8C%E4%BD%BF%E7%94%A8shadowsocks/index.html)
[Linux安装配置Shadowsocks客户端及开机自动启动](https://blog.huihut.com/2017/08/25/LinuxInstallConfigShadowsocksClient/)
