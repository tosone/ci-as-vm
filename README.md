# CI as VM

白嫖 GitHub Actions 上的主机，搞事情。

## 内网穿透

利用 [frp](https://github.com/fatedier/frp) 将 vm 从 GitHub Actions 内代理出来。

比如现有一个主机含有公网 IP `192.168.1.1`，在主机上启动 `frps -c frps.ini`，配置文件在当前目录的 frps.ini 内。

## 流水线

GitHub Actions 中的 frpc 会连接当前目录的 frpc.ini 内设置的地址，并在拥有公网主机上暴露出 9001 的端口。

## 连接

最后只需在本机上使用命令 `ssh -p 9001 runner@192.168.1.1`，然后输入在 GitHub Action secrets 中设置的密码就可以连上了。
