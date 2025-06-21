---
title: "Hugo+Netlify 博客极速迁移"
description: "GitHub Pages 10分钟迁移：1. 删除 GitHub Actions 脚本 2. 配置 Netlify 自动构建 3. 开启全球 CDN 加速"
date: 2025-06-21T04:10:05+08:00
lastmod: 2025-06-21T04:10:05+08:00
categories: ["程序"]
collections: ["Hugo 博客"]
---

<!--more-->

[GitHub Pages](https://docs.github.com/zh/pages/getting-started-with-github-pages) 作为静态站点基础托管方案，其国内访问速度受限于无 CDN 优化，且需依赖 [GitHub Actions](https://docs.github.com/zh/actions) 脚本实现自动化部署，维护成本较高。[Netlify](https://docs.netlify.com/) 提供更优解决方案：

1. **访问加速**：全球 200+ CDN 节点（含香港/新加坡），实测国内加载速度提升 3 倍。
2. **流程简化**：原生支持 Hugo 构建，替代 Actions 脚本。
3. **功能扩展**：无缝集成评论/表单等动态功能。

![操作流程](pic0-1.png)

## 1. 迁移准备

### 1.1 本地仓库

删除 `.github` 文件夹（建议备份到别的目录，包含 `hugo.yaml` 文件）。

打开 `config/_default/hugo.toml` 文件，修改 `baseURL` 参数。

```toml
baseURL = "https://<用户名>.netlify.app/"
```

完成后，将本地仓库推送至 GitHub 仓库。

### 1.2 GitHub 仓库

登录 GitHub 仓库，进入 “Settings” → “Pages” 页面，点击 “Visit site” 旁边的 `···` ，选择 “ Unpublish site ” 。

此操作将立即停用 GitHub Pages 服务，但保留本地历史部署记录。确认后，原访问地址（`http://<usename>.github.io`）将返回 404 状态。

## 2. 配置 Netlify

### 2.1 仓库连接设置

打开 [Netlify](https://app.netlify.com/)，选择 “ Log in with GitHub ” → “ Sign in ” → “Authorize netlify”。

点击 “Project” → “Import from Git” ，选择 “GitHub” → “Authorize netlify” ，在仓库列表选择你的 Hugo 项目仓库。

进入 “Configure project and deploy” 页面，修改以下内容：

① `Project name` ：填写上面 `baseURL` 参数的 `<用户名>` 。若显示被占用，则换另一个，同步修改 `baseURL` 参数，并再次从本地推送修改至 GitHub 仓库。

② `Build command` ：修改为 `hugo --gc --minify` 。

③ `Add environment variables`：“Key” 填写 `HUGO_VERSION` ，“Values” 填写本地环境配置的 Hugo 版本号（本地执行 `hugo version` 命令可获取），如 `0.147.8` 。

④ 其余选项保持默认，点击 `Deploy <用户名>` 。

### 2.2 完成部署并访问

在屏幕底部，等待部署完成，完后点击部署日志条目。

![Published](pic2-1.png)

点击 “Open production deploy” 按钮查看现场站点。

![Open production deploy](pic2-2.png)

## 参考内容

1. [Netlify Docs](https://docs.netlify.com/)
