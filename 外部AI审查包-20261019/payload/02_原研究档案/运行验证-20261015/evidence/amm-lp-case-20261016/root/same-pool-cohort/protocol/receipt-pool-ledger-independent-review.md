# 群组receipt与pool账：限定层PASS

审阅UTC：2026-10-16T08:00:41.638039+00:00；实际model/effort UNKNOWN。规则PERMISSIONS-2026-10-14-v1、ROUTING-2026-10-13-v4。0联网，仅原件JSON/ABI/hex、整数/hash；无EVM、模型、回测、策略、安装、账户、交易或外发。

**与root receipt-verified-pool-ledger.json的pool本金、实际领取、分项费用及gas相符。通过receipt/事件/实际token层，不把尚待单独审阅的native或价格层混入。**

- 32份原receipt逐文件hash/长度及读取回执对应：27成功、5失败。receipt hash、区块、from/to、日志身份、实际gasUsed/effectiveGasPrice与保存普通交易索引吻合；失败5份logs均空。
- 新10NFT各page1/2及1338529旧分页复用，41条仓位事件按固定截止过滤，逐条与receipt topics/data/hash/height/logIndex匹配，无重复；11个累计liquidity均为0。旧1338529查询截止更晚，未把截止后记录混入。
- 全27笔成功交易只各服务一个不同NFT，逐NFT去重gas求和等于全局唯一交易求和：**4663905102987639 wei（0.004663905102987639 ETH）**。没有按同笔Increase/Decrease/Collect条数重复扣gas。
- 各Increase与实际pool Mint/入pool token Transfer一致；Decrease与对应非零pool Burn本金一致。三笔部分撤资随后Collect还触发Burn(0,0,0)更新费用；明确单列这些零Burn，不当第二次移除本金。
- 各Collect按实际pool Collect及pool→recipient token Transfer核量；recipient为owner时WETH/USDT直接到账，为NPM时USDT→owner及WETH Withdrawal一致。最终native→owner/退款的18笔历史记录另阶段审，不从Withdrawal直接冒称该层已全部闭合。
- NFT1319375最终领取交易`0xacf9b4e2c13fe77945f3bb7705001e61c637a12f4a6084baa0a562c811fc27f9`，NPM Collect预期减pool实际为**[0 WETH raw, 2 USDT raw]**。已采用实际pool/Transfer量，不回填事件或把0.000002 USDT舍入差当实收。
- 五失败nonce3/5/19/26/43均有实际gas，不能把请求value当本金损失；19/26可绑定目标NFT，3/5为其他池，43仍为路由器归属UNKNOWN，不把五费向每个仓位全扣。

此处liquidity归零不独立证明tokensOwed/storage残余严格零，正常分页与同提供商receipt也不是独立节点全链完备证明。实际领取减移除本金只是分项fee原量，不等于经济净利、样本外优势、私人策略公开或容量。

全部实际输入hash、逐NFT数量/费用、41事件及零Burn/舍入差详见同名JSON。价格选择/估值未在本文件审定；根文件未改。
