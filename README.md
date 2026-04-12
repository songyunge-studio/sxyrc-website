# 宋向元汝瓷官网 v3.1

**域名**: 
- 主站：https://sxyrc.cn
- 备用：https://sxyrc.com.cn (301 跳转)
- 品牌：https://宋向元汝瓷。中国 (品牌展示)

**技术栈**:
- 前端：HTML + TailwindCSS + Alpine.js
- 托管：Cloudflare Pages（免费）
- API：Cloudflare Workers（静态 JSON）
- 图片：Cloudflare Images（免费额度）

**性能目标**:
- 首屏时间：<1.5 秒
- API 响应：<50ms
- Lighthouse：>95 分

**年费预算**: ¥500 以内

---

## 📁 项目结构

```
sxyrc-website/
├── index.html              # 首页
├── about.html              # 关于页面
├── products.html           # 产品列表
├── products/
│   └── [id].html          # 产品详情页
├── craft.html              # 工艺展示
├── contact.html            # 联系页面
├── css/
│   └── style.css          # 自定义样式
├── js/
│   ├── app.js             # 主应用
│   └── chat.js            # 客服聊天窗口
├── images/                 # 图片资源
├── data/
│   ├── products.json      # 产品数据
│   └── stories.json       # 作品故事
├── api/                    # Cloudflare Workers
│   └── index.js           # API 路由
├── .well-known/           # SSL 验证等
└── README.md              # 本文件
```

---

## 🚀 快速开始

### 本地开发

```bash
# 克隆仓库
git clone https://github.com/songyunge-studio/sxyrc-website.git
cd sxyrc-website

# 安装依赖（仅 TailwindCSS 需要）
npm install -D tailwindcss

# 本地预览
npx serve .
```

### 部署到 Cloudflare Pages

1. 登录 https://pages.cloudflare.com/
2. 连接 GitHub 仓库 `sxyrc-website`
3. 构建设置：
   - 构建命令：`npm run build`（如使用 TailwindCSS）
   - 输出目录：`./`
4. 添加自定义域名：
   - `sxyrc.cn`（主域名）
   - `宋向元汝瓷。中国`（punycode: `xn--z4q21eb3jgysu0j.xn--fiqs8s`）

### 配置域名跳转

在 Cloudflare Rules 中配置：
```
sxyrc.com.cn → https://sxyrc.cn (301 Redirect)
```

---

## 🎨 设计规范

### 色彩系统

```css
:root {
  --color-tianqing: #B0C4DE;    /* 天青色 - 主色 */
  --color-yuebai: #F0F8FF;      /* 月白色 - 背景 */
  --color-douqing: #90C4B6;     /* 豆青色 - 辅助 */
  --color-kaipian: #E8E8E8;     /* 开片纹 - 装饰 */
}
```

### Slogan

> **雨过天青云破处**

---

## 🤖 AI 集成

### CLI 命令

```bash
# 信息查询
feishu sxyrc info
feishu sxyrc products list --category=茶杯
feishu sxyrc craft --step=72
feishu sxyrc story --id=123

# 客服对话
feishu sxyrc cs "这个茶杯多少钱？" --agent=xiaoke

# 订单管理
feishu sxyrc order create
feishu sxyrc track --order=12345

# AI 生成文案
feishu sxyrc ai-generate --type=copywriting --product=123
```

### OpenClaw 内容工厂

```yaml
# .claw/workflows/content-factory.yaml
name: 汝瓷内容工厂
trigger: new_product_added
steps:
  - extract: product_details
  - generate:
      - taobao_copywriting
      - douyin_script
      - xiaohongshu_post
      - wechat_article
  - review: human_approval
  - publish: auto_deploy
```

---

## 📊 成功指标

| 指标 | 目标值 | 测量方式 |
|------|--------|---------|
| 首屏加载时间 | <1.5 秒 | Lighthouse |
| API 响应时间 | <50ms | Cloudflare Analytics |
| 年费成本 | ¥500 以内 | 账单统计 |
| 月访问量 | >1000 | Google Analytics |
| CLI 调用次数 | >200/月 | API 日志 |
| 客服满意度 | >95% | 用户评价 |
| 产品咨询转化率 | >15% | 订单统计 |

---

## 📝 开发日志

| 日期 | 事件 | 负责人 |
|------|------|--------|
| 2026-04-12 | 项目启动，Phase 1 完成 | 老三 |
| 2026-04-12 | Phase 2 开始，GitHub 仓库创建 | 老三 |

---

## 🔗 关联文档

- [官网方案决策建议汇总](../04-宋家客厅/20260402_1150_官网方案决策建议汇总.md)
- [小可意见建议](../04-宋家客厅/20260402_1137_宋可可_官网重建方案意见建议.md)
- [悟空技术建议](../04-宋家客厅/20260402_1145_宋悟空_官网重建方案技术建议.md)

---

**创建时间**: 2026-04-12  
**创建人**: 老三 宋韵阁  
**仓库**: https://github.com/songyunge-studio/sxyrc-website
