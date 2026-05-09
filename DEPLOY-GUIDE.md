# 松哥数字分身 - 部署指南

## 📦 部署包内容

```
digital-twin-deploy/
├── api/
│   └── chat.js          # 后端AI接口（Vercel Serverless Function）
├── public/
│   ├── index.html        # 前端应用（完整单文件）
│   ├── manifest.json     # PWA配置（添加到桌面）
│   ├── icon-192.png      # 应用图标
│   └── icon-512.png      # 应用图标（高清）
├── package.json          # 项目配置
├── vercel.json           # Vercel部署配置
└── DEPLOY-GUIDE.md       # 本文件
```

---

## 🚀 方案A：Vercel部署（推荐，免费）

### 前提条件
- 一个 GitHub 账号
- 一个 OpenAI API 密钥（或其他兼容API密钥）

### 步骤

#### 1. 上传代码到GitHub
```bash
# 初始化Git仓库
cd digital-twin-deploy
git init
git add .
git commit -m "松哥数字分身 v1.0"

# 创建GitHub仓库后
git remote add origin https://github.com/你的用户名/digital-twin-songge.git
git push -u origin main
```

#### 2. 一键部署到Vercel
1. 访问 [vercel.com](https://vercel.com)
2. 用GitHub账号登录
3. 点击 "New Project"
4. 选择刚上传的仓库
5. 点击 "Deploy"
6. 等待部署完成（约1分钟）

#### 3. 配置API密钥
1. 在Vercel项目页面，点击 "Settings"
2. 找到 "Environment Variables"
3. 添加环境变量：
   - `OPENAI_API_KEY` = `你的OpenAI API密钥`
   - （可选）`OPENAI_API_BASE` = `自定义API地址`（如使用国内代理）
   - （可选）`AI_MODEL` = `gpt-4o`（默认值，可改为其他模型）
4. 点击 "Save"
5. 重新部署（Deployments → 点击最新部署 → Redeploy）

#### 4. 访问应用
部署完成后，Vercel会给你一个网址，例如：
`https://digital-twin-songge.vercel.app`

#### 5. 添加到手机桌面
- **iOS**：用Safari打开 → 点击分享按钮 → "添加到主屏幕"
- **Android**：用Chrome打开 → 点击菜单 → "添加到主屏幕"

---

## 🚀 方案B：Netlify部署（免费）

### 步骤
1. 访问 [netlify.com](https://netlify.com)
2. 用GitHub账号登录
3. 将 `digital-twin-deploy` 文件夹拖拽到Netlify
4. 配置环境变量（同Vercel）
5. 部署完成

> 注意：Netlify的Serverless Functions配置略有不同，如需后端API，推荐使用Vercel。

---

## 🚀 方案C：本地服务器部署

### 前提条件
- Python 3.8+
- OpenAI API密钥

### 步骤

#### 1. 纯前端模式（最简单）
```bash
cd digital-twin-deploy/public
python3 -m http.server 8080
```
然后在浏览器打开 `http://localhost:8080`

在设置页面输入API密钥即可使用。

> 手机访问：确保手机和电脑在同一WiFi，访问 `http://你电脑的IP:8080`

#### 2. Node.js服务器模式
```bash
cd digital-twin-deploy
npm install
npx vercel dev
```
访问 `http://localhost:3000`

---

## 🔧 高级配置

### 使用Claude API
如果你更想用Claude（推荐，理解力更强）：
1. 使用OpenAI兼容的Claude转发服务
2. 在设置中配置：
   - API地址：你的转发服务地址
   - API密钥：你的Claude密钥
   - 模型：`claude-3.5-sonnet`

### 使用国内代理
如果OpenAI API无法直接访问：
1. 配置API代理地址（如：`https://your-proxy.com/v1`）
2. 在设置中填写代理地址
3. 使用国内可访问的模型

---

## 🔒 安全说明

- API密钥存储在浏览器localStorage中，**不会上传到任何服务器**
- 如果使用Vercel部署后端API，密钥存储在Vercel环境变量中
- 建议设置API使用限额，避免意外超额

---

## 📱 添加到手机桌面后的效果

- ✅ 全屏显示，类似原生APP
- ✅ 有自己的图标
- ✅ 没有浏览器地址栏
- ✅ 支持对话、档案查看、盲点检测
- ✅ 数据保存在本地浏览器中

---

## 🐛 常见问题

### Q: 对话没有AI回复？
A: 检查API密钥是否正确配置。可以在设置页面查看和修改。

### Q: 手机上无法添加到桌面？
A: 确保使用Safari（iOS）或Chrome（Android）打开，不要用微信内置浏览器。

### Q: 部署后API调用失败？
A: 检查Vercel环境变量是否正确设置，确认重新部署。

### Q: 如何更新系统？
A: 修改GitHub代码后，Vercel会自动重新部署。

---

*松哥数字分身 v1.0 | 2025*
