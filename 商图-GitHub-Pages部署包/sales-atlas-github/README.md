# 商图 · 全球客户洞察

黑底与极光绿主题，支持中英文国家 / 城市搜索、地图定位、北京时间与客户时间对照、经济数据和美元 / 欧元报价换算。已移除“集成商跟进要点”。

## 在 GitHub Pages 发布（无需安装开发软件）

1. 登录 GitHub，创建仓库，例如 `sales-atlas`。免费个人账号使用 Public 仓库即可启用 Pages。Pages 网页通常公开可访问，与原 Sites 私有网页的访问范围不同。
2. 解压部署包。将本目录里的文件上传到仓库根目录，确保 `index.html` 就在根目录，不要多套一层 `sales-atlas-github` 文件夹。
3. 在仓库打开 **Settings → Pages**。
4. **Source** 选择 **Deploy from a branch**；分支选择上传文件的分支（通常为 `main`），文件夹选择 **/(root)**，点击 **Save**。
5. 等待发布完成，Pages 设置页面会显示实际网址，通常为 `https://你的用户名.github.io/sales-atlas/`。以 GitHub 显示的链接为准。

官方说明：https://docs.github.com/en/pages/getting-started-with-github-pages/configuring-a-publishing-source-for-your-github-pages-site

本项目是纯静态网页，不需要 API 密钥、Node.js、数据库、npm install 或构建命令。资源使用相对路径，支持 GitHub Pages 的仓库子路径。

## 使用与限制

- 默认世界地图和地图组件保存在项目中，不依赖远程瓦片，因此不会遇到此前本地 HTML 请求地图瓦片的 403 问题。
- 通过 HTTPS 网址访问时可勾选在线街道图；服务出错会恢复内置世界概览。国家边界和小岛细节不是精细地图。
- 国家搜索、经济快照及货币映射保存在项目中。城市搜索与汇率需要联网；外部服务不可用时页面会提示。
- 国家概览不代表客户具体时区，选择城市后才能计算当地时间。联系窗口按客户当地周一至周五 09:00–18:00 与北京时间 09:00–20:00 的交集估算，未计节假日及客户实际作息。
- 经济数据使用 2026-09-15 获取的世界银行最新非空年度快照，不会自动更新。各指标的统计年份不同，页面单独显示。
- 查询词会发送给 Open-Meteo；货币对查询发送给 Frankfurter。本项目不记录或上传客户名单，也不带登录系统。

## 主要文件

- `index.html`、`app.js`、`style.css`、`aurora.css`：页面、交互和样式。
- `world.json`：内置世界地图。
- `countries.json`、`economics.json`、`currencies.json`：国家、经济和货币数据。
- `leaflet.js`、`leaflet.css`、`opencc.js`：本地地图组件和中文简繁体转换。
- `.nojekyll`：让 GitHub Pages 直接发布静态文件。

## 数据与第三方资源

- 世界概览：Natural Earth，公共领域。https://www.naturalearthdata.com/about/terms-of-use/
- 国家信息：mledoze/countries，ODbL 1.0；完整许可见 `countries-LICENSE.txt`。https://github.com/mledoze/countries
- 城市搜索与坐标：Open-Meteo / GeoNames。https://open-meteo.com/en/docs/geocoding-api
- 经济指标：世界银行。https://data.worldbank.org/
- 汇率：Frankfurter。https://frankfurter.dev/
- 货币映射：Unicode CLDR。https://github.com/unicode-org/cldr-json
- 地图组件：Leaflet 1.9.4，BSD-2-Clause；见 `leaflet-LICENSE.txt`。
- 简繁体转换：OpenCC JS 1.0.5。https://github.com/nk2028/opencc-js
- 可选在线街道图：OpenStreetMap。https://www.openstreetmap.org/copyright

更换或再分发第三方资源时请保留各自许可和署名。
