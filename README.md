# D-File 文件管理系统

一个基于 GitHub API 的简单文件管理系统，支持文件上传、下载、删除等基本操作。

> 本项目源自 [@dhjz/file](https://github.com/dhjz/file) 二次开发，感谢原作者的贡献。

## 主要特性

### 文件操作

- ✨ 支持多文件拖拽上传（优化版）
  - 智能并发控制（最多3个并发）
  - 自动失败重试（最多3次）
  - 详细的上传进度显示
  - 完整的上传结果统计
- 📁 支持文件夹创建和管理
- 🗑️ 支持文件删除
- 🔍 支持文件搜索
- 📱 完整的移动端适配

### 界面交互

- 💫 拖拽上传视觉反馈
  - 顶部固定提示条
  - 拖拽时的动态效果
  - 空文件夹大型提示区域
- 📊 文件上传状态展示
  - 实时进度显示
  - 成功/失败统计
  - 详细错误提示
- 🎯 支持列表/网格两种显示模式
- 🌈 美观的深色主题界面

### CDN加速

- 🚀 支持多个CDN源（建议优先选择自定义域名方案）

  > **重要提示：**
  > 1. 本站加速（即部署在 GitHub/CF Pages）必须配置自定义域名才能实现加速
  > 2. 如果您没有自己的域名，建议使用以下第三方加速源：

  - gitmirror: raw.gitmirror.com
  - jsdelivr: gcore.jsdelivr.net
  - jsdelivr1: cdn.jsdelivr.net
  - ghgo: ghgo.xyz
  - gh-proxy: gh-proxy.com
  - ghproxy: ghproxy.cc
  - cf-ghproxy: cf.ghproxy.cc
  - ghproxy.net: ghproxy.net
- 📊 自动延迟测试
  - 自动测试所有源延迟
  - 延迟<1000ms显示绿色
  - 失败源显示红色
- 🔄 一键切换加速源
  - 点击即可切换源
  - 当前选中源高亮显示
  - 横向排列更直观

## 部署方式

### 1. GitHub Pages 部署

1. Fork 本仓库到你的账户
2. 进入仓库设置 Settings -> Pages
3. Source 选择 `main` 分支，/(root) 目录
4. 保存后等待几分钟，即可通过 `https://{username}.github.io/{repo}` 访问
5. 自定义域名配置：
   - 在 Settings -> Pages -> Custom domain 中输入你的域名
   - 添加 DNS 记录：

     ```dns
     类型    主机记录    值
     CNAME   www     {username}.github.io
     ```

   - 等待 DNS 生效，GitHub 会自动配置 SSL 证书

### 2. Cloudflare Pages 部署（推荐）

1. 登录 [Cloudflare 控制台](https://dash.cloudflare.com)
2. 进入 Pages -> Create a project -> Connect to Git
3. 选择你 fork 的仓库，点击 Begin setup
4. 配置构建和部署选项：
   - Project name: 自定义项目名称
   - Production branch: main
   - Framework preset: None
   - Build command: 留空
   - Build output directory: /
5. 点击 Save and Deploy
6. 等待部署完成后，可通过 `https://你的项目名.pages.dev` 访问
7. 自定义域名配置：
   - 在 Cloudflare Pages 项目中点击 Custom domains
   - 点击 Set up a custom domain
   - 输入你的域名（例如：file.yourdomain.com）
   - 如果域名已托管在 Cloudflare，DNS 记录会自动添加
   - 如果域名未托管在 Cloudflare：

     ```dns
     类型    主机记录           值
     CNAME   file        你的项目名.pages.dev
     ```

   - Cloudflare 会自动配置 SSL 证书

> 注意：使用自定义域名可以：
>
> - 避免 GitHub Pages 的访问限制
> - 绕过 GitHub 的 CDN 限制
> - 获得更好的访问速度
> - 更专业的展示效果

#### Cloudflare Pages 的优势

- 🚀 全球节点加速
  - 200+ 数据中心分布
  - 智能路由优化
  - 自动压缩优化

- 🔒 企业级安全防护
  - 免费 SSL 证书
  - DDoS 防护
  - WAF 防火墙
  - Bot 攻击防护

- 💎 开发者友好
  - 自动构建部署
  - 回滚版本控制
  - 自定义域名支持
  - 详细的分析统计

- 🎯 稳定可靠
  - 99.99% 可用性
  - 自动故障转移
  - 全天候监控

- 💰 慷慨的免费额度
  - 每月 500K 请求
  - 无带宽限制
  - 无需信用卡
  - 无隐藏收费

## 使用方法

1. 配置
   - 设置GitHub仓库：点击"设置Repo"
   - 设置访问Token：点击"设置Token"

2. 文件上传
   - 方式一：直接将文件拖放到页面任意位置
   - 方式二：点击"上传文件"按钮选择文件

3. 文件管理
   - 点击文件夹名称进入下级目录
   - 点击"返回"回到上级目录
   - 点击"删除"可删除文件
   - 点击"分列"切换显示模式
   - 使用搜索框可快速查找文件

## 技术特性

- 🔒 安全的文件处理
  - 文件覆盖确认
  - 关键文件保护
- 🛠️ 健壮的错误处理
  - 自动重试机制
  - 详细的错误提示
  - 完整的错误日志
- ⚡ 性能优化
  - 文件上传队列管理
  - 智能并发控制
  - 大文件分片处理

## 注意事项

1. 首次使用需要设置GitHub仓库和Token
2. Token需要有仓库的读写权限
3. init.jpg 文件是必需文件，不可删除，用于CDN测速功能（建议大小<50KB）
4. index.html文件受保护，不可删除
5. 本项目有两个版本：
   - [bbylw/file](https://github.com/bbylw/file): 默认版本，使用固定加速源，稳定可靠
   - [bbylw/fileplus](https://github.com/bbylw/fileplus): 多加速源版本，可根据需求自由增减加速源
6. 强烈推荐使用 Cloudflare Pages 部署:
   - 全球 CDN 加速，访问更快
   - 自动 HTTPS，更加安全
   - 免费额度充足，无需成本
   - 部署简单，维护方便
7. 关于加速方案选择：
   - 有自己域名：优先使用 Cloudflare Pages + 自定义域名部署
   - 无自己域名：使用第三方加速源（如 gitmirror、jsdelivr 等）
   - 注意：直接使用 GitHub Pages 或 Cloudflare Pages 默认域名可能无法获得理想的加速效果

## 更新日志

### 2025.01.01

- 增加多个稳定的加速源
- 优化加速源显示布局
- 改进延迟测试显示效果
- 优化多文件上传机制
- 添加文件上传队列管理
- 改进拖拽上传视觉反馈
- 优化移动端显示效果
- 添加上传进度详细展示
- 添加 Cloudflare Pages 部署说明
