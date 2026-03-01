# Google Analytics 设置指南

本指南将帮助您为湖南省医保政策和法规文件网站设置Google Analytics，以便统计网站访问数据。

## 什么是Google Analytics？

Google Analytics（谷歌分析）是一个免费的网站分析工具，可以帮助您：

- 📊 **追踪访问量** - 了解每天有多少人访问您的网站
- 🌍 **分析访问来源** - 了解访问者从哪里来（搜索引擎、社交媒体、直接访问等）
- 👥 **了解访问者** - 了解访问者的地理位置、设备类型、浏览器等
- ⏱️ **分析用户行为** - 了解访问者在网站上停留了多久、浏览了哪些页面
- 📈 **优化网站** - 根据数据分析结果优化网站内容和用户体验

## 前提条件

1. **拥有Google账号**
   - 如果没有，请先注册：https://accounts.google.com/

2. **网站已部署到GitHub Pages**
   - 确认网站已成功部署
   - 当前访问地址：https://redboy333999.github.io/hunan-medical-insurance-policies/

## 设置步骤

### 步骤1：创建Google Analytics账号

1. 访问Google Analytics：
   ```
   https://analytics.google.com/
   ```

2. 点击 **"开始测量"**（Start measuring）按钮

3. **创建账号：**
   - **账号名称：** 输入 `湖南省医保政策网站` 或您喜欢的名称
   - **账号数据共享设置：** 根据您的需求选择（建议保持默认）
   - 点击 **"下一步"**

4. **设置媒体资源：**
   - **媒体资源名称：** 输入 `湖南省医保政策和法规文件汇编`
   - **报告时区：** 选择 `中国 - 北京时间 (GMT+08:00)`
   - **货币：** 选择 `人民币 (CNY ¥)`
   - 点击 **"下一步"**

5. **关于您的业务：**
   - **行业类别：** 选择 `政府` 或 `其他`
   - **企业规模：** 根据实际情况选择
   - **您打算如何使用Google Analytics：** 根据需求选择
   - 点击 **"创建"**

6. **接受服务条款：**
   - 选择您的国家/地区：`中国`
   - 阅读并同意服务条款
   - 点击 **"我接受"**

### 步骤2：设置数据流

1. **选择平台：**
   - 选择 **"网站"**

2. **设置数据流：**
   - **网站网址：** 输入 `https://redboy333999.github.io/hunan-medical-insurance-policies/`
   - **数据流名称：** 输入 `湖南省医保政策网站`
   - **增强型衡量功能：** 建议开启（可以收集更多数据）
   - 点击 **"创建数据流"**

3. **获取衡量ID：**
   - 创建成功后，您会看到一个衡量ID（Measurement ID）
   - 格式类似：`G-XXXXXXXXXX`
   - **请记录这个ID，后面会用到！**

### 步骤3：将Google Analytics代码添加到网站

#### 方法A：手动添加（推荐用于GitHub Pages）

1. **打开您的 `download.html` 文件**

2. **找到 `<head>` 标签**

3. **在 `<head>` 标签内添加以下代码：**

   ```html
   <!-- Google Analytics -->
   <script async src="https://www.googletagmanager.com/gtag/js?id=G-XXXXXXXXXX"></script>
   <script>
     window.dataLayer = window.dataLayer || [];
     function gtag(){dataLayer.push(arguments);}
     gtag('js', new Date());
     gtag('config', 'G-XXXXXXXXXX');
   </script>
   ```

   **重要：** 将 `G-XXXXXXXXXX` 替换为您在步骤2中获得的实际衡量ID！

4. **保存文件**

#### 方法B：使用GitHub Actions自动添加（高级）

1. 在仓库根目录创建 `.github/workflows/analytics.yml` 文件
2. 添加以下内容：

   ```yaml
   name: Add Google Analytics

   on:
     push:
       branches: [ main ]

   jobs:
     add-analytics:
       runs-on: ubuntu-latest
       steps:
         - uses: actions/checkout@v2
         - name: Add Google Analytics
           run: |
             sed -i 's/G-XXXXXXXXXX/G-您的实际ID/g' download.html
         - name: Commit changes
           run: |
             git config --local user.email "action@github.com"
             git config --local user.name "GitHub Action"
             git add download.html
             git commit -m "Add Google Analytics"
             git push
   ```

### 步骤4：验证Google Analytics设置

1. **访问您的网站：**
   ```
   https://redboy333999.github.io/hunan-medical-insurance-policies/download.html
   ```

2. **检查Google Analytics：**
   - 访问 https://analytics.google.com/
   - 进入您的账号
   - 点击左侧菜单的 **"报告"**（Reports）
   - 点击 **"实时"**（Realtime）
   - 如果您刚才访问了网站，应该能看到至少1个活跃用户

3. **等待数据更新：**
   - Google Analytics通常需要24-48小时才能显示完整数据
   - 实时数据会立即显示

## 查看分析数据

### 主要报告

#### 1. 实时报告（Realtime）
- **位置：** 报告 → 实时
- **用途：** 查看当前有多少人正在访问网站
- **数据：** 活跃用户数、页面浏览量、地理位置等

#### 2. 用户获取报告（Acquisition）
- **位置：** 报告 → 用户获取
- **用途：** 了解访问者从哪里来
- **数据：**
  - 流量来源（搜索引擎、社交媒体、直接访问等）
  - 流量渠道（自然搜索、付费广告、社交媒体等）
  - 引荐网站（哪些网站链接到您的网站）

#### 3. 受众报告（Audience）
- **位置：** 报告 → 用户
- **用途：** 了解访问者的特征
- **数据：**
  - 地理位置（国家、城市）
  - 设备类型（桌面、移动、平板）
  - 浏览器和操作系统
  - 语言偏好
  - 新用户与回访用户比例

#### 4. 行为报告（Behavior）
- **位置：** 报告 → 互动
- **用途：** 了解访问者在网站上的行为
- **数据：**
  - 页面浏览量
  - 平均会话时长
  - 跳出率
  - 热门页面
  - 用户路径

### 自定义报告

您可以根据需求创建自定义报告：

1. 点击左侧菜单的 **"自定义"**（Customization）
2. 点击 **"创建自定义报告"**
3. 选择要显示的指标和维度
4. 保存报告

## 高级功能

### 1. 设置目标（Goals）

目标可以帮助您追踪特定的用户行为，例如：

- 文件下载次数
- 页面停留时间
- 特定页面访问次数

**设置步骤：**

1. 访问 https://analytics.google.com/
2. 点击左下角的 **"管理"**（Admin）
3. 在 **"视图"** 列中点击 **"目标"**（Goals）
4. 点击 **"+ 新目标"**
5. 选择目标类型：
   - **目标：** 下载文件
   - **类型：** 事件
   - **类别：** 下载
   - **操作：** 点击
   - **标签：** 文件名
6. 保存目标

### 2. 设置事件追踪

事件追踪可以追踪用户与网站元素的交互，例如：

- 按钮点击
- 文件下载
- 表单提交
- 视频播放

**实现方法：**

在 `download.html` 中添加事件追踪代码：

```html
<a href="湖南省医保政策和法规文件汇编.docx"
   class="download-btn"
   download
   onclick="gtag('event', 'download', {
     'event_category': '文件下载',
     'event_label': 'Word文档'
   })">
  📥 下载Word文档
</a>
```

### 3. 设置自定义维度

自定义维度可以收集额外的数据，例如：

- 文件类型
- 下载时间
- 用户角色

**设置步骤：**

1. 访问 https://analytics.google.com/
2. 点击左下角的 **"管理"**（Admin）
3. 在 **"媒体资源"** 列中点击 **"自定义定义"** → **"自定义维度"**
4. 点击 **"+ 创建自定义维度"**
5. 填写名称和范围
6. 保存

### 4. 设置受众群体

受众群体可以帮助您分析特定用户群体的行为。

**设置步骤：**

1. 访问 https://analytics.google.com/
2. 点击左下角的 **"管理"**（Admin）
3. 在 **"媒体资源"** 列中点击 **"受众群体"** → **"受众群体"**
4. 点击 **"+ 新受众群体"**
5. 定义受众群体条件
6. 保存

## 数据隐私和合规

### GDPR合规

如果您有来自欧盟的访问者，需要确保符合GDPR要求：

1. **添加Cookie同意横幅**
2. **提供隐私政策**
3. **允许用户选择退出追踪**

### 添加Cookie同意横幅

在 `download.html` 中添加：

```html
<div id="cookie-banner" style="position: fixed; bottom: 0; left: 0; right: 0; background: #333; color: white; padding: 20px; text-align: center; display: none;">
  <p>我们使用Google Analytics来改善网站体验。继续使用即表示您同意我们的隐私政策。</p>
  <button onclick="acceptCookies()" style="background: #667eea; color: white; border: none; padding: 10px 20px; border-radius: 5px; cursor: pointer;">同意</button>
</div>

<script>
  function acceptCookies() {
    document.getElementById('cookie-banner').style.display = 'none';
    localStorage.setItem('cookiesAccepted', 'true');
  }

  window.onload = function() {
    if (!localStorage.getItem('cookiesAccepted')) {
      document.getElementById('cookie-banner').style.display = 'block';
    }
  }
</script>
```

## 常见问题

### Q1: 为什么看不到数据？

**A:** 可能的原因：

1. **时间太短**
   - Google Analytics需要24-48小时才能显示完整数据
   - 实时数据会立即显示

2. **代码未正确添加**
   - 检查 `<head>` 标签中是否正确添加了代码
   - 检查衡量ID是否正确

3. **浏览器插件拦截**
   - 某些浏览器插件会拦截Google Analytics
   - 尝试使用无痕/隐私模式访问

4. **网站未部署**
   - 确认网站已成功部署到GitHub Pages

### Q2: 如何排除自己的访问？

**A:** 使用过滤器排除自己的IP地址：

1. 访问 https://analytics.google.com/
2. 点击左下角的 **"管理"**（Admin）
3. 在 **"视图"** 列中点击 **"过滤器"**（Filters）
4. 点击 **"+ 添加过滤器"**
5. 填写：
   - **过滤器名称：** 排除我的IP
   - **过滤器类型：** 排除
   - **选择来源或目的地：** 来自IP地址的流量
   - **选择表达式：** 等于
   - **IP地址：** 输入您的IP地址
6. 保存

**如何获取您的IP地址：**
- 访问 https://www.whatismyip.com/

### Q3: 如何追踪文件下载？

**A:** 使用事件追踪：

```html
<a href="湖南省医保政策和法规文件汇编.docx"
   class="download-btn"
   download
   onclick="gtag('event', 'download', {
     'event_category': '文件下载',
     'event_label': 'Word文档'
   })">
  📥 下载Word文档
</a>
```

### Q4: 数据不准确怎么办？

**A:** 可能的原因和解决方法：

1. **检查过滤器设置**
   - 确认没有意外排除流量

2. **检查代码实现**
   - 确认所有页面都添加了追踪代码

3. **检查数据采样**
   - 对于高流量网站，Google Analytics可能会采样数据

4. **联系Google支持**
   - 如果问题持续，联系Google Analytics支持

### Q5: 如何导出数据？

**A:** 导出数据的方法：

1. **在报告中导出**
   - 打开任意报告
   - 点击右上角的 **"导出"** 按钮
   - 选择格式（PDF、Excel、Google Sheets等）

2. **使用API导出**
   - 使用Google Analytics Reporting API
   - 适合自动化导出

3. **使用第三方工具**
   - Google Data Studio
   - Supermetrics
   - 其他数据分析工具

## 最佳实践

### 1. 定期查看数据

建议每周或每月查看一次数据，了解网站表现。

### 2. 设置告警

设置自定义告警，当访问量异常时收到通知。

### 3. 优化网站内容

根据数据分析结果，优化网站内容和用户体验。

### 4. 保护用户隐私

遵守数据隐私法规，保护用户隐私。

## 资源链接

- **Google Analytics文档：** https://support.google.com/analytics/
- **Google Analytics Academy：** https://analytics.google.com/analytics/academy/
- **Google Analytics社区：** https://support.google.com/analytics/community
- **Google Developers：** https://developers.google.com/analytics

## 总结

设置Google Analytics后，您可以：

✅ **了解网站访问量**
✅ **分析访问者来源**
✅ **优化网站内容**
✅ **提升用户体验**
✅ **做出数据驱动的决策**

祝您使用愉快！