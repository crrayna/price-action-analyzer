# Price Action Analyzer — Al Brooks 价格行为学 Skill

基于 Al Brooks《Trading Price Action》三部曲体系，用于对 A 股/全球股票进行系统化 K 线技术分析的 Codex skill。

## 安装

将整个 `price-action-analyzer` 文件夹放入 `~/.codex/skills/` 目录：

```bash
cp -r price-action-analyzer ~/.codex/skills/
```

重启 Codex 或重新加载 skills 后即可使用。

## 触发方式

在 Codex 中对我说以下任意关键词即可自动激活：

- "用价格行为学分析一下 XX 股票"
- "PA 分析这只票"
- "看看 K 线形态"
- "判断一下趋势"
- "这个回调能入场吗"
- "突破是真还是假"
- "这个楔形会反转吗"

## Skill 结构

```
price-action-analyzer/
├── SKILL.md                           # 分析工作流（5步）
├── agents/openai.yaml                 # Codex UI 元数据
└── references/
    └── price-action-rules.md          # Al Brooks 完整交易规则（13章）
```

## 分析能力

- 市场状态判定（突破/窄通道/宽通道/震荡区间）
- H1/H2/L1/L2 入场信号识别
- 真假突破判断（80% 突破失败规则）
- 反转形态检测（MTR/楔形/抛物线反转/Final Flag/双顶底）
- 20 EMA 关键信号（M2B/M2S/20 GAP Bar）
- 实际盈亏比评估
- 仓位与风险管理建议

## 规则来源

- Al Brooks《Trading Price Action》三部曲（Trends / Trading Ranges / Reversals）
- [LouiePriceAction YouTube 频道](https://www.youtube.com/@LouiePriceAction/videos) 120+ 视频
- NexusFi 社区讨论
- 中文学习笔记

## 依赖

需要 Codex 已配置以下 MCP 工具以获取 K 线数据：

- `china_stock`（A 股数据）
- `cn_financial`（A 股金融数据）

## 许可

仅供学习参考，不构成投资建议。
