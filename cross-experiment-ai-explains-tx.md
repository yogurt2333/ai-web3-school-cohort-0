# 最小交叉实验说明：AI 解释链上交易

> AI × Web3 School Cohort 0 — Week 1 交付物
> 实验时间：2026-05-19

---

## 实验概述

让 AI（Hermes Agent）解释一笔真实的 Sepolia 测试网交易，逐字段分析交易结构和 Gas 构成，然后人工在 Etherscan 上核对验证。

## 实验流程

```
AI 读取交易 → AI 逐字段解释 → 人工核对 Etherscan → 整理学习记录
```

## 实验内容

### 1. 交易数据

通过 RPC 调用 `eth_getTransactionByHash` 获取了第一笔 Sepolia 交易的原始数据：

**交易哈希**：`0x9ce6ce41d3ee8c6ffd7bce76d52a168f2cbd30bf6aed61c6494c6131e48cf9d8`

### 2. AI 分析结果

AI（Hermes Agent）对交易原始数据做了逐字段拆解：

| 字段 | 原始值（Hex） | 解析值 | AI 解释 |
|------|-------------|--------|--------|
| `nonce` | `0x0` | 0 | 钱包发出的第一笔交易 |
| `value` | `0x16345785d8a0000` | 0.1 ETH | 转账金额 |
| `gas` | `0x7b0c` | 31,500 | 愿意支付的最大 Gas 上限 |
| `gasPrice` | `0x5beeb4ea` | 1.542 Gwei | 实际 Gas 价格 |
| `maxPriorityFeePerGas` | `0x59682f00` | 1.5 Gwei | 给验证者的小费 |
| `type` | `0x2` | EIP-1559 | 现代交易类型 |
| `input` | `0x` | 空 | 纯转账，无合约调用 |

### 3. Gas 结构深度解释

AI 进一步解释了 EIP-1559 的费用模型：

```
总费用 = Gas Used × Gas Price
       = 21,000 × 1.542 Gwei
       = 0.00003238 ETH

组成：
- Base Fee: 0.04 Gwei → 🔥 销毁（通缩机制）
- Priority Fee: 1.5 Gwei → 🎁 给验证者（激励打包）
```

同时解释了为什么普通 ETH 转账固定消耗 **21,000 Gas**，以及为什么 Nonce=0 有纪念意义。

### 4. 人工验证

在 Sepolia Etherscan 打开交易链接，逐项核对 AI 的分析：

- ✅ 交易状态：Success
- ✅ 金额：0.1 ETH
- ✅ Gas Used：21,000
- ✅ Nonce：0
- ✅ 区块高度：10,879,178

**结论：AI 解释与 Etherscan 数据完全一致。**

## 实验结论

### ✅ AI 能干的事
- 快速解析交易原始数据
- 解释 Gas 结构和 EIP-1559 机制
- 指出值得注意的细节（Nonce=0 的意义、Gas 优化的空间）
- 给出形象的类比帮助理解

### ⚠️ AI 不能替代的事
- **最终检查权**：必须自己在 Etherscan 上看一眼，确认 AI 没胡说
- **Gas 定价决策**：AI 可以解释，但你得根据网络拥堵决定设多少 Tip
- **安全判断**：AI 无法判断这笔交易是不是被钓鱼网站诱导的

### 💡 核心原则

> **AI 生成 → 人工复核 → 钱包确认**
>
> 这个链路里每一层都是安全冗余，少一层就是风险敞口。

---

*记录人：段宇轩*
*仓库：github.com/yogurt2333/ai-web3-school-cohort-0*
