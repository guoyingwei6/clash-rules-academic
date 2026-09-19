# clash-rules-academic

Clash/Mihomo 规则集：学术直连 + AI 服务 + 个性化杂项。

## 规则文件

| 文件 | 域名数 | 内容 | 建议目标组 |
|---|---|---|---|
| `Rules/Academic.yaml` | 40 | 期刊/数据库/预印本/中文库/Apple CDN/deepseek | DIRECT（全局直连） |
| `Rules/AI-Extra.yaml` | 20 | Claude/OpenAI/Gemini/Grok/Perplexity/MiniMax/DDG | 代理（AI 组） |
| `Rules/Google-Extra.yaml` | 1 | antigravity-unleash.goog | 代理（谷歌服务组） |
| `Rules/Node-Select.yaml` | 11 | cloudflare/updf/小宇宙/googleapis.cn/gmail 等杂项 | 手动 select 组 |

> 每个文件内按功能分块注释（`# ===== 分区 =====`），一个文件对应一个目标组。

## 引用方式

在你的 Clash/Mihomo 配置或 Verge 扩展脚本中：

```yaml
rule-providers:
  academic:
    type: http
    format: yaml
    behavior: classical
    url: https://raw.githubusercontent.com/guoyingwei6/clash-rules-academic/main/Rules/Academic.yaml
    path: ./ruleset/academic.yaml
    interval: 86400
  ai-extra:
    type: http
    format: yaml
    behavior: classical
    url: https://raw.githubusercontent.com/guoyingwei6/clash-rules-academic/main/Rules/AI-Extra.yaml
    path: ./ruleset/ai-extra.yaml
    interval: 86400
  google-extra:
    type: http
    format: yaml
    behavior: classical
    url: https://raw.githubusercontent.com/guoyingwei6/clash-rules-academic/main/Rules/Google-Extra.yaml
    path: ./ruleset/google-extra.yaml
    interval: 86400
  node-select:
    type: http
    format: yaml
    behavior: classical
    url: https://raw.githubusercontent.com/guoyingwei6/clash-rules-academic/main/Rules/Node-Select.yaml
    path: ./ruleset/node-select.yaml
    interval: 86400

rules:
  # ===== 学术直连 =====
  - RULE-SET,academic,DIRECT
  # ===== AI 补充 =====
  - RULE-SET,ai-extra,你的AI组名
  # ===== 谷歌补充 =====
  - RULE-SET,google-extra,你的谷歌组名
  # ===== 杂项（邮件/工具站） =====
  - RULE-SET,node-select,你的select组名
```

## 设计说明

- **为什么分 4 个文件**：mihomo 的 `RULE-SET` 机制是整个文件指向一个目标组，一个文件无法同时表达"直连+代理"两种行为。按目标分组拆文件，引用时 1 文件 = 1 行 provider + 1 行 rule。
- **jsDelivr 备选**：raw.githubusercontent.com 访问不佳时，可替换为 `https://fastly.jsdelivr.net/gh/guoyingwei6/clash-rules-academic@main/Rules/xxx.yaml`。
