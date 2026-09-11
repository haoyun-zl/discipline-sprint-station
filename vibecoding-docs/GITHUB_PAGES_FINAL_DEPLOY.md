## GitHub Pages 最终发布说明

当前工作目录里的版本已经是最终修正版，包含以下关键更新：

- 角色形象已替换为图片版最终角色
- 页面改为免登录自动保存
- PWA 缓存版本已更新，角色图片已加入缓存清单
- `sitemap.xml` 已改为正式公开地址

### 本次需要上传到仓库的关键文件

- `index.html`
- `styles.css`
- `script.js`
- `sw.js`
- `manifest.webmanifest`
- `.nojekyll`
- `robots.txt`
- `sitemap.xml`
- `assets/characters/tree.png`
- `assets/characters/cat.png`
- `assets/characters/turtle.png`

### 推荐发布方式

1. 打开 GitHub 仓库：`discipline-sprint-station`
2. 用当前最终文件覆盖仓库中的旧文件
3. 提交到 `main` 分支
4. 等待 GitHub Pages 自动重新部署
5. 打开公开地址确认新角色是否生效

### 如果线上仍显示旧角色

这通常是缓存导致的，不一定是代码没更新。处理方式：

1. 打开网页后强制刷新
2. 关闭旧标签页，重新打开
3. 如果已安装到主屏幕，先删除旧 PWA 再重新打开网页

### 当前正式地址

`https://haoyun-zl.github.io/discipline-sprint-station/`
