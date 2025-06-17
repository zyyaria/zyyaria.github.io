# Hugo + FixIt 自动化博客

> **基于 Windows 的极简静态博客系统**  
> 用 Markdown 写作 → GitHub 自动发布 → 零成本托管

---

## 🚀 核心功能

1、**写作**：本地用 `hugo new posts/title/index.md` 创建文章。

2、**美化**：FixIt 主题提供响应式布局/暗黑模式/多语言。

3、**发布**：推送到 GitHub 自动构建并上线。

## 🛠️ 部署流程

1、**安装工具**：Hugo Extended、Git、VSCode。

2、**创建博客**：

```bash
hugo new site blog
cd blog
git init
git submodule add https://github.com/hugo-fixit/FixIt.git themes/FixIt
echo "theme = 'FixIt'" >> hugo.toml
echo "defaultContentLanguage = 'zh-cn'" >> hugo.toml
```

3、**配置自动化**：在 `./.github/workflows/` 创建 hugo.yaml。
