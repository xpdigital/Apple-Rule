# 🍎 Apple-US Rule List for Surge / Stash / Clash

一个用于让 **Apple Intelligence / Siri / iCloud Relay** 等苹果服务强制走 **美国节点** 的规则集。  
主要适用于 Surge、Stash、Clash 等代理工具，方便测试或使用 Apple Intelligence 功能。

---

## 📦 文件说明

**文件名：** `Apple-US.list`  
**托管地址：**  
👉 [https://raw.githubusercontent.com/xpdigital/Apple-Rule/main/Apple-US.list](https://raw.githubusercontent.com/xpdigital/Apple-Rule/main/Apple-US.list)

---

## ⚙️ Surge 引用方式

在你的 Surge 配置文件中加入以下内容：

```ini
[Rule]
RULE-SET,Apple-US,美国节点
FINAL,Proxy

[Rule Provider]
Apple-US = 
  type = http,
  behavior = classical,
  url = https://raw.githubusercontent.com/xpdigital/Apple-Rule/main/Apple-US.list,
  interval = 86400
