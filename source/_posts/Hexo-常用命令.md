---
title: Hexo 常用命令
date: 2026-05-29 21:48:52
tags: [Hexo, 教程]
categories: 技术
---

# Hexo 常用命令速查

## 初始化

```bash
hexo init [folder]          # 初始化 Hexo 项目
npm install                 # 安装依赖
```

## 创建新文章

```bash
hexo new "文章标题"         # 创建新文章
hexo new page "页面标题"    # 创建新页面
hexo new draft "草稿标题"   # 创建草稿
```

## 生成静态文件

```bash
hexo generate              # 生成静态文件
hexo g                     # 简写
hexo generate --watch      # 监听文件变动自动生成
hexo g -w                  # 简写
```

## 本地预览

```bash
hexo server                # 启动本地服务器，默认端口 4000
hexo s                     # 简写
hexo server -p 5000        # 指定端口
hexo server -i 0.0.0.0     # 指定 IP
```

## 部署

```bash
hexo deploy                # 部署到远程服务器
hexo d                     # 简写
hexo generate --deploy     # 先生成再部署
hexo g -d                  # 简写
hexo deploy --generate     # 先部署再生成（不常用）
```

## 清理

```bash
hexo clean                 # 清理缓存文件 (db.json) 和生成的静态文件 (public)
```

## 其他常用命令

```bash
hexo list                  # 列出网站信息
hexo list post             # 列出所有文章
hexo list page             # 列出所有页面
hexo list tag              # 列出所有标签
hexo list category         # 列出所有分类
hexo version               # 查看 Hexo 版本
```

## 组合命令（最常用）

```bash
hexo clean && hexo g && hexo d    # 完整的发布流程：清理 → 生成 → 部署
```

## 推荐工作流

1. 创建文章：`hexo new "文章标题"`
2. 编辑文章：编辑 `source/_posts/` 下的 Markdown 文件
3. 本地预览：`hexo s`，在浏览器打开 http://localhost:4000 查看效果
4. 发布上线：`hexo clean && hexo g -d`

记住这些命令，Hexo 博客管理就变得非常简单了！
