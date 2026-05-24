# Learning Plan — AI × Web3 School Cohort 0

**Period**: 2026-05-17 ~ 2026-06-14
**Daily Budget**: ~3 hours
**Overall Goal**: Hackathon-ready skills + systematic Web3 understanding

## 🗺️ 课程总览

| 阶段 | 周次 | 内容 |
|------|------|------|
| Book Camp | W1 (5.17-23) | AI 基础 + Web3 基础 + 最小交叉实验 |
| Book Camp | W2 (5.24-30) | AI×Web3 Bridge（支付/身份/权限） |
| Hackathon | W3 (5.31-6.6) | 项目攻坚 |
| Demo Day | W4 | 展示 |

## 🎯 Week 1 目标

### 核心学习目标
- [ ] 理解 LLM、prompt、workflow、agent、tool use、AI coding 的基本概念
- [ ] 理解账户、钱包、签名、交易、Gas、合约、测试网和区块浏览器的链上操作链
- [ ] 至少完成一次 AI 工具实践、一次测试网交互、一次 AI×Web3 最小交叉实验
- [ ] 初步建立权限、安全、人工确认、日志、验证材料和失败恢复意识
- [ ] 为 Week 2 建立共同语言

### 建议学习顺序

```
判断短板 → 补短板 → 两个最小实践 → 交叉实验 → 整理产出
```

**我的路径**：Web3 是短板 → 优先补 **Module B**（Web3 基础）
AI 有基础 → 快速过 **Module A**，重点在实验

---

## 📦 Module A｜AI 基础

### 核心知识点
- [ ] LLM 基本工作方式：概率生成、上下文窗口、擅长/不擅长的边界
- [ ] 四层控制：上下文窗口 / 系统指令 / 提示词 / 工具调用
- [ ] 动手调用 LLM API（跑通第一个请求）
- [ ] Prompt → Workflow → Agent 的边界与失控风险
- [ ] AI Coding 工具的价值与限制
- [ ] AI 输出必须验证的 5 种错误
- [ ] Agent 核心技术组件：State / Memory / MCP / Skills / Tool Calling / Tracing / Guardrails / Handoff / 错误恢复
- [ ] 什么时候需要 agent？

### 实践任务
- [x] 任务 1：搭建 learning agent → Hermes Agent ✅
- [x] 任务 2：创建 GitHub repo → 完成 ✅
- [ ] 任务 3：用 agent 生成可交互学习产物（流程图 / quiz / 小页面）

### 推荐材料
- Hugging Face LLM Course Chapter 1
- Z.ai API 文档 / GLM MaaS API
- Hermes Agent Docs
- Microsoft《AI Agents for Beginners》

---

## 📦 Module B｜Web3 基础

### 核心知识点
- [ ] 账户、地址和钱包的关系
- [ ] 助记词、私钥、地址分别是什么 & 为什么不能泄露
- [ ] 签名与交易的关系
- [ ] Gas 是什么，为什么有成本/失败/等待
- [ ] L1/L2 与执行成本
- [ ] 智能合约 vs 普通后端逻辑
- [ ] 主网 vs 测试网
- [ ] 区块浏览器、钱包提示、交易回执
- [ ] 账户抽象 / 智能账户 / 多签 / Safe（进阶）

### 实践任务
- [ ] 创建测试钱包，理解地址/助记词/私钥
- [ ] 切换到测试网，领测试币，发一笔交易
- [ ] 在区块浏览器中查看交易（哈希/状态/Gas/区块高度）
- [ ] 用 Remix / Hardhat 部署一个最小合约，完成读写

### 推荐材料
- Ethereum Accounts 文档
- MetaMask Getting Started
- Remix IDE
- Sepolia Faucet
- viem / wagmi（前端链上读写）

---

## 🔗 Module C｜最小交叉实验

### 实验方向
- [ ] AI 生成合约交互说明/脚本 → 人工复核 → 测试网执行
- [ ] AI 解释交易或合约 ABI → 人工检查 → 整理学习记录
- [ ] 画出"AI 生成 → 人工复核 → 钱包确认 → 链上执行 → 区块浏览器验证"流程图

---

## 📁 Week 1 交付物
- [x] Learning agent 配置记录（Hermes Agent ✅ 已有）
- [x] GitHub repo 链接 + commit 记录 ✅
- [x] Web3 测试网实践记录（钱包地址 / 交易哈希 / 区块浏览器链接）✅ `web3-testnet-practice.md`
- [x] 基础概念说明：LLM → workflow → agent → 钱包 → 签名 → 交易 → 合约 ✅ `ai-web3-concepts.md`
- [x] 最小交叉实验说明 ✅ `cross-experiment-ai-explains-tx.md`

## 📋 每日打卡流程

1. 读 Handbook 对应章节
2. 完成当日实践任务
3. 写 daily/YYYY-MM-DD.md
4. Commit & push
5. WCB 平台打卡
