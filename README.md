# TradingAgents-CN 🤖📈

> 基于多智能体的中国股票市场交易分析框架

[![Python 3.10+](https://img.shields.io/badge/python-3.10+-blue.svg)](https://www.python.org/downloads/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Docker](https://img.shields.io/badge/docker-supported-blue.svg)](https://www.docker.com/)

TradingAgents-CN 是 [hsliuping/TradingAgents-CN](https://github.com/hsliuping/TradingAgents-CN) 的 Fork 版本，专注于中国 A 股市场的多智能体交易分析。本项目通过协作的 AI 智能体模拟真实的交易公司决策流程，为投资者提供深度市场分析。

## ✨ 主要特性

- 🧠 **多智能体协作** — 分析师、研究员、交易员、风险管理等多角色 AI 智能体
- 📊 **A 股数据支持** — 集成 AKShare、Tushare 等中国金融数据源
- 🔍 **深度市场分析** — 技术分析、基本面分析、情绪分析多维度结合
- 🛡️ **风险管理** — 内置多层风险评估与控制机制
- 🐳 **Docker 支持** — 开箱即用的容器化部署方案
- 🌐 **中文优化** — 针对中文金融语境优化的提示词与分析逻辑

## 🏗️ 系统架构

```
TradingAgents-CN
├── 分析师团队
│   ├── 技术分析师 — K线、均线、技术指标分析
│   ├── 基本面分析师 — 财务数据、估值分析
│   ├── 情绪分析师 — 新闻、社交媒体情绪
│   └── 宏观分析师 — 政策、宏观经济环境
├── 研究团队
│   ├── 多头研究员 — 挖掘买入机会
│   └── 空头研究员 — 识别风险因素
├── 交易团队
│   └── 交易员 — 综合决策与执行建议
└── 风险管理
    └── 风险管理员 — 仓位与风险控制
```

## 🚀 快速开始

### 环境要求

- Python 3.10 或更高版本
- Docker（可选，推荐用于生产环境）

### 方式一：本地安装

```bash
# 克隆仓库
git clone https://github.com/your-username/TradingAgents-CN.git
cd TradingAgents-CN

# 创建虚拟环境
python -m venv venv
source venv/bin/activate  # Windows: venv\Scripts\activate

# 安装依赖
pip install -r requirements.txt

# 配置环境变量
cp .env.example .env
# 编辑 .env 文件，填入您的 API 密钥

# 运行示例
python main.py
```

### 方式二：Docker 部署

```bash
# 克隆仓库
git clone https://github.com/your-username/TradingAgents-CN.git
cd TradingAgents-CN

# 配置环境变量
cp .env.docker .env
# 编辑 .env 文件

# 启动服务
docker-compose up -d
```

## ⚙️ 配置说明

复制 `.env.example` 为 `.env` 并配置以下关键参数：

| 参数 | 说明 | 必填 |
|------|------|------|
| `OPENAI_API_KEY` | OpenAI API 密钥 | 是 |
| `TUSHARE_TOKEN` | Tushare 数据接口 Token | 推荐 |
| `ANTHROPIC_API_KEY` | Anthropic Claude API 密钥 | 可选 |
| `DEEPSEEK_API_KEY` | DeepSeek API 密钥 | 可选 |

详细配置说明请参考 [配置文档](docs/configuration.md)。

## 📖 使用示例

```python
from tradingagents import TradingAgentsGraph

# 初始化交易分析框架
# 注意：个人使用时 deepseek 性价比更高，可将 llm_provider 改为 "deepseek"
ta = TradingAgentsGraph(
    llm_provider="deepseek",
    model="deepseek-chat",
    market="cn"  # 中国市场
)

# 分析股票
result = ta.analyze(
    ticker="000001",  # 平安银行
    date="2024-01-15",
    analysis_depth="deep"
)

print(result["decision"])    # 交易决策
print(result["reasoning"])   # 决策理由
print(result["risk_level"])  # 风险等级
```

## 🤝 贡献指南

欢迎提交 Issue 和 Pull Request！请查看 [贡献指南](CONTRIBUTING.md) 了解详情。

1. Fork 本仓库
2. 创建特性分支 (`git checkout -b feat/amazing-feature`)
3. 提交更改 (`git commit -m 'feat: add amazing feature'`)
4. 推送到分支 (`git push origin feat/amazing-feature`)
5. 提交 Pull Request

## ⚠️ 免责声明

本项目仅供学习和研究目的，不构成任何投资建议。股市有风险，投资需谨慎。作者不对任何基于本工具的投资决策承担责任。

## 📄 许可证

MIT License — 详见 [LICENSE](LICENSE) 文件

## 🙏 致谢

- [TradingAgents](https://github.com/TauricResearch/TradingAgents) — 原始项目
- [hsliuping/TradingAgents-CN](https://github.com/hsliuping/TradingAgents-CN) — 上游 Fork
- [AKShare](https://github.com/akfamily/akshare) — 中国金融数据
- [Tushare](https://tushare.pro/) — 专业金融数据平台
