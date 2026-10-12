# 币圈分流（Shadowrocket）

让常用加密货币服务走 Shadowrocket 当前选中的代理节点，其余流量直连。仓库不包含代理节点、订阅或账户信息。

## 直接导入完整配置

1. 先在 Shadowrocket 首页添加并选中你自己的可用节点。
2. 在「配置」中通过 URL 下载并使用 [crypto.conf](https://raw.githubusercontent.com/nimingzhe01/bi-fenliu/main/crypto.conf)。
3. 将全局路由设为「配置」。规则命中的域名使用 `PROXY`，其余请求按 `FINAL,DIRECT` 直连。
4. 打开 Shadowrocket 的连接记录，确认目标服务显示为 `PROXY`。

## 加入现有配置

如果你已有自己的 Shadowrocket 配置，无需替换整个配置。在现有配置的 `[Rule]` 中、`FINAL` 规则之前加入：

```ini
RULE-SET,https://raw.githubusercontent.com/nimingzhe01/bi-fenliu/main/crypto.list,PROXY
```

规则集只包含匹配条件，使用你的现有配置决定其他流量如何连接。

## 范围与维护

- 涵盖常见交易所、行情/DeFi、钱包和区块浏览器域名；具体条目见 [crypto.list](crypto.list)。
- `DOMAIN-SUFFIX` 会匹配根域名及其子域名。未列出的域名仍遵循其他规则；在完整配置中会直连。部分 App 使用额外域名时，可根据连接记录补充规则。
- 规则只改变网络连接方式，不提供节点，也不会替你验证交易平台网址。登录或转账前请自行核对官方域名。
- 配置不启用 HTTPS 解密、脚本或 URL 重写。
