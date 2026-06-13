# 碳循环减脂记录器 PWA

这是一个纯前端静态 PWA。数据保存在当前浏览器的 `localStorage` 中，不需要后端服务器。

## 功能

- 输入体重、身高、基础代谢、运动消耗和 TDEE。
- 设置低碳日 / 高碳日的碳水、蛋白质、脂肪 g/kg。
- 自动计算营养目标、总热量、相对 TDEE 的缺口或盈余。
- 记录每日食物摄入，保存并查看历史日期记录。
- 导出食物明细 CSV 和每日汇总 CSV。
- 支持通过 HTTPS 部署后注册 Service Worker，并缓存必要资源用于离线打开。

## 本地测试

不要直接双击 `index.html` 测试 PWA。Service Worker 需要通过 `http://localhost` 或 HTTPS 访问。

在本文件夹中运行：

```bash
python -m http.server 8080
```

然后打开：

```text
http://localhost:8080/
```

在浏览器开发者工具中检查：

- Application / Manifest 能看到应用名称和图标。
- Application / Service Workers 显示 service worker 已注册。
- Application / Cache Storage 中能看到 `carb-cycle-pwa-v4`。
- 断网或开启离线模式后刷新，页面仍能打开。

## 部署到 GitHub Pages

推荐把本文件夹中的所有文件上传到一个 GitHub 仓库的根目录：

```text
index.html
manifest.webmanifest
service-worker.js
README.md
.nojekyll
icons/
```

操作步骤：

1. 登录 GitHub，新建一个仓库，例如 `carb-cycle-pwa`。
2. 把上面的文件和 `icons` 文件夹上传到仓库根目录。
3. 进入仓库的 `Settings`。
4. 打开 `Pages`。
5. `Source` 选择 `Deploy from a branch`。
6. `Branch` 选择 `main`，目录选择 `/root`，点击 `Save`。
7. 等待 GitHub Pages 构建完成。
8. 打开 GitHub 给出的 HTTPS 地址，例如：

```text
https://你的用户名.github.io/carb-cycle-pwa/
```

## 在 iPhone 上安装

1. 用 iPhone Safari 打开 GitHub Pages 的 HTTPS 地址。
2. 等页面完全加载一次。
3. 点击 Safari 底部或顶部的“分享”按钮。
4. 选择“添加到主屏幕”。
5. 名称可保留“碳循环”，点击“添加”。
6. 回到主屏幕后，从图标打开即可像 App 一样使用。

## 如果无法添加或离线失败

优先检查：

- 网址是否是 HTTPS。GitHub Pages 默认是 HTTPS。
- 是否使用 iPhone Safari 打开，而不是微信、Chrome 或内置浏览器。
- `index.html`、`manifest.webmanifest`、`service-worker.js` 是否在同一目录。
- `manifest.webmanifest` 是否能直接打开并显示 JSON。
- `icons/icon-180.png`、`icons/icon-192.png` 和 `icons/icon-512.png` 是否能直接打开。
- 是否等待 GitHub Pages 部署完成，通常需要几十秒到几分钟。
- iPhone 是否开启了“低数据模式”或内容拦截器，可以临时关闭后重试。
- 修改文件后如果旧缓存未更新，进入 Safari 设置清除该网站数据，再重新打开一次。
