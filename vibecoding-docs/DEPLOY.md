# 公开部署说明

当前你看到的 `http://127.0.0.1:8124/` 只是本机预览地址，不能直接被互联网访问。

现在这个项目已经补齐成“可直接发布到公网静态托管平台”的版本，适合部署到：

- Vercel
- Netlify
- GitHub Pages

## 已包含内容

- `vercel.json`：Vercel 部署配置
- `netlify.toml`：Netlify 部署配置
- `.nojekyll`：GitHub Pages 静态站点兼容文件
- `robots.txt`：搜索引擎抓取规则
- `sitemap.xml`：站点地图模板
- `manifest.webmanifest`：PWA 配置
- `sw.js`：离线缓存

## 发布前需要改的地方

1. 把 `sitemap.xml` 里的 `https://your-domain.example/` 改成你自己的正式域名
2. 如果你有社交分享封面图，可以把 `index.html` 里的 `og:image` 改成公开可访问的图片地址
3. 如果你要绑定自定义域名，在托管平台里配置即可

## 最快发布方式

### Vercel

1. 把当前文件夹上传到 GitHub 仓库
2. 登录 Vercel 并导入这个仓库
3. 不需要额外构建命令，直接发布
4. 发布后会得到一个公网 `https://xxx.vercel.app` 链接

### Netlify

1. 把当前文件夹上传到 GitHub 仓库，或者直接拖拽整个项目文件夹到 Netlify
2. 发布目录保持默认根目录 `.`
3. 发布后会得到一个公网 `https://xxx.netlify.app` 链接

### GitHub Pages

1. 把当前文件夹上传到 GitHub 仓库
2. 打开仓库 `Settings` -> `Pages`
3. 在 `Build and deployment` 里选择从主分支发布
4. 发布后会得到一个公网 `https://<你的用户名>.github.io/<仓库名>/` 链接

## 为什么现在还不是公网链接

因为当前会话只能给你本地可预览版本，不能替你登录外部平台并直接代发到你的公网账号下。

也就是说：

- 网页本身已经可以公网部署
- 但真正的公网网址，需要你把这些文件放到一个静态托管平台上

## 数据说明

当前版本的数据默认保存在用户自己的浏览器 `localStorage` 中：

- 优点：部署简单，不需要后端
- 限制：换浏览器或换设备后数据不会自动同步

## 如果你想做成真正的公网产品

我后面还可以继续帮你接：

- 登录系统
- 云端数据库
- 多设备同步
- 用户独立数据隔离
