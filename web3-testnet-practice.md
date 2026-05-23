# Web3 测试网实践记录

> AI × Web3 School Cohort 0 — Week 1 交付物
> 2026-05-19 ~ 2026-05-23

---

## 一、钱包与环境配置

| 项目 | 内容 |
|------|------|
| 钱包工具 | MetaMask |
| 网络 | Sepolia Testnet |
| 钱包地址 | `0xED3802DDD5E1a700FD2071F32a2c6f5ea9415a51` |
| 助记词/私钥 | ❌ 不公开（已安全保存） |

### 配置步骤

1. 安装 MetaMask 浏览器扩展
2. 在设置中启用测试网络
3. 切换到 Sepolia 测试网
4. 创建测试钱包，记录地址

---

## 二、领取测试币

### 遇到的困难

所有主流 Sepolia Faucet 均因需要 **Google 账号 / GitHub 账号** 而无法使用：

| Faucet | 要求 | 结果 |
|--------|------|------|
| Alchemy Sepolia Faucet | 需主网 ETH 余额 | ❌ |
| Google Cloud Faucet | 需 Google 账号 | ❌ |
| BuildBear | 报错 | ❌ |
| QuickNode | 需主网余额 | ❌ |
| PoW Faucet (pk910) | 需主网余额 | ❌ |

### 解决方案

通过 **LXDAO 社群成员直接转账** 获得 Sepolia 测试 ETH。社群支持是解决测试币问题的最有效途径。

---

## 三、第一笔链上交易

### 基本信息

| 字段 | 值 |
|------|-----|
| 交易哈希 | `0x9ce6ce41d3ee8c6ffd7bce76d52a168f2cbd30bf6aed61c6494c6131e48cf9d8` |
| 区块浏览器 | https://sepolia.etherscan.io/tx/0x9ce6ce41d3ee8c6ffd7bce76d52a168f2cbd30bf6aed61c6494c6131e48cf9d8 |
| 日期 | 2026-05-19 |
| 类型 | ETH 转账（`input: 0x`） |
| 金额 | **0.1 ETH** |
| 接收方 | `0x50430634df68f7e45881ef6940fb0f277046136c`（朋友） |
| 状态 | ✅ 成功 |

### Gas 详情

| 字段 | 值 |
|------|-----|
| Nonce | 0（钱包第一笔交易 🎉） |
| Gas Limit | 31,500 |
| Gas Used | 21,000（普通转账固定消耗） |
| Gas Price | 1.542 Gwei |
| maxFeePerGas | 1.555 Gwei |
| maxPriorityFeePerGas | 1.5 Gwei（Tip） |
| Base Fee | 0.04 Gwei（被销毁） |
| 总手续费 | 0.00003238 ETH |
| 区块高度 | 10,879,178 |
| 交易类型 | Type 2（EIP-1559） |

### Gas 构成解析

```
总费用 = Gas Used × Gas Price
       = 21,000 × 1.542 Gwei
       = 0.00003238 ETH

其中：
- Base Fee (0.04 Gwei) → 🔥 销毁
- Priority Fee (1.5 Gwei) → 🎁 给验证者
```

---

## 四、区块浏览器验证

通过 Sepolia Etherscan 和 RPC 调用验证了交易：

### Etherscan 查看

打开 https://sepolia.etherscan.io/tx/0x9ce6ce41d3ee8c6ffd7bce76d52a168f2cbd30bf6aed61c6494c6131e48cf9d8

可查看：交易状态、金额、Gas 消耗、区块信息等。

### RPC 原始查询

```bash
curl -X POST \
  -H "Content-Type: application/json" \
  --data '{
    "jsonrpc":"2.0",
    "method":"eth_getTransactionByHash",
    "params":["0x9ce6ce41d3ee8c6ffd7bce76d52a168f2cbd30bf6aed61c6494c6131e48cf9d8"],
    "id":1
  }' \
  https://sepolia.infura.io/v3/YOUR_KEY
```

返回的原始数据逐字段解读，加深了对交易结构的理解。

---

## 五、学习要点

### 学到的东西

1. **钱包 ≠ 地址**：钱包是管理私钥的工具，地址是链上身份的标识
2. **签名 ≠ 交易**：签名是本地用私钥对交易内容的加密盖章，交易是签名后广播上链
3. **Gas 是资源定价**：每步操作（转账/合约调用）都有固定的 Gas 成本，拥堵时 Gas Price 水涨船高
4. **EIP-1559**：Base Fee 销毁实现通缩，Priority Fee 激励验证者打包交易
5. **测试币靠社群**：公共 Faucet 门槛越来越高，社群互助是可靠来源
6. **区块浏览器是真相源**：MetaMask 显示的信息，可以在区块浏览器二次验证，避免被篡改

### 关键认知

> **Nonce = 0** 意味着这个钱包发出的第一笔交易，很有纪念意义 (´▽｀)

> **手续费 0.000032 ETH ≈ 0.00006 美元**（测试网），但在主网同样一笔交易可能花费几美元甚至几十美元——Gas 价格差上千倍。

---

## 六、下一步

- [ ] 发一笔低 Tip（0.1 Gwei）交易验证能否成功
- [ ] 用 Remix IDE 部署一个最小合约（Counter / Storage）
- [ ] 在区块浏览器中查看合约交互

---

*记录人：段宇轩*
*仓库：github.com/yogurt2333/ai-web3-school-cohort-0*
