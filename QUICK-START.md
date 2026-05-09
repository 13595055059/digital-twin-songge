# 松哥数字分身 - 3分钟部署指南

## 🚀 最简单方案：Vercel拖拽部署（推荐）

### 你需要准备的
- 一个 OpenAI API 密钥（从 https://platform.openai.com 获取）
  - 或其他兼容API（如DeepSeek、通义千问等）

---

### 第一步：注册Vercel（1分钟）
1. 打开 https://vercel.com
2. 点击 "Sign Up"
3. 用 GitHub 账号登录（推荐）或邮箱注册

### 第二步：创建项目（1分钟）
1. 登录后，点击右上角 **"Add New"** → **"Project"**
2. 找到 **"Import Git Repository"** 下方的 **"Continue with a template"**
3. 或者更简单：点击左下角 **"..."** → 选择 **"Create from CLI"**

> **更简单的方法**：
> 1. 把 `digital-twin-deploy` 文件夹上传到你的 GitHub 仓库
> 2. 在 Vercel 中点击 "Import" 这个仓库
> 3. 点击 "Deploy"

### 第三步：配置API密钥（30秒）
1. 部署完成后，进入项目 → **Settings** → **Environment Variables**
2. 添加：
   - Name: `OPENAI_API_KEY`
   - Value: `你的OpenAI API密钥`
3. 点击 Save
4. 回到 Deployments 页面，点击最新部署旁的 **"..."** → **Redeploy**

### 第四步：添加到手机桌面
1. 用手机浏览器（Safari/Chrome）打开 Vercel 给你的网址
2. **iOS**: 点击分享按钮 → "添加到主屏幕"
3. **Android**: 点击菜单 → "添加到主屏幕"

---

## 🔑 如果你没有OpenAI API

### 方案A：使用DeepSeek（便宜，中文好）
1. 注册 https://platform.deepseek.com
2. 获取API Key
3. 在应用设置中配置：
   - API地址: `https://api.deepseek.com/v1`
   - API密钥: `你的DeepSeek密钥`
   - 模型: `deepseek-chat`

### 方案B：使用其他兼容API
任何兼容OpenAI格式的API都可以用，只需在应用设置中修改API地址和密钥。

---

## 📁 文件说明

```
digital-twin-deploy/
├── api/
│   └── chat.js          ← 后端AI接口
├── public/
│   ├── index.html        ← 前端应用（核心文件）
│   ├── manifest.json     ← PWA配置
│   ├── icon-192.png      ← 应用图标
│   └── icon-512.png      ← 应用图标（高清）
├── package.json          ← 项目配置
├── vercel.json           ← Vercel路由配置
└── DEPLOY-GUIDE.md       ← 详细部署指南
```

---

*部署遇到问题随时来找我！*
