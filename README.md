# proxylist

niki（mihomo/Clash 内核）的**个人补充规则集**，与 MetaCubeX 官方 geosite/geoip 集配合使用。

## 规则集用途

- **`proxy.list`** → 在 nikki 里映射为 `RULE-SET,proxy,日本自动`（走代理，命中优先于各专用组）。
  收录**国内无法直连/受限**的海外第三方服务：视频平台、社交通讯、AI 服务、云盘、开发协作工具等。
  官方集已覆盖的（YouTube/Steam/NETFLIX/Wallet/Apple/Google/GitHub 等）不在此重复。

- **`no_proxy.list`** → 映射为 `RULE-SET,no_proxy,直连,no-resolve`（直连，高优先级）。
  收录**必须走国内直连**的服务：内网 IP、PT 站、国内视频/购物/支付/云厂商等。

## 维护约定

- 每条一行，格式 `DOMAIN-SUFFIX,xxx` 或 `IP-CIDR,xxx,no-resolve`。
- 用 `# 分类` 注释分块。
- 新增前先确认：①nikki 官方集是否已覆盖 ②现有条目是否已包含该后缀。
- Telegram 由 nikki 专用 `telegram_domain`/`telegram_ip` 规则处理，不在此文件。

## 生效

niki 配置里 rule-providers 已引用本仓库 `refs/heads/main`，改完 push 后，niki 按 `interval`（24h）自动拉取，或手动重载 profile 立即生效。
