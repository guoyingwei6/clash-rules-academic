# clash-rules-academic

Clash/Mihomo 规则集：学术直连 + AI 服务 + 个性化杂项。

## 规则集

| 文件 | 用途 | 建议目标 |
|---|---|---|
| `Rules/Academic.yaml` | 学术期刊/数据库直连（保机构 IP） | DIRECT |
| `Rules/AI-Extra.yaml` | AI 服务补充域名 | 代理 |
| `Rules/Google-Extra.yaml` | 谷歌服务补充 | 代理 |
| `Rules/Node-Select.yaml` | 个性化杂项（走节点选择组） | 自选 |

## 引用方式

```yaml
rule-providers:
  academic:
    type: http
    format: yaml
    behavior: classical
    url: https://raw.githubusercontent.com/guoyingwei6/clash-rules-academic/main/Rules/Academic.yaml
    path: ./ruleset/academic.yaml
    interval: 86400
rules:
  - RULE-SET,academic,DIRECT
```
