# liquidity-db-arch · 资金面数据库 技术架构手册

> **skill-资金面数据库**（liquidity-db）的解耦架构文档 —— 面向集成者与二次开发者。
> 银行间流动性全景跟踪：9 大维度 × 34 分析视角 × 5 数据源 × 4 取数引擎。
> **作者：叶青** · 文档开源，Skill 源码不开源。

---

## 🚀 一句 Prompt 获取 Skill

在任意 AI Agent 对话框中输入：

```
请访问 https://kmrhoavgygtv.sealosbja.site/api/skill-installer
安装 skill-资金面数据库 skill
```

带凭证配置版本：

```
请访问 https://kmrhoavgygtv.sealosbja.site/api/skill-installer
安装 skill-资金面数据库 skill，配置 DM Quant API 凭证
```

安装后验证：

```
运行资金面数据库的 fetcher.status()，确认 DM / iFinD HTTP / AKShare 各数据源可用状态，
并取最近一周 DR007 验证取数链路
```

Skill 商店直链：<https://kmrhoavgygtv.sealosbja.site>

---

## 文档清单

| 文件 | 说明 |
|------|------|
| `architecture.html` | 技术架构手册（自包含 HTML，fioutput Report 设计体系 · Navy） |
| `README.md` | 本文件 |
| `LICENSE` | CC BY-NC 4.0 |

在线阅读：<https://kmrhoavgygtv.sealosbja.site/pages/tutorial-liquidity-db-architecture/>

---

## 架构概览

```
L4  输出层    10板块HTML周报 + 图表引擎 + 6套点评模板        ← 可独立渲染
L3  计算层    9套公式 + 5维综合评分卡 + 5类拐点信号          ← 可独立计算
L2  知识层    34视角分析逻辑 + 阈值框架 + M码/报表文档       ← 可独立查阅
L1  取数层    DmFetcher / iFinD HTTP / AKShare / Unified    ← 可独立取数
L0  数据源    DM Quant API · Wind MCP · iFinD · AKShare     ← 可独立订阅
```

- **L1 取数层**：DM Quant API 一家 100% 覆盖 34 视角；五源自动降级链
- **L2 知识层**：data_contract.yaml（34视角×5源取数代码）+ 5 个知识库文件（preserve 模式，升级不覆盖）
- **L3 计算层**：资金松紧/分层/IRS Z值/隐含远期/Carry/基差/NCD净融资/大行融出变化率/季节性Z值
- **L4 输出层**：`output/资金面周报_{YYYYMMDD}.html`，40+ 模板变量

## 集成模式

| 模式 | 深度 | 适合 |
|------|------|------|
| A 全流程 | 一句话生成周报 | 周报组装器/日报/看板 |
| B 只取数 | 把 fetcher/ 当独立客户端 | 自建数据库/回测 |
| C 只查知识 | knowledge/ 当分析手册 | Wind/iFinD 用户查码 |
| D 只复用输出 | 拿走模板与图表函数 | 已有数据管道 |

---

## License

[CC BY-NC 4.0](LICENSE) — 文档开源，Skill 源码（SKILL.md / fetcher/ / knowledge/ / templates/）不开源。

**作者：叶青** · fioutput Report Design System · Navy
