# 部署说明：docs-site

## 一句话
用 docsify 把 Markdown 变成带侧边栏和搜索的静态文档站，托管在 GitHub Pages。

## 前置条件
- GitHub 账号，仓库必须 Public（Pages 免费版只支持公开仓库）
- 本地能 git push（SSH key 已配好）

## 启动命令
无需启动，Pages 由 GitHub 托管。

本地预览：
python -m http.server 8000
访问 http://localhost:8000

## 验证方法（看到什么算成功）
- 打开 https://tsyg1001.github.io/docs-site/ 返回 200
- 左侧出现「首页 / Git 笔记 / 嵌入式」三项
- 右侧渲染出 README 内容，中文不乱码

## 端口与访问地址
- 线上：https://tsyg1001.github.io/docs-site/
- 本地预览：http://localhost:8000

## 数据存在哪（卷名/路径）
无数据库。内容就是仓库里的 .md 文件，GitHub 上有完整副本。

## 如何升级
改 md 文件，然后：
git add -A
git commit -m "docs: xxx"
git push

Pages 自动重建，等 1~2 分钟生效。

## 如何彻底卸载
仓库 Settings → Pages → 关闭 Pages；
或直接删除整个仓库。

## 踩过的坑
1. .nojekyll 必须有，否则 Jekyll 会忽略 _sidebar.md 这类下划线开头的文件，侧边栏失效。
2. 项目站点（/docs-site/）下用 basePath 容易解析错，md 直接放根目录最省事。
3. GitHub Pages 静态资源缓存 10 分钟，404 也会被缓存；改完先 Ctrl+Shift+R 或开无痕窗口。
4. 文件名大小写：Pages 跑在 Linux 上区分大小写，本地 Windows 不区分，容易本地正常线上 404。