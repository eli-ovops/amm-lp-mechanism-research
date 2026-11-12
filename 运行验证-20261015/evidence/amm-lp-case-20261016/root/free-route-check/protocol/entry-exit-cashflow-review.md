# NFT1338529进出金：实际两币收支通过，总盈利未证

审阅UTC：2026-10-16T07:18:05.196882+00:00；实际model/effort UNKNOWN。规则PERMISSIONS-2026-10-14-v1、ROUTING-2026-10-13-v4。只被动读已保存原件、解码ABI/hex和整数/Decimal算术；额外一次精确Swap签名公开GET。无EVM、eth_call、trace、模拟、模型、回测、策略、安装、账户、交易或外发。

**限定现金流层PASS：mint/exit同发起人、同NPM，两币实际路径与该NFT事件相符。实收减移除本金可分出两币手续费；没有统一估值及全部归属成本，不称总盈利、ROI或持币基准优势。**

## 原件状态与身份

保存回执的HTTP200、原字节长度及SHA256均逐项复核。两份带page/offset的native旧原件实际为status0/NOTOK、result空字符串，保留坏原件，**没有当零流量**。后续明确txhash-only接口的两份新native原件status1/OK，各返回两条成功已记录内部流；不是新trace执行或独立全节点证明。

两笔receipt分别6/8条日志，均status0x1；transaction与receipt的hash、block/hash、index、from/to一致。from均`0xeeded7912e2f4aac5781e8befeab728f715314f6`，to均NPM C364…；日志身份一致、无重复/removed。仅见本NFT1338529铸造，Increase/Decrease/Collect均是该id。静态multicall解析为建仓2子调用、退出4子调用，退出前两个仓位参数均id1338529，未见额外NFT仓位操作。

## 实际入金、收回本金及手续费

按原token单位及此前WETH18/USDT6小数口径：

| 项目 | WETH/ETH数量 | USDT数量 |
|---|---:|---:|
| 实际建仓投入 | 634.074933604560966689 | 1,353,746.011618 |
| 退出移除本金（pool Burn = NPM Decrease） | 90.428962086344584172 | 2,449,397.185410 |
| 实际收款（pool→NPM） | 102.939699277107850163 | 2,475,946.784070 |
| 实收减移除本金，分项手续费 | **12.510737190763265991** | **26,549.598660** |

两币本金原量为90428962086344584172、2449397185410；实际收款原量102939699277107850163、2475946784070。完整receipt的pool Burn数据精确等于Decrease（全初始liquidity590034172147953513），Collect预期值也恰等于pool实际两条Transfer，**本笔没有观察到舍入差**。分项手续费差额以所读NFT生命周期及官方NPM本金/fee会计为前提，不将总Collect当手续费。

入场transaction.value为634.074941999687971482 ETH；已记录manager→原EOA退款0.000008395127004793 ETH，减后精确等于实际包装WETH并付pool数量。USDT实际EOA→pool原量1353746011618。desired或value均不能替代实际投入，退款不是收入。

退出transaction.value=0。pool实际USDT→NPM后，NPM同量全付原EOA；pool实际WETH→NPM后，Withdrawal原量与已记录WETH→NPM native、NPM→EOA native均为102939699277107850163。只有一次经济收款，不能把中间两次USDT转移、WETH及其解包ETH重复算收入。

## 实际gas及剩余费用范围

| 交易 | gasUsed | effectiveGasPrice（wei） | 实际gas ETH |
|---|---:|---:|---:|
| mint | 396666 | 92936821 | 0.000036864877038786 |
| exit | 233704 | 6721593030 | 0.001570863177483120 |
| 两笔合计 | — | — | **0.001607728054521906** |

使用实际receipt effectiveGasPrice，不用gasLimit/maxFee上限；两笔完整gas均计入，不任意分摊。此范围原EOA资产数量变化为：

- ETH净减少 **531.136842055507638432**（实际投入减退出，并已扣两gas）。
- USDT净增加 **1,122,200.772452**。

方向相反的库存变化不能相加直接称利润；这里未进行市场估值，也未证明实际卖出剩余库存、美元ROI或相对持有收益。

mint nonce59、exit nonce60相邻：同一EOA两者之间没有另一个已上链出站nonce，不虚构中间approval或失败费。仍未核建仓前USDT授权/设立、此前或之后可归属尝试、其他执行者费用、离线维护及税费；这些应按限定策略归属，而非要求全实体多年经营账。未直接读取历史tokensOwed/钱包全部余额，不宣称所有残余或全账户经济状态严格归零。

## 给历史池价取证的Swap接口

唯一新增精确签名GET为`Swap(address,address,int256,int256,uint160,uint128,int24)`，4byte唯一text_signature匹配topic0：

`0xc42079f94a6350d7e6235f29174924f928cc2ac818eb64fed8004e115fbcca67`

此为辅助签名映射，非本地Keccak计算或部署证明。已存官方core Pool.sol 743—751行先写slot0.sqrtPriceX96/tick，786行以相同state字段发Swap。因此按区块/logIndex找目标动作之前最近成功Swap，可取得该swap完成后的历史池状态；不是NFT实际售出价格、可立即成交报价或TWAP，也不能在未核完整有序事件时断言中间没有其他状态变化。

该状态可用于明确标注假设的历史估值，不是执行交易、EVM或回测，更不能将按此价估算的库存价值说成已兑现收入。本审阅不生成价格或收益路径，根另取历史原件。

原件URL/UTC/HTTP/hash、两笔静态调用字段、实际流量及全部输入指纹见`entry-exit-cashflow-review.json`；根文件与旧失败原件均未改。
