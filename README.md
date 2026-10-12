# 币圈分流 · Shadowrocket

本配置以用户提供的「含策略组版本，基于官方群组【懒人配置.conf 2025-02-26 22:31:11】更新，2026-09-16」为基础，保留原有通用分流、DNS、重写和 MITM 设置，并加入加密货币分流。

## 扫码导入

![Shadowrocket 扫码导入配置](shadowrocket-qr.svg)

二维码包含 Shadowrocket 的配置导入链接，指向本仓库的 `crypto.conf`。在 Shadowrocket 中扫描后，按提示下载并使用配置。已有节点或订阅仍需自行添加；如果扫码没有跳转到配置导入页，请按下方 URL 步骤导入。

## 使用

1. 在 Shadowrocket 首页添加你的节点或节点订阅。
2. 在「配置」中通过 URL 下载并启用 [crypto.conf](https://raw.githubusercontent.com/nimingzhe01/bi-fenliu/main/crypto.conf)。
3. 把全局路由设为「配置」。
4. 在策略组 **Crypto** 中选择使用的节点地区，或选择 **全部节点** 后手动选具体节点。默认是 `PROXY`。
5. 可在连接记录中确认币圈域名命中 **Crypto**。

## 节点分组

配置保留香港、台湾、日本、新加坡、韩国、美国地区组，新增 **全部节点**，用于查看和选择订阅中其他名称的节点。地区组根据节点名称关键词筛选；若订阅没有对应地区的节点，该组仍可能为空。配置文件本身不会生成代理节点。

## 币圈规则

交易所、行情与 DeFi、钱包与区块浏览器的 25 条规则集中保存在 [rules/Crypto.list](rules/Crypto.list)。其[原始下载地址](https://raw.githubusercontent.com/nimingzhe01/bi-fenliu/main/rules/Crypto.list)可单独使用。主配置在通用规则之前通过以下一行加载它，匹配流量交给 **Crypto** 策略组：

```ini
RULE-SET,https://raw.githubusercontent.com/nimingzhe01/bi-fenliu/main/rules/Crypto.list,Crypto
```

规则文件只包含匹配条件；`Crypto` 是主配置中的策略组。未命中的流量继续按原配置处理。以后增删币圈域名，只需修改 `rules/Crypto.list` 并在 Shadowrocket 中更新配置或规则集。二维码仍指向主配置，无需更换。

原配置中部分服务规则使用了与策略组定义不一致的大写名称；现已统一为实际策略组名。

请使用自己的可信节点与订阅，并在登录、转账前核对服务域名。
