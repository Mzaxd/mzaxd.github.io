---
title: Git设置代理(v2rayN)
categories:
  - 工具技巧
tags:
  - Git
  - V2ray
---

## 为什么设置代理？

在使用Git操作远程库（Github）的时候偶尔会失败，通常都是网络的问题~~（众所周知的原因）~~，通过使用代理可以有效避免这个问题

## 查看代理本地监听的端口号

1. 打开v2rayN的管理面板
2. 点击`设置`，选择`参数设置`
3. 在弹出的`参数设置`页面找到下图中的`本地监听端口`和`协议`
4. 根据你的端口号和协议进行对应设置

![image-20230318143459628](https://blog-1310221847.cos.ap-beijing.myqcloud.com/202303181434674.png)

## 设置Http代理

```bash
# http协议，1081端口修改成自己的本地代理端口
git config --global http.proxy http://127.0.0.1:1081
git config --global https.proxy https://127.0.0.1:1081
```

## 设置socks代理

```bash
# socks5协议，1080端口修改成自己的本地代理端口
git config --global http.proxy socks5://127.0.0.1:1080
git config --global https.proxy socks5://127.0.0.1:1080
```

## 只给Github加代理

上面的代理配置是让所有Git命令都走代理，但是如果你使用国内的Gitee或者自建的GitLab，那么使用代理只会让访问变慢。

```bash
# socks5协议，1080端口修改成自己的本地代理端口
git config --global http.https://github.com.proxy socks5://127.0.0.1:1080
git config --global https.https://github.com.proxy socks5://127.0.0.1:1080

# http协议，1081端口修改成自己的本地代理端口
git config --global http.https://github.com.proxy http://127.0.0.1:1081
git config --global https.https://github.com.proxy http://127.0.0.1:1081
```

## 取消代理设置

```bash
git conifg --global --unset http.proxy
git conifg --global --unset https.proxy
```
