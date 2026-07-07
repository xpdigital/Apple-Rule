# Apple AI Rule List for Surge

一个用于让 **Apple Intelligence / Siri / iCloud Private Relay / Apple Relay** 等 Apple 相关服务走指定美国节点的 Surge 规则集。

## 文件说明

**文件名：** `Apple-AI.list`

**托管地址：**

```text
https://raw.githubusercontent.com/xpdigital/Apple-Rule/refs/heads/main/Apple-AI.list
```

规则内容使用 Surge `RULE-SET` 支持的 classical 规则格式。规则集文件内每一行只包含匹配规则，例如：

```text
DOMAIN,guzzoni.apple.com
DOMAIN-SUFFIX,smoot.apple.com
```

规则集内不需要在每行末尾填写策略组名称。

主要包含：

- Apple Intelligence / Siri 相关域名
- iCloud Private Relay / Apple Relay 相关域名
- Apple Relay 使用的 Cloudflare / Fastly 边缘域名
- Apple 位置、资源与 iCloud 网关相关域名

## Surge 使用方式

在 Surge 配置文件的 `[Rule]` 段加入下面这一行，并放在 `GEOIP`、`FINAL` 等兜底规则之前：

```ini
RULE-SET,https://raw.githubusercontent.com/xpdigital/Apple-Rule/refs/heads/main/Apple-AI.list,美国节点,no-resolve
```

其中 `美国节点` 需要替换成你自己 Surge 配置里的代理策略组名称，例如 `Proxy`、`US`、`United States` 等。

完整示例：

```ini
[Proxy Group]
美国节点 = select, US-01, US-02, US-03

[Rule]
RULE-SET,https://raw.githubusercontent.com/xpdigital/Apple-Rule/refs/heads/main/Apple-AI.list,美国节点,no-resolve
GEOIP,CN,DIRECT
FINAL,Proxy
```

保存配置后，在 Surge 中更新配置或重新加载规则即可生效。

注意：Surge 不需要单独写 `[Rule Provider]`。远程规则集可以直接在 `[Rule]` 段通过 `RULE-SET,URL,策略组` 引用。

## 参考

- [Surge Manual: Ruleset](https://manual.nssurge.com/rule/ruleset.html)
- [Surge Manual: Domain-based Rule](https://manual.nssurge.com/rule/domain-based.html)
