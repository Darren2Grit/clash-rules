# Clash 分流规则配置

> 让你的科学上网更智能：国内网站直连、国外网站自动走代理，不同服务走不同节点。

---

## 这是什么？能帮我做什么？

### 先解释几个概念（老手可跳过）

| 名词 | 通俗解释 |
|------|---------|
| **Clash** | 一款科学上网软件，支持 Windows、Mac、手机等多平台 |
| **Clash Verge Rev** | Clash 的一个好用版本，界面美观，推荐使用 |
| **机场** | 提供科学上网服务的商家，你需要付费购买，他们会给你一个「订阅链接」 |
| **订阅链接** | 机场给你的一串网址，Clash 通过它获取服务器节点信息 |
| **分流规则** | 告诉 Clash「哪些网站直连、哪些网站走代理」的配置 |
| **节点** | 代理服务器，不同节点在不同国家/地区，速度和稳定性不同 |

### 这个项目能帮你做什么？

**没有分流规则时：**
- 访问淘宝、微信也走代理 → 速度慢、浪费流量
- 访问 ChatGPT、YouTube 不知道走哪个节点 → 可能被封号或速度慢
- 所有网站都用同一个节点 → 不够灵活

**用了这个项目后：**
- 国内网站（淘宝、微信、B站等）→ 自动直连，不走代理
- ChatGPT、Claude 等 AI → 自动走美国/日本节点
- YouTube、Netflix → 自动走你选择的节点
- Google → 可以单独选择走哪个地区的节点
- 加密货币交易所 → 自动走新加坡等安全节点

---

## 快速开始（5 分钟搞定）

### 第一步：安装 Clash Verge Rev

1. 打开下载页面：https://github.com/clash-verge-rev/clash-verge-rev/releases
2. 找到最新版本，根据你的系统下载：
   - Windows 用户：下载 `.exe` 文件
   - Mac 用户：下载 `.dmg` 文件
   - Mac M1/M2/M3 芯片：选择 `aarch64` 版本
   - Mac Intel 芯片：选择 `x64` 版本
3. 安装并打开软件

### 第二步：复制本项目

> 为什么要复制（Fork）？因为你需要填入自己的机场订阅链接，这是隐私信息，不能公开。

1. 确保你已登录 GitHub（没有账号就注册一个，免费的）
2. 点击本页面右上角的 **Fork** 按钮
3. 在弹出的页面点击 **Create fork**
4. 等待几秒，你就拥有了自己的副本

### 第三步：填入你的机场订阅链接

1. 进入你刚刚 Fork 的仓库（地址是 `github.com/你的用户名/clash-rules`）
2. 点击进入 `config` 文件夹
3. 点击 `clash-verge.yaml` 文件
4. 点击右上角的 **铅笔图标**（Edit this file）
5. 找到下面这段内容（大约在第 40-60 行）：

```yaml
proxy-providers:
  # 机场1 - 替换为你的订阅链接
  airport1:
    type: http
    url: "YOUR_SUBSCRIPTION_URL_1"
```

6. 把 `YOUR_SUBSCRIPTION_URL_1` 替换成你的机场订阅链接
7. 如果你有第二个机场，同样替换 `YOUR_SUBSCRIPTION_URL_2`
8. 如果你只有一个机场，可以删除整个 `airport2` 部分
9. 滚动到页面底部，点击绿色的 **Commit changes** 按钮
10. 在弹出框中再次点击 **Commit changes**

### 第四步：等待自动发布

1. 点击仓库页面上方的 **Actions** 标签
2. 你会看到一个正在运行的任务（黄色圆圈）
3. 等待它变成绿色对勾（通常不到 1 分钟）
4. 完成后，你的配置就发布好了

### 第五步：在 Clash 中导入配置

1. 打开 Clash Verge Rev
2. 点击左侧的 **订阅**（Profiles）
3. 在顶部输入框中粘贴以下地址（把 `你的用户名` 换成你的 GitHub 用户名）：

```
https://cdn.jsdelivr.net/gh/你的用户名/clash-rules@release/config/clash-verge.yaml
```

4. 点击 **导入**（Import）
5. 导入成功后，点击这个配置使其生效（变成高亮状态）
6. 点击左侧的 **代理**（Proxies），你应该能看到各种策略组了

### 第六步：开启代理

1. 点击 Clash Verge Rev 主界面的开关，开启代理
2. 试着访问 https://www.google.com ，如果能打开，说明配置成功！

---

## 策略组说明（如何选择节点）

在 Clash 的「代理」页面，你会看到很多策略组，这里解释每个是干什么的：

| 策略组 | 用途 | 建议设置 |
|-------|------|---------|
| **节点选择** | 默认代理出口 | 选「自动选择」或你喜欢的地区 |
| **自动选择** | 自动测速选最快节点 | 不用管，自动的 |
| **OpenAI** | ChatGPT 等 | 美国或日本节点（避免封号） |
| **Gemini** | Google AI | 美国或日本节点（香港不支持） |
| **Google** | 谷歌服务 | 任意节点都行 |
| **YouTube** | 油管视频 | 选速度快的节点 |
| **Netflix** | 奈飞 | 选有解锁的节点 |
| **Telegram** | 电报 | 新加坡或美国 |
| **Twitter** | 推特 | 任意节点 |
| **Crypto** | 加密货币交易所 | 新加坡（避免风控） |
| **Apple** | 苹果服务 | 直连或香港 |
| **哔哩哔哩** | B站 | 直连（看港澳台番选对应地区） |
| **广告拦截** | 屏蔽广告 | 保持 REJECT |
| **直连** | 国内网站 | 不用改 |

---

## 常见问题

### Q: 导入后看不到节点怎么办？

**可能原因：** 你的机场订阅链接填错了，或者机场服务到期了。

**解决方法：**
1. 检查订阅链接是否正确（直接在浏览器打开链接，应该能看到一堆配置文本）
2. 确认机场服务没有到期
3. 重新编辑 `clash-verge.yaml` 文件，仔细检查订阅链接

### Q: 提示「配置解析错误」怎么办？

**可能原因：** 编辑文件时不小心破坏了格式。

**解决方法：**
1. YAML 文件对格式要求很严格，特别是空格
2. 订阅链接必须用英文引号 `"` 包裹
3. 如果实在搞不定，删除你 Fork 的仓库，重新 Fork 一次，仔细编辑

### Q: 网站能打开，但速度很慢？

**解决方法：**
1. 在 Clash 的「代理」页面，点击「自动选择」旁边的测速图标
2. 等待测速完成，选择延迟低的节点
3. 或者手动在「节点选择」中选一个速度快的节点

### Q: ChatGPT/Claude 提示地区不支持？

**解决方法：**
1. 在「代理」页面找到「OpenAI」策略组
2. 切换到美国或日本节点
3. 清除浏览器 Cookie 后重试

### Q: 修改了配置但没生效？

**可能原因：** CDN 有缓存。

**解决方法：**
1. 在浏览器中访问以下地址（替换你的用户名）来清除缓存：
```
https://purge.jsdelivr.net/gh/你的用户名/clash-rules@release/config/clash-verge.yaml
```
2. 回到 Clash，右键点击你的配置，选择「更新」

### Q: 我想添加自己的规则怎么办？

**添加需要走代理的网站：**
1. 编辑 `rules/proxy-extra.yaml` 文件
2. 在 `payload:` 下面添加：
```yaml
payload:
  - DOMAIN-SUFFIX,要代理的网站.com
```

**添加需要直连的网站：**
1. 编辑 `rules/direct-extra.yaml` 文件
2. 格式同上

---

## 项目结构（进阶用户）

```
clash-rules/
├── config/
│   └── clash-verge.yaml      # 主配置文件，包含策略组和规则
├── rules/
│   ├── ai-extra.yaml         # AI 服务规则（自动同步）
│   ├── gemini.yaml           # Google AI 规则（自动同步）
│   ├── crypto.yaml           # 加密货币规则（自动同步）
│   ├── direct-extra.yaml     # 自定义直连规则（手动维护）
│   └── proxy-extra.yaml      # 自定义代理规则（手动维护）
└── .github/workflows/
    ├── sync-rules.yml        # 每天自动从上游同步规则
    └── release.yml           # 自动发布到 release 分支
```

**规则自动更新：** `ai-extra.yaml`、`gemini.yaml`、`crypto.yaml` 每天北京时间 8:00 自动从上游同步最新规则，无需手动维护。

---

## 规则来源致谢

- [blackmatrix7/ios_rule_script](https://github.com/blackmatrix7/ios_rule_script) - 提供大部分分流规则
- [logicrw/RuleGo](https://github.com/logicrw/RuleGo) - AI 和加密货币规则来源

---

## 遇到问题？

如果按照教程操作后还是有问题，可以：
1. 在本仓库提 [Issue](../../issues)
2. 附上你的问题描述和截图

