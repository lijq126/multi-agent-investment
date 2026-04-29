# Multi-Agent Investment Analysis Framework

> 多智能体金融投研分析框架 - 模拟专业投资公司的协作模式，通过多个专业化 AI 角色协同分析股票、基金或行业，形成结构化的投资研究报告。

## 特性

- **4角色并行分析**：基本面分析师、情绪分析师、行业分析师、风险分析师同时工作
- **多空辩论机制**：自动生成多头论点 vs 空头论点，识别核心分歧
- **结构化研报输出**：标准化投资研究报告模板，覆盖8大模块
- **双模式运行**：快速问答模式 + 深度流程模式
- **数据驱动**：对接金融数据 API，获取实时行情、财务报表、机构持仓等

## 文件结构

```
multi-agent-investment/
├── README.md                              # 本文件
├── LICENSE                               # MIT 开源协议
├── .gitignore                            # Git 忽略规则
└── skill/
    ├── SKILL.md                          # 核心 Skill 定义
    └── references/
        ├── fundamental-analyst.md        # 基本面分析框架
        ├── sentiment-analyst.md          # 情绪分析框架
        ├── industry-analyst.md           # 行业分析框架
        ├── risk-analyst.md               # 风险评估框架
        └── report-template.md            # 研报输出模板
```

## 安装

### 方式一：手动安装

将 `skill/` 目录完整复制到 WorkBuddy 的用户级 Skill 目录：

```bash
# 克隆仓库
git clone https://github.com/lijq126/multi-agent-investment.git

# 复制 skill 目录到 WorkBuddy skills 目录
cp -r multi-agent-investment/skill ~/.workbuddy/skills/multi-agent-investment
```

Windows PowerShell：

```powershell
git clone https://github.com/lijq126/multi-agent-investment.git
Copy-Item -Recurse multi-agent-investment\skill $env:USERPROFILE\.workbuddy\skills\multi-agent-investment
```

### 方式二：Skill 管理器安装

1. 打开 WorkBuddy 左侧边栏的「Skills」面板
2. 点击「Install from URL」
3. 输入本仓库地址：`https://github.com/lijq126/multi-agent-investment`

## 使用方法

### 触发词

| 场景 | 示例 |
|------|------|
| 股票投资价值分析 | "帮我分析贵州茅台的投资价值" |
| 基金分析 | "分析中概互联ETF值得买吗" |
| 行业研究 | "分析新能源汽车行业" |
| 板块对比 | "对比光伏和锂电池赛道" |
| 风险评估 | "我的持仓比亚迪有什么风险" |
| 事件驱动分析 | "美联储降息对A股有什么影响" |
| 市场情报 | "最近半导体板块怎么样" |

### 分析流程

```
用户请求
    ↓
理解需求（标的 + 分析目的）
    ↓
分析师团队并行分析（基本面 / 情绪 / 行业 / 风险）
    ↓
多空辩论（多头论点 vs 空头论点）
    ↓
综合研报输出（投资评级 + 操作建议 + 核心逻辑）
```

### 交互模式

- **快速问答**：问题明确时直接回答，自动识别需要的分析师角色
- **深度分析**：包含"分析""研究""评估""对比"等关键词时启动完整协作流程

## 四大分析师角色

| 角色 | 职责 | 核心指标 |
|------|------|----------|
| **基本面分析师** | 评估财务质量和内在价值 | ROE、毛利率、现金流、PE/PB估值 |
| **情绪分析师** | 评估市场情绪和预期 | 机构持仓、分析师评级、资金流向 |
| **行业分析师** | 评估行业赛道和竞争格局 | 行业空间、竞争格局、产业链位置 |
| **风险分析师** | 识别潜在风险因素 | 经营风险、财务风险、市场风险 |

## 输出报告模块

标准研报包含 8 个模块：

1. **标的概览** - 基本信息、市值、当前价格
2. **基本面分析** - 盈利能力、财务质量、估值分析
3. **情绪与预期** - 机构持仓、分析师预期、市场情绪
4. **行业与竞争** - 行业空间、竞争格局、产业链位置
5. **风险评估** - 四维风险矩阵（经营/财务/市场/外部）
6. **多空辩论结论** - 多头逻辑 vs 空头逻辑，力量对比
7. **投资建议** - 综合评级、操作建议、核心投资逻辑
8. **附录** - 数据来源、分析方法论、免责声明

## 协同使用

本框架可与 [短线精灵（short-term-stock-picker）](https://github.com/lijq126/short-term-stock-picker) 协同使用，详见仓库中的 [SYNERGY.md](https://github.com/lijq126/short-term-stock-picker/blob/main/SYNERGY.md)。

## 数据来源

- **行情与财务数据**：通过 `finance-data-retrieval` / `neodata-financial-search` Skill 获取
- **行业与政策数据**：通过 WebSearch 获取最新研报和政策动态
- **专业评分**：可结合 `company-quality`、`dividend-returns` 等 Skill 获取结构化评分

## 推荐模型配置

| 任务类型 | 推荐模型 |
|----------|----------|
| 深度分析 | GPT-4o / Claude-3.5-Sonnet / DeepSeek-V3 |
| 快速问答 | GPT-4o-mini / Claude-3-Haiku / Qwen-Turbo |
| 中文市场 | 智谱 GLM-4 / 阿里 Qwen-Max / DeepSeek |

## 注意事项

1. **免责声明**：分析结果仅供研究参考，不构成投资建议
2. **数据时效**：基于当前可获取的数据，定期更新
3. **模型限制**：LLM 存在幻觉风险，关键数据需二次验证
4. **风险教育**：建议用户理解风险后再做投资决策

## 许可证

[MIT License](LICENSE)
