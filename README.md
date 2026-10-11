# 铁记 IronLog — iOS 健身记录 Web App

一个不依赖服务器数据库的力量与有氧记录 App。可在 iPhone Safari 中添加到主屏幕，已打开过的页面可离线使用。

## 功能
- 常见胸、背、肩、二头、三头、腿、核心、全身训练动作库，按肌群/器械筛选、搜索、创建自定义动作。
- 每组独立记录：总重量 kg / 左右手 kg / 自重；次数；日期；可一键复用上一组。
- 有氧：跑步机爬坡、跑步、快走、椭圆机、单车、划船机、登阶机等。跑步机支持坡度百分比，支持速度 km/h 或配速 min/km（分:秒格式），时长、估算距离。
- 历史日志：按月筛选、回顾每组、删除或修改日期后继续记录。
- 统计：7 天 / 30 天 / 90 天 / 全部时间；训练天数、力量训练量趋势、肌群分布、最高记录、有氧时长/距离。
- 数据本地存储，支持 JSON 备份、JSON 合并恢复、CSV 导出。

## 安装到 iPhone

### 推荐：用 GitHub Pages 免费发布
1. 新建 GitHub 公开仓库 `ironlog`。
2. 将 `ironlog-ios` 文件夹内**所有文件**上传到仓库根目录（`index.html` 必须在根目录）。
3. 仓库 **Settings → Pages → Build and deployment → Deploy from a branch → main / (root) → Save**。
4. 打开 GitHub Pages 提供的 HTTPS 链接（通常是 `https://用户名.github.io/ironlog/`）。
5. 在 iPhone 的 Safari 打开链接，点分享 → 添加到主屏幕，即可得到独立的图标和全屏使用界面。

也可以用 Netlify Drop 等静态网站部署工具上传整个文件夹。静态托管不需要后端。

### 本地预览
可在有 Python 的电脑上进入文件夹，运行 `python -m http.server 8080`，浏览器访问 `http://localhost:8080`。注意 iPhone 访问电脑 IP 的 HTTP 地址不能完整体验 PWA 安装能力，正式安装请使用 HTTPS。

## 数据注意事项
- 数据默认保存于当前浏览器的 `localStorage`，**不是云同步**。
- 主屏幕 App 和 Safari 页面可能采用独立存储；固定使用一个入口记录。更换设备、删除主屏幕 App 或清除网站数据前，先从“我的 → 导出完整备份”导出 JSON 文件。
- CSV 适合使用 Excel / Numbers 查看，不支持直接导入；只有 JSON 备份可以恢复。
- 力量训练量＝各组重量×次数。左右手模式为（左手 + 右手）×每侧次数。自重项目不计入负重总量；最高记录中的左右手动作显示单侧最高重量。
- 速度/配速换算关系：配速秒/公里＝3600÷速度 km/h。有氧距离为平均速度 × 时长的估算值。

## 文件
- `index.html` 主要界面和全部本地业务逻辑
- `manifest.webmanifest` 安装名称和图标
- `sw.js` 离线缓存
- `icon-*.png`、`apple-touch-icon.png` App 图标

无需 npm、数据库或外部网络 API。
