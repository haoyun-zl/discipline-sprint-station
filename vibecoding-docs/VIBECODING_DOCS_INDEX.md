# Vibecoding 文档总览

这份文档用于汇总当前项目里和 `vibecoding` 交付、部署、发布相关的核心资料，方便统一上传到 GitHub。

## 建议一起上传的文档

- `README.md`
  项目总说明，包含产品定位、功能结构、技术栈、公开地址、使用方式与扩展方向。

- `DEPLOY.md`
  静态站点公开部署说明，包含 GitHub Pages、Vercel、Netlify 的发布方式。

- `GITHUB_PAGES_FINAL_DEPLOY.md`
  最终发布说明，重点记录这次修正后的最终上线版本，包括图片角色、自动保存、缓存更新与正式地址。

- `CLOUD_SYNC_SETUP.md`
  云同步配置说明，适用于后续接入 Supabase、多设备同步和账号体系。

## 当前最终版重点

- 游戏角色已经切换为图片版角色，不再使用旧的编程 SVG 角色
- 页面已改为免登录自动保存模式
- PWA 缓存版本已更新，角色图片已加入缓存清单
- `sitemap.xml` 已指向正式公开地址

## 上传到 GitHub 时建议一起保留的项目文件

除了文档，建议同时上传这些运行相关文件：

- `index.html`
- `styles.css`
- `script.js`
- `sw.js`
- `cloud-config.js`
- `manifest.webmanifest`
- `.nojekyll`
- `robots.txt`
- `sitemap.xml`
- `assets/characters/tree.png`
- `assets/characters/cat.png`
- `assets/characters/turtle.png`

## 当前公开地址

`https://haoyun-zl.github.io/discipline-sprint-station/`

## 当前仓库地址

`https://github.com/haoyun-zl/discipline-sprint-station`

## 建议上传方式

1. 先把这份文档包上传到仓库根目录或 `docs/` 目录
2. 再上传项目运行文件与资源文件
3. 提交到 `main` 分支
4. 等待 GitHub Pages 自动部署

## 如果线上还是旧角色

这通常是缓存问题，建议：

1. 强制刷新页面
2. 关闭旧标签页后重新打开
3. 如已安装 PWA，先删除旧版本再重新打开网页
