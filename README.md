# 智慧茶园霜冻实时监测平台 · 前端演示版

这是一个用于 GitHub Pages 在线作品展示的**纯静态前端 Demo**。原项目中运行在 `127.0.0.1:5000` 的 Flask + MySQL 后端已被移除，所有数据均在浏览器本地模拟生成，不会发起任何后端请求。

## 页面结构

| 文件 | 说明 |
| --- | --- |
| `index.html` | 登录 / 注册入口（由原 `login.html` 复制而来） |
| `system2.html` | 工作台主框架，包含左侧菜单与 iframe 内容区 |
| `home.html` | 数据概览：茶园欢迎语、实时温度、湿度、霜冻风险指数 |
| `dashboard.html` | 实时监控大屏：微气候地图、风险仪表盘、综合趋势、12h 预报、告警列表 |
| `history.html` | 历史告警：筛选、分析图表、详情弹窗、CSV 导出 |
| `ai.html` | AI 农事助手：本地知识库模拟问答、打字机效果、茶苗动画 |
| `images/` | 演示截图资源 |

## 本地预览

推荐在项目目录启动一个静态服务器：

```bash
cd github_pages_demo
python -m http.server 8000
```

然后访问 `http://127.0.0.1:8000/`。

也可以直接双击 `index.html` 打开；如果浏览器对本地 iframe 有安全限制，使用上面的静态服务器即可。

## 演示说明

- **登录**：输入任意非空账号和密码，点击“登录智慧茶园”即可进入 `system2.html`。
- **注册**：注册流程完全在本地完成，成功后会自动回填账号密码，不会写入任何服务器。
- **演示数据**：风险指数固定为 `45/100`，温度、湿度、告警和图表均为本地 Mock 数据；仪表盘每 10 秒模拟刷新，数字与曲线会有可见波动。
- **AI 助手**：发送问题后会先显示思考气泡，再以打字机效果输出本地预设的防霜建议。
- **导出**：历史告警页的“导出数据”使用 SheetJS 在浏览器本地生成 CSV。

## 部署到 GitHub Pages

1. 在 GitHub 新建一个仓库（例如 `tea-garden-demo`）。
2. 将 **`github_pages_demo` 文件夹里的全部内容**上传到仓库根目录，确保 `index.html` 位于根目录，而不是多套一层文件夹。
3. 打开仓库的 **Settings → Pages**，在 **Build and deployment** 中选择 **Deploy from a branch**，分支选 `main`，目录选 `/ (root)`，点击 **Save**。
4. 等待几十秒，访问：
   `https://<你的用户名>.github.io/<仓库名>/`

> 不需要上传 `app.py`、数据库文件或原项目其他目录；本文件夹已经是完整的静态站点。

如果你习惯使用命令行，也可以在 GitHub 建好空仓库后执行：

```bash
cd D:/tea_project/github_pages_demo
git init
git add .
git commit -m "feat: tea garden frost monitoring static demo"
git branch -M main
git remote add origin https://github.com/<你的用户名>/<仓库名>.git
git push -u origin main
```

推送完成后，再按上面的步骤在 Settings → Pages 中选择 `main` 分支根目录发布。

## 兼容性说明

- 图表依赖 ECharts CDN，图标依赖 FontAwesome CDN，表格导出依赖 SheetJS CDN，首次打开需要联网。
- 所有页面共用浏览器 `localStorage` 中的 `tea_user` 登录状态；换设备或清理浏览器数据后重新“登录”即可。
- 建议使用最新版 Chrome / Edge / Firefox 浏览，演示大屏在 1440×900 桌面分辨率下效果最佳，也适配移动端。

—— 用于毕业设计作品展示的静态演示版本
