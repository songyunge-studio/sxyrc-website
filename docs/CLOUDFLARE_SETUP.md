# Cloudflare Pages 配置指南

**创建时间**: 2026-04-12  
**创建人**: 老三 宋韵阁  
**适用项目**: 宋向元汝瓷官网 v3.1

---

## 📋 配置步骤

### 1. 登录 Cloudflare

访问：https://pages.cloudflare.com/

### 2. 连接 GitHub 仓库

1. 点击 **"Create a project"**
2. 选择 **"Connect to Git"**
3. 授权 Cloudflare 访问 GitHub
4. 选择仓库：`songyunge-studio/sxyrc-website`
5. 分支：`main`

### 3. 构建设置

```
Build command: npm run build
Build output directory: ./
Root directory: /
```

> **注意**: 如果暂时不使用 TailwindCSS 编译，可以留空 Build command，直接部署静态文件。

### 4. 环境变量（可选）

```
NODE_VERSION = 20
```

### 5. 部署

点击 **"Save and Deploy"**

首次部署会在 1-2 分钟内完成。

---

## 🌐 配置自定义域名

### 主域名：sxyrc.cn

1. 在 Cloudflare Pages 项目页面，点击 **"Custom domains"**
2. 点击 **"Add custom domain"**
3. 输入：`sxyrc.cn`
4. Cloudflare 会自动配置 DNS
5. 等待 DNS 传播（通常几分钟内）

### 品牌域名：宋向元汝瓷。中国

1. 同样在 **"Custom domains"** 添加
2. 输入 punycode 编码：`xn--z4q21eb3jgysu0j.xn--fiqs8s`
3. 或中文：`宋向元汝瓷。中国`
4. 配置 DNS 解析到 Cloudflare

### 备用域名跳转：sxyrc.com.cn → sxyrc.cn

在 Cloudflare Rules 中配置 301 跳转：

1. 访问：https://dash.cloudflare.com/
2. 选择域名：`sxyrc.com.cn`
3. 进入 **"Rules"** → **"Redirect Rules"**
4. 点击 **"Create rule"**
5. 配置：
   ```
   Rule name: Redirect to primary domain
   If incoming requests match: Hostname equals sxyrc.com.cn
   Then: Static redirect
   Redirect to: https://sxyrc.cn
   Status code: 301 - Permanent Redirect
   ```
6. 点击 **"Deploy"**

---

## 🔒 SSL/TLS 配置

Cloudflare Pages 自动提供免费的 SSL 证书，无需手动配置。

### SSL 模式

在 Cloudflare Dashboard 的 **"SSL/TLS"** 设置中：
- 选择 **"Full"** 或 **"Full (strict)"** 模式
- 启用 **"Always Use HTTPS"**

---

## ⚡ 性能优化

### 1. 自动优化

Cloudflare Pages 自动提供：
- 全球 CDN 加速
- HTTP/2 支持
- 自动压缩（Brotli/Gzip）

### 2. 手动优化建议

在 `README.md` 中已包含：
- 关键 CSS 内联
- 图片响应式（srcset）
- 懒加载
- 字体预加载

---

## 📊 监控与分析

### Cloudflare Analytics

访问：https://dash.cloudflare.com/ → 选择域名 → **"Analytics"**

查看：
- 请求次数
- 带宽使用
- 缓存命中率
- 威胁分析

### 集成 Google Analytics

在 `index.html` 中添加：

```html
<!-- Google Analytics -->
<script async src="https://www.googletagmanager.com/gtag/js?id=GA_MEASUREMENT_ID"></script>
<script>
  window.dataLayer = window.dataLayer || [];
  function gtag(){dataLayer.push(arguments);}
  gtag('js', new Date());
  gtag('config', 'GA_MEASUREMENT_ID');
</script>
```

---

## 💰 成本估算

### Cloudflare Pages（免费套餐）

- 请求次数：无限
- 带宽：无限
- 构建次数：500 次/月
- 自定义域名：无限

**预计费用**: ¥0/月

### Cloudflare Workers（免费套餐）

- 请求次数：10 万次/天
- CPU 时间：10ms/请求
- KV 存储：1GB

**预计费用**: ¥0/月（前期）

### 域名续费

| 域名 | 年费 | 备注 |
|------|------|------|
| sxyrc.cn | ¥55/年 | 阿里云续费 |
| sxyrc.com.cn | ¥80/年 | 阿里云续费 |
| 宋向元汝瓷。中国 | ¥280/年 | 中文域名较贵 |

**总计**: ¥415/年

---

## 🔧 故障排查

### DNS 未生效

```bash
# 检查 DNS 解析
dig sxyrc.cn
dig xn--z4q21eb3jgysu0j.xn--fiqs8s

# 检查 Cloudflare DNS 记录
登录 Cloudflare Dashboard → DNS → 检查 A/CNAME 记录
```

### 部署失败

1. 检查 Build command 是否正确
2. 查看构建日志（Cloudflare Pages → Deployments → 查看失败日志）
3. 本地测试：`npm run build`

### SSL 证书问题

- 确保 Cloudflare SSL 模式设置为 "Full" 或 "Full (strict)"
- 等待证书颁发（通常几分钟内）

---

## 📝 下一步行动

1. ✅ GitHub 仓库创建完成
2. ✅ 初始代码推送完成
3. ⏳ Cloudflare Pages 配置（需老爸操作或授权）
4. ⏳ 域名 DNS 配置（需老爸操作）
5. ⏳ 首页开发（Phase 2 继续）

---

## 🔗 关联文档

- [项目 README](../README.md)
- [官网方案决策建议汇总](../04-宋家客厅/20260402_1150_官网方案决策建议汇总.md)
- [悟空技术建议](../04-宋家客厅/20260402_1145_宋悟空_官网重建方案技术建议.md)

---

**更新时间**: 2026-04-12 13:30  
**仓库**: https://github.com/songyunge-studio/sxyrc-website  
**文档位置**: `docs/CLOUDFLARE_SETUP.md`
