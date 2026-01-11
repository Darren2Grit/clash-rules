# Clash 智能分流配置

**一句话介绍：** 让你上网更聪明——国内网站不绕路，国外网站自动翻。

---

## 📖 什么是分流？

想象你要寄快递：
- 寄到国内 → 用顺丰，又快又便宜
- 寄到国外 → 用 DHL，虽然贵但能送到

**分流就是让电脑自动判断：**
- 打开淘宝 → 直接连，不走代理
- 打开 Google → 自动走代理
- 打开 ChatGPT → 自动选美国线路（避免封号）

**没有分流 = 所有快递都用 DHL = 又慢又费钱**

---

## 🚀 5 分钟上手

### 准备工作

你需要：
1. ✅ 一个「机场」的订阅链接（就是你买代理服务后，商家给你的那串网址）
2. ✅ 一个 GitHub 账号（免费注册：https://github.com）
3. ✅ 电脑上装好 Clash Verge Rev（下载：https://github.com/clash-verge-rev/clash-verge-rev/releases）

---

### 第 1 步：复制本项目

点击页面右上角的绿色按钮 **「Fork」** → 点击 **「Create fork」**

> 💡 这相当于把这个项目复制一份到你自己的账号下

---

### 第 2 步：填入你的机场订阅

1. 打开你 Fork 后的项目（网址变成了 `github.com/你的名字/clash-rules`）
2. 点进 **config** 文件夹
3. 点击 **clash-verge.yaml**
4. 点右上角的 ✏️ 铅笔图标
5. 按 `Ctrl+F`（Mac 用 `Cmd+F`）搜索 `YOUR_SUBSCRIPTION_URL`
6. 把它替换成你的机场订阅链接，像这样：

```
替换前：url: "YOUR_SUBSCRIPTION_URL_1"
替换后：url: "https://xxx.com/你的订阅链接"
```

7. 拉到最下面，点绿色按钮 **「Commit changes」** 保存

---

### 第 3 步：等 1 分钟

点击页面上方的 **「Actions」** 标签，等黄色圆圈变成 ✅ 绿色勾

---

### 第 4 步：导入到 Clash

1. 打开 Clash Verge Rev
2. 点左边的 **「订阅」**
3. 在顶部输入框粘贴：
```
https://cdn.jsdelivr.net/gh/你的GitHub用户名/clash-rules@release/config/clash-verge.yaml
```
4. 点 **「导入」**
5. 点一下刚导入的配置，让它变亮（选中状态）

---

### 第 5 步：开启！

打开 Clash 主界面的开关 → 访问 google.com 试试 → 能打开就成功了 🎉

---

## 🎛️ 怎么切换线路？

打开 Clash → 点左边「代理」→ 看到很多组：

| 看到这个 | 它控制什么 | 怎么选 |
|---------|-----------|--------|
| 🚀 节点选择 | 大部分国外网站 | 选「自动选择」最省心 |
| 🤖 OpenAI | ChatGPT | 选 🇺🇸 美国 或 🇯🇵 日本 |
| 💎 Gemini | Google AI | 选 🇺🇸 美国 或 🇯🇵 日本（不能选香港！）|
| 🌐 Google | 谷歌搜索等 | 随便选，都能用 |
| 📹 YouTube | 看视频 | 选速度快的 |
| 💰 Crypto | 币安、OKX 等 | 选 🇸🇬 新加坡 |
| 📺 哔哩哔哩 | B 站 | 保持「直连」|

---

## ❓ 遇到问题？

### 导入后一个节点都没有？
→ 你的订阅链接可能填错了，回去检查一下

### 提示「解析错误」？
→ 编辑时可能不小心删了什么，重新 Fork 一次吧

### 改了配置没生效？
→ 访问这个链接清除缓存（把 `你的用户名` 换成你的）：
```
https://purge.jsdelivr.net/gh/你的用户名/clash-rules@release/config/clash-verge.yaml
```
然后回到 Clash，右键配置 → 更新

### ChatGPT 说不支持我的地区？
→ 去「代理」页面，把「OpenAI」那一组换成美国节点

---

## 📁 文件说明（给想折腾的人）

```
config/clash-verge.yaml  ← 主配置，改订阅链接就改这个
rules/proxy-extra.yaml   ← 想加代理规则就加这里
rules/direct-extra.yaml  ← 想加直连规则就加这里
```

AI、加密货币相关的规则每天自动更新，不用管。

---

## 🙏 致谢

规则来源：[blackmatrix7](https://github.com/blackmatrix7/ios_rule_script)、[RuleGo](https://github.com/logicrw/RuleGo)
