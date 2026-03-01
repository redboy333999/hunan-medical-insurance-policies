# GitHub Personal Access Token 创建指南

## 步骤1：创建Personal Access Token

1. 访问 https://github.com/settings/tokens
2. 点击 **Generate new token** → **Generate new token (classic)**
3. 填写token信息：
   - **Note（备注）：** Hunan Medical Insurance Policies Deployment
   - **Expiration（过期时间）：** 选择 **No expiration**（永不过期）或 **90 days**
4. 选择权限（勾选）：
   - ✅ **repo**（完整的仓库访问权限）
5. 点击页面底部的 **Generate token** 按钮
6. **重要：** 复制生成的token（只显示一次，请妥善保存）

## 步骤2：使用Token推送代码

创建token后，在终端执行以下命令：

```bash
git remote set-url origin https://[您的Token]@github.com/redboy333999/hunan-medical-insurance-policies.git
git push -u origin main
```

**注意：** 将 `[您的Token]` 替换为您刚才复制的实际token。

## 步骤3：验证推送成功

推送成功后，您会看到类似以下输出：

```
Enumerating objects: 20, done.
Counting objects: 100% (20/20), done.
Delta compression using up to 8 threads
Compressing objects: 100% (18/18), done.
Writing objects: 100% (20/20), 2.50 MiB | 2.50 MiB/s, done.
Total 20 (delta 2), reused 0 (delta 0), pack-reused 0
To https://github.com/redboy333999/hunan-medical-insurance-policies.git
 * [new branch]      main -> main
```

## 步骤4：启用GitHub Pages

推送成功后：

1. 访问 https://github.com/redboy333999/hunan-medical-insurance-policies
2. 点击 **Settings**（设置）
3. 在左侧菜单点击 **Pages**
4. 在 **Build and deployment** 部分：
   - **Source** 选择：**Deploy from a branch**
   - **Branch** 选择：**main**
   - **Folder** 选择：**/(root)**
5. 点击 **Save**（保存）

## 步骤5：等待部署完成

1. GitHub会自动部署（通常需要1-2分钟）
2. 部署完成后，在Pages页面会显示访问链接
3. 访问地址：https://redboy333999.github.io/hunan-medical-insurance-policies/download.html

## Token安全提示

⚠️ **重要安全提醒：**
- Token只显示一次，请立即复制并妥善保存
- 不要将token分享给他人
- 定期更换token以提高安全性
- 如果token泄露，立即在GitHub设置中删除

## 常见问题

### Q1: Token推送时提示认证失败？
**A:** 检查以下几点：
- Token是否正确复制（不要有多余空格）
- Token是否已过期
- 是否选择了正确的权限（repo）

### Q2: 如何查看已创建的token？
**A:** 访问 https://github.com/settings/tokens，可以看到所有已创建的token

### Q3: 如何删除token？
**A:** 在token列表中，点击token右侧的 **Delete** 按钮

### Q4: 推送后如何更新文件？
**A:** 执行以下命令：
```bash
git add .
git commit -m "更新描述"
git push
```

## 下一步

完成推送和GitHub Pages设置后，您就可以：
1. 随时随地访问：https://redboy333999.github.io/hunan-medical-insurance-policies/download.html
2. 分享链接给其他人
3. 持续更新政策文件
4. 建立专业的政策文档网站

需要帮助？请参考 [GitHub官方文档](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/creating-a-personal-access-token)。