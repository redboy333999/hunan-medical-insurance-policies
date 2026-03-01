# GitHub Pages 部署指南

## 步骤1：创建GitHub仓库

1. 访问 https://github.com/new
2. 登录您的GitHub账号（如果没有账号，请先注册）
3. 填写仓库信息：
   - **Repository name（仓库名称）：** `hunan-medical-insurance-policies`
   - **Description（描述）：** 湖南省医保政策和法规文件汇编
   - **Public/Private（公开/私有）：** 选择 **Public**（公开）
   - **不要勾选** "Add a README file"
4. 点击 **"Create repository"** 按钮

## 步骤2：推送代码到GitHub

创建仓库后，GitHub会显示推送命令。在您的本地终端中执行以下命令：

```bash
git remote add origin https://github.com/[您的GitHub用户名]/hunan-medical-insurance-policies.git
git branch -M main
git push -u origin main
```

**注意：** 将 `[您的GitHub用户名]` 替换为您实际的GitHub用户名。

## 步骤3：启用GitHub Pages

1. 在GitHub仓库页面，点击 **Settings**（设置）
2. 在左侧菜单中找到 **Pages** 选项
3. 在 **Build and deployment** 部分：
   - **Source（源）：** 选择 **Deploy from a branch**
   - **Branch（分支）：** 选择 **main** 分支
   - **Folder（文件夹）：** 选择 **/(root)**
4. 点击 **Save**（保存）按钮

## 步骤4：等待部署完成

1. GitHub会自动部署您的网站（通常需要1-2分钟）
2. 部署完成后，您会在Pages设置页面看到访问链接
3. 访问链接格式为：`https://[您的GitHub用户名].github.io/hunan-medical-insurance-policies/`

## 步骤5：访问下载页面

部署完成后，您可以通过以下链接访问下载页面：

```
https://[您的GitHub用户名].github.io/hunan-medical-insurance-policies/download.html
```

## 可选：使用自定义域名

如果您想使用自己的域名，可以在GitHub Pages设置中：

1. 在Pages设置页面，找到 **Custom domain** 部分
2. 输入您的域名（如：`medical-insurance.yourdomain.com`）
3. 按照提示配置DNS记录
4. 等待DNS生效

## 常见问题

### Q1: 推送时提示认证失败怎么办？
**A:** 使用个人访问令牌（Personal Access Token）：
1. 访问 https://github.com/settings/tokens
2. 点击 **Generate new token** → **Generate new token (classic)**
3. 选择 `repo` 权限
4. 生成后复制token
5. 推送时使用：`https://[token]@github.com/[用户名]/[仓库名].git`

### Q2: 如何更新文件？
**A:** 执行以下命令：
```bash
git add .
git commit -m "更新描述"
git push
```

### Q3: 如何删除仓库？
**A:** 在仓库页面点击 **Settings** → 滚动到最底部 → 点击 **Delete this repository**

## 文件说明

- `download.html` - 下载页面（GitHub Pages默认显示此页面）
- `湖南省医保政策和法规文件汇编.md` - Markdown格式的政策汇编
- `湖南省医保政策和法规文件汇编.docx` - Word格式的政策汇编
- `精神疾病类医保定点医疗机构整改报告.docx` - 精神疾病医保整改报告模板
- `README.md` - 项目说明文档

## 优势

✅ **免费托管** - GitHub Pages完全免费
✅ **HTTPS支持** - 自动配置SSL证书
✅ **全球CDN** - GitHub提供全球CDN加速
✅ **版本控制** - Git版本管理，随时回滚
✅ **易于更新** - 推送代码即可更新网站
✅ **随时随地访问** - 只要有网络就能访问

## 下一步

完成部署后，您就可以：
1. 随时随地访问下载页面
2. 分享链接给其他人
3. 持续更新政策文件
4. 建立专业的政策文档网站

如有问题，请参考 [GitHub Pages官方文档](https://docs.github.com/en/pages)。