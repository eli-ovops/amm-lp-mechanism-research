# 第二固定候选退出原件独立审阅

限定PASS。三原件hash/字节与回执一致，交易成功、顶层value为0，hash/block/时间对应固定候选。**真实receipt为12条日志，log212—223；任务文字13条是计数描述误差，root摘要已正确记12。** 全部日志已解码或保留未知原始字段，其中5条Transfer；本池emitter的6条与既存固定日原页逐字段一致。

| 项目 | 实际原量 |
|---|---:|
| 持LP地址向pair转入并销毁 | 62282388937 LP raw |
| USDC返还 | 8788683 raw |
| WETH返还并Withdrawal | 3595855684063142 raw |
| gasUsed × effectiveGasPrice | 247672 × 2560659911 |
| 实际gas | 634203761477192 wei |

付款gas的From为`0xa8e9e4d0f213736b463ebeff5b92dc8ef873f772`；To、实际LP发送者及Burn接收者为`0xbaf0b66c0add5bb02fef5b3210275195313fab9c`。USDC和WETH先进后者，随后WETH解包。native索引仅有WETH→后者这一条，金额与Withdrawal相同；没有后者→From的已记录付款，不能写成EOA到账或认定两个地址同现实所有人。

USDC/WETH返还含本金与当前库存，本阶段不称利润。LP Approval、转入pair和销毁不是三次本金成本；WETH Transfer、Withdrawal和ETH入款也不重复计收入。零地址向`f38521…5f85`另铸47665969295 raw LP，独立保留，不混为用户份额或收入。两个外层合约自定义事件无已核ABI，保留原字段，不据形状猜完整业务、受益关系或分配路径。

native行本身没有txhash/blockHash，仅按保存的精确txhash查询URL与block/time/原量绑定，不回填字段。单提供商事件和索引不是独立完整余额或归档证明；历史取得成本及最终受益分配仍UNKNOWN，但不因此否认退出现金事实，也不新增私人bot门槛。

一次自写本地断言最初误把两种底层代币emitter也计作pair日志，预期写8，检查在输出前停止；实际两组原件均为6条pair日志且相符。未改任何原件、未增加GET。完整12条事件、来源SHA/UTC、地址分离向量及此修正记录见同名JSON。

本任务未读取后续LP历史或建仓数据。0网络、模型、回测、来源代码/策略/EVM/SDK执行或交易，实际model/effort为UNKNOWN。
