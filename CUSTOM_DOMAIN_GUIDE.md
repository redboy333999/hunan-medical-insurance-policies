# 自定义域名设置指南

本指南将帮助您为湖南省医保政策和法规文件网站设置自定义域名。

## 前提条件

1. **拥有自己的域名**
   - 如果还没有域名，可以从以下域名注册商购买：
     - 阿里云：https://wanwang.aliyun.com/
     - 腾讯云：https://dnspod.cloud.tencent.com/
     - Cloudflare：https://www.cloudflare.com/products/registrar/
     - GoDaddy：https://www.godaddy.com/

2. **GitHub Pages网站已部署**
   - 确认网站已成功部署到GitHub Pages
   - 当前访问地址：https://redboy333999.github.io/hunan-medical-insurance-policies/

## 设置步骤

### 步骤1：在GitHub Pages中添加自定义域名

1. 访问仓库的Pages设置页面：
   ```
   https://github.com/redboy333999/hunan-medical-insurance-policies/settings/pages
   ```

2. 在 **Custom domain** 部分：
   - 输入您的自定义域名，例如：
     - `medical-insurance.yourdomain.com`（子域名）
     - `www.yourdomain.com`（带www的域名）
     - `yourdomain.com`（根域名）

3. 点击 **Save** 按钮

4. 等待GitHub生成DNS记录（几秒钟）

### 步骤2：配置DNS记录

根据您的域名类型，选择相应的配置方法：

#### 方法A：使用子域名（推荐）

例如：`medical-insurance.yourdomain.com`

1. 登录您的域名管理面板（DNS服务商）
2. 找到DNS管理或DNS解析设置
3. 添加以下记录：

   **记录类型：** CNAME
   **主机记录：** medical-insurance
   **记录值：** redboy333999.github.io
   **TTL：** 600（或默认值）

4. 保存设置

#### 方法B：使用www子域名

例如：`www.yourdomain.com`

1. 登录您的域名管理面板
2. 添加以下记录：

   **记录类型：** CNAME
   **主机记录：** www
   **记录值：** redboy333999.github.io
   **TTL：** 600（或默认值）

3. 保存设置

#### 方法C：使用根域名（需要额外配置）

例如：`yourdomain.com`

1. 登录您的域名管理面板
2. 添加以下记录：

   **记录类型：** A
   **主机记录：** @
   **记录值：** 185.199.108.153
   **TTL：** 600（或默认值）

3. 保存设置

4. **重要：** 同时添加以下CNAME记录以支持www：

   **记录类型：** CNAME
   **主机记录：** www
   **记录值：** yourdomain.com
   **TTL：** 600（或默认值）

### 步骤3：启用HTTPS（推荐）

1. 回到GitHub Pages设置页面
2. 在 **Enforce HTTPS** 部分
3. 点击 **Enable** 按钮
4. 等待SSL证书生成（通常需要几分钟到几小时）

### 步骤4：验证域名设置

1. 等待DNS传播（通常需要5-30分钟，最长可能需要48小时）
2. 访问您的自定义域名：
   - 例如：https://medical-insurance.yourdomain.com
3. 检查网站是否正常显示
4. 检查浏览器地址栏是否显示安全锁图标（如果启用了HTTPS）

## 常见问题

### Q1: DNS传播需要多长时间？

**A:** 通常需要5-30分钟，但最长可能需要48小时。您可以使用以下工具检查DNS状态：
- https://dnschecker.org/
- https://www.whatsmydns.net/

### Q2: 如何检查DNS记录是否正确？

**A:** 使用以下命令检查DNS记录：

**Windows:**
```cmd
nslookup medical-insurance.yourdomain.com
```

**Mac/Linux:**
```bash
dig medical-insurance.yourdomain.com
```

或者使用在线工具：
- https://www.nslookup.io/

### Q3: 网站无法访问怎么办？

**A:** 请按以下步骤排查：

1. **检查DNS记录**
   - 确认DNS记录已正确添加
   - 等待DNS传播完成

2. **检查GitHub Pages设置**
   - 确认自定义域名已添加
   - 检查是否有错误提示

3. **清除浏览器缓存**
   - 使用Ctrl+F5强制刷新页面
   - 或使用无痕/隐私模式访问

4. **检查域名状态**
   - 确认域名已过期
   - 确认域名DNS服务器设置正确

### Q4: HTTPS证书生成失败怎么办？

**A:** 请按以下步骤排查：

1. **确认DNS记录正确**
   - CNAME记录必须指向 `redboy333999.github.io`

2. **等待DNS传播**
   - HTTPS证书生成需要DNS记录生效

3. **检查域名状态**
   - 确认域名未被标记为不安全

4. **联系GitHub支持**
   - 如果问题持续，联系GitHub支持团队

### Q5: 可以同时使用多个域名吗？

**A:** 可以！GitHub Pages支持多个自定义域名：

1. 在GitHub Pages设置中添加多个域名
2. 为每个域名配置相应的DNS记录
3. 选择一个主域名（通常选择不带www的域名）

## 高级配置

### 配置自动重定向

如果您希望 `yourdomain.com` 自动重定向到 `www.yourdomain.com`：

1. 在仓库根目录创建 `CNAME` 文件
2. 文件内容为：`www.yourdomain.com`
3. 提交并推送到GitHub

### 配置CDN加速

如果您使用Cloudflare，可以：

1. 在Cloudflare中添加您的域名
2. 将DNS服务器更改为Cloudflare提供的DNS服务器
3. 在Cloudflare中配置DNS记录
4. 启用CDN和HTTPS

### 配置邮件服务

如果您需要使用该域名的邮件服务：

1. 添加MX记录
2. 添加SPF记录
3. 添加DKIM记录

具体配置请参考您的邮件服务提供商的文档。

## 维护建议

### 定期检查

1. **每月检查一次**
   - 检查域名是否即将过期
   - 检查DNS记录是否正常
   - 检查HTTPS证书是否有效

2. **监控网站状态**
   - 使用Uptime监控工具
   - 设置告警通知
   - 定期检查网站访问速度

### 备份配置

1. **记录DNS配置**
   - 保存DNS记录的截图或文档
   - 记录所有配置参数

2. **备份网站文件**
   - 定期备份GitHub仓库
   - 保存重要文件的副本

## 联系支持

如果在设置过程中遇到问题：

- **GitHub支持：** https://support.github.com/
- **DNS服务商支持：** 联系您的域名注册商
- **社区支持：** https://github.com/community

## 示例配置

### 示例1：使用阿里云域名

1. 登录阿里云控制台
2. 进入域名管理
3. 点击域名进入DNS解析设置
4. 添加记录：

   **记录类型：** CNAME
   **主机记录：** medical-insurance
   **记录值：** redboy333999.github.io
   **TTL：** 600

5. 保存设置

### 示例2：使用腾讯云域名

1. 登录腾讯云控制台
2. 进入DNSPod
3. 添加记录：

   **主机记录：** medical-insurance
   **记录类型：** CNAME
   **线路类型：** 默认
   **记录值：** redboy333999.github.io
   **TTL：** 600

4. 保存设置

### 示例3：使用Cloudflare

1. 登录Cloudflare
2. 添加站点
3. 添加DNS记录：

   **Type：** CNAME
   **Name：** medical-insurance
   **Target：** redboy333999.github.io
   **Proxy status：** Proxied（橙色云朵）

4. 保存设置

## 总结

设置自定义域名后，您的网站将拥有：

✅ **更专业的形象**
✅ **更容易记忆的地址**
✅ **更好的品牌识别**
✅ **更高的可信度**

祝您设置顺利！