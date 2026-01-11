# Clash Rules

个人 Clash Verge Rev 分流规则配置，基于方案 B+C 设计：
- **B**: 自建 GitHub 仓库托管自定义规则
- **C**: 引用 blackmatrix7 等成熟规则集

## 使用方法

### 1. Fork 本仓库

### 2. 修改订阅链接

编辑 `config/clash-verge.yaml`，找到 `proxy-providers` 部分，替换你的机场订阅：

```yaml
proxy-providers:
  sspai:
    url: "你的订阅链接1"
  ninja:
    url: "你的订阅链接2"
```

### 3. 导入 Clash Verge Rev

方式一：直接使用本地配置
- 将 `config/clash-verge.yaml` 复制到 Clash Verge Rev 配置目录

方式二：使用 CDN 远程配置（推送到 GitHub 后）
```
https://cdn.jsdelivr.net/gh/你的用户名/clash-rules@release/config/clash-verge.yaml
```

## 目录结构

```
clash-rules/
├── rules/
│   ├── ai-extra.yaml      # AI 补充规则（Claude、Gemini 等）
│   ├── crypto.yaml        # 加密货币交易所
│   ├── direct-extra.yaml  # 自定义直连
│   └── proxy-extra.yaml   # 自定义代理
├── config/
│   └── clash-verge.yaml   # 主配置文件
└── .github/workflows/
    └── release.yml        # 自动发布
```

## 规则来源

| 规则 | 来源 | 说明 |
|------|------|------|
| OpenAI | blackmatrix7 | ChatGPT 等 |
| AI-Extra | 自建 | Claude、Gemini、Copilot 等补充 |
| YouTube | blackmatrix7 | |
| Netflix | blackmatrix7 | |
| Disney+ | blackmatrix7 | |
| BiliBili | blackmatrix7 | |
| Telegram | blackmatrix7 | |
| Twitter | blackmatrix7 | |
| TikTok | blackmatrix7 | |
| PayPal | blackmatrix7 | |
| Apple | blackmatrix7 | |
| Weibo | blackmatrix7 | |
| China | blackmatrix7 | 国内直连 |
| 去广告 | skk.moe | |
| Crypto | 自建 | 交易所 |

## 自定义规则

在 `rules/proxy-extra.yaml` 中添加需要代理的域名：
```yaml
payload:
  - DOMAIN-SUFFIX,example.com
  - DOMAIN,specific.example.com
```

## CDN 刷新

jsDelivr 有 24 小时缓存，强制刷新：
```
https://purge.jsdelivr.net/gh/你的用户名/clash-rules@release/config/clash-verge.yaml
```
