---
title: "Netlify 部署 Twikoo 评论系统"
description: "Program Hugo Twikoo"
date: 2025-06-21T17:34:05+08:00
lastmod: 2025-06-21T17:34:05+08:00
categories: ["程序"]
collections: ["Hugo 博客"]
---

<!--more-->

## 1. 准备 MongoDB 数据库

① **创建免费 MongoDB 集群**

注册并登录 [MongoDB Atlas](https://www.mongodb.com/cloud/atlas/register) ，点击 “+ Create” ，选择 “Free” ，“ Name” 填写如 `Twikoo` ，点击 “Create Deployment”。

弹出 “Connect to Twikoo” 界面，点击 “Add Your Current IP Address” ，输入 `0.0.0.0/0`，点击 “Add IP Address” ，修改 “Username” 如 `Aria` ，点击 “Copy” （粘贴到记事本备用）→ “Create Database User” → “Choose a connection method” ，选择  “Drives”。

② **获取数据库连接字符串**

在 “Connecting with MongoDB Driver” 页面，复制数据库连接字符串（`mongodb+srv://<用户名>:<密码>@cluster0.xxx.mongodb.net/?retryWrites=true&w=majority`），并将 `<密码>` 修改为上面复制的密码，粘贴到记事本备用，点击 “Done” 。

## 2. 在Netlify 部署 Twikoo 后端

① **创建 Twikoo 服务仓库**

打开 [twikoojs/twikoo-netlify](https://bgithub.xyz/twikoojs/twikoo-netlify) ，点击 `fork` 将仓库 fork 到自己的账号下。

② **配置 Netlify 部署**

登录 [Netlify](https://app.netlify.com) ，点击 “ Add new project” → “Import an existing project” → “GitHub” ，连接 GitHub 账户，选择前面 fork 的 twikoo-netlify 仓库。

进入 “Configure project and deploy” 页面，修改以下内容：

- `Project name`：填写如 `<项目名称>-twikoo` 。
- `Add environment variables`：选择 “Add key/value pairs”，“Key” 填写 `MONGODB_URI` ，“Values” 填写前面记录的数据库连接字符串。
- 其余选项保持默认，点击 `Deploy <用户名>` 。

③ **获取服务地址**

部署完成后，在 Netlify 控制台，点击 “Projects” → “Project configuration” ，会项目地址，如 `<projectname>.netlify.app` 。

## 3. Hugo 站点集成 Twikoo

① **修改 Hugo 配置**

打开 `config/_default/hugo.toml` 文件，修改以下内容：

```toml
    [params.page.comment]
      enable = true
      [params.page.comment.twikoo]
        enable = true
        envId = "https://<projectname>.netlify.app/.netlify/functions/twikoo"
        region = ""
        path = ""
        visitor = true
        commentCount = true
        lightgallery = true
        katex = true
```

> **云函数地址**（`envId`）：包含 `https://` 前缀和 `/.netlify/functions/twikoo` 后缀，如 `https://<projectname>.netlify.app/.netlify/functions/twikoo`）。

完成后，推送至 GitHub 远程仓库。

② **验证与测试**

在项目根目录打开 Git Bash 终端，输入以下命令：

```bash
hugo server -e production           # 生产模式（支持评论 / CDN）
```



## 参考内容

1. [Twikoo 文档 - Netlify 部署](https://twikoo.js.org/backend.html#netlify-%E9%83%A8%E7%BD%B2)
