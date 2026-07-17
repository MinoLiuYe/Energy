# 把这个页面发布到 GitHub Pages（让别人看到、每天自动更新）

只需**一次性设置**，之后每天 07:00 定时任务会自动重新生成并推送，别人打开链接就是最新的。

## 三步设置

### ① 建一个 GitHub 仓库
1. 登录 https://github.com （没有账号先免费注册）。
2. 右上角 **+ → New repository**。
3. 仓库名随意，例如 `storage-dashboard`；**选 Public（公开）**（免费版 Pages 需要公开仓库）；
   **不要**勾选 "Add a README"（保持空仓库）。→ Create repository。

> ⚠️ 公开仓库意味着页面内容（含「覆盖标的」你的持仓清单和投资逻辑）在 GitHub 上也公开可见、可被搜索。
> 你选了「包含全部」，确认接受再继续；想收窄可回来让我把覆盖标的从导出页去掉。

### ② 连接远程 + 首次推送
打开「终端」，粘贴执行（把 `<用户名>` 和 `<仓库名>` 换成你的）：

```bash
cd /Users/minoliusfolder/Documents/Claude/energy-storage-platform/publish
git remote add origin https://github.com/<用户名>/<仓库名>.git
git push -u origin main
```

首次 push 会要求登录：
- **Username**：你的 GitHub 用户名。
- **Password**：**不是**账号密码，而是 **Personal Access Token（个人令牌）**。
  生成：GitHub → 右上头像 → Settings → Developer settings → Personal access tokens →
  Tokens (classic) → Generate new token，勾选 **repo** 权限，生成后复制粘贴当密码。
- macOS 会把令牌存进钥匙串，**以后定时任务自动推送不再需要手输**。

### ③ 打开 Pages
1. 进你的仓库 → **Settings** → 左侧 **Pages**。
2. **Source** 选 "Deploy from a branch"；**Branch** 选 `main` / `/ (root)` → **Save**。
3. 等 1–2 分钟，页面上方会显示网址：
   **https://<用户名>.github.io/<仓库名>/** —— 这就是发给别人的链接。

## 完成后

- 每天 07:00，本地定时任务采集→更新数据→重新生成静态页→`git push`，GitHub 一分钟内刷新。
- 想手动立刻更新一次：
  ```bash
  bash /Users/minoliusfolder/Documents/Claude/energy-storage-platform/scripts/publish_static.sh
  ```
- 页面是**只读快照**：别人看得到数据，但采集/刷新/问答等操作只在你本地平台可用。
- 问答助手需要本地 AI，快照页不提供（会显示说明）。
