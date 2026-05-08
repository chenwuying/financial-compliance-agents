# 金融级智能合规审查多 Agent 系统

> 基于多 Agent 协作与长链推理的合规审查系统，已落地金融科技公司合规部，日处理文档 500+，审查效率提升 90%。

## 📊 核心指标
- 日处理文档：500+
- 首轮审查效率提升：90%
- 风险遗漏率下降：42%
- 月均 Token 消耗：~8 亿

## 🧠 系统架构
三层 Agent 协作，由 LangGraph 编排：

1. **法规解析 Agent** – 基于思维链拆解合规检查点，调用 Claude 3.5 Sonnet 与 DeepSeek-V2。
2. **交叉验证 Agent** – 对抗辩论机制，合规官 vs 业务方，多轮辩论输出风险评级。
3. **报告生成 Agent** – 汇总推理链，生成分段报告与改写建议。

![架构图](architecture.png)

### 对抗辩论示例
参见 [demo-chat-log.txt](./demo-chat-log.txt)

### 生成报告示例
[下载](./sample-report.pdf)

## 🛠️ 技术栈
- 模型：Claude 3.5 Sonnet, DeepSeek-V2
- 编排：LangGraph + 自研调度器
- AI 开发工具：Cline, Aider, Cursor
- 提示工程：Prompt 版本控制与回归测试

## 🚀 在线演示
体验地址：[https://chenwuying.github.io/financial-compliance-agents](https://chenwuying.github.io/financial-compliance-agents)

## 📄 许可证
MIT


graph TD
    A[上传文档] --> B[法规解析Agent<br/>思维链拆解检查点]
    B --> C[交叉验证Agent<br/>合规官 vs 业务方辩论]
    C --> D[报告生成Agent]
    D --> E[合规报告+修改建议]
    B -.-> F[向量检索: 判例库/法规库]
    C -.-> F
