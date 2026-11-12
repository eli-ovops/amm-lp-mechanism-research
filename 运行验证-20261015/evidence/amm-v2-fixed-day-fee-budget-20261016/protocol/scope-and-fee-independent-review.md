# 固定日输入与毛费用规则量独立审阅

限定PASS。本次先独立计算，未读取root结果。仅用冻结三页原logs、ABI与官方Pair文本；输入SHA/字节与scope核合，scope SHA为`3cab497d1f0efe700b0509d0d77fee21cff2fb3bc625fd4ef48655ef643642d7`。0网络、0外来代码执行。

2840条原日志均在固定2026-10-15 UTC日内，无重复log身份。Swap为ABI唯一“两indexed address、四uint256 data”形状，实际topic一致；独立取得1379条、1378个unique tx，未用SHA3代Keccak。

| 分币字段 | 原始整数合计 |
|---|---:|
| USDC输入 | 686511160099 |
| WETH输入 | 263566511930682726460 |
| USDC输出 | 623366576983 |
| WETH输出 | 287922929667070319212 |

对每币输入分别按3/1000保留精确有理数，不对每笔向上取整、不将两币加成美元：

- USDC规则量：**2059.533480297 USDC**（6位币种单位下的精确规则因子，可含小于一个raw的部分，不表示独立整数到账）。
- WETH规则量：**0.79069953579204817938 WETH**（18位币种单位下同理）。

实际分类：842条仅USDC输入且WETH输出；537条仅WETH输入，其中536条USDC输出、1条同币WETH输入/输出。双输入0、双输出0、USDC同币输入/输出0。特殊交易`0xda4aefb1e9fff14c003eb96974b292378002dcc30f40b6c3dbbf596bd662d5d6`报告WETH输入1013039117352057 raw、输出1010000000000000 raw，原样保留为同币回偿形态，不强称普通换币客户或确定某类借贷。4条Swap的transactionIndex为`0x`，保留不用，按block/globalLog排序；与先前全部事件8条同类警告范围不同。

**规则量不等于独立feeTransfer。** 源码的amountIn由执行后balance与先前reserve、输出额推导，可能包含较早转入的超额余额、捐赠或callback回偿，不保证全部是同交易新客户资金。约束使用`balance*1000−amountIn*3`，本次仅被动计算该有理数因子，不模拟成交、不运行源码、不据此确认可提取个人收入。

公开feeTo机制可能铸LP并稀释份额；本轮没有完整totalSupply、个人份额、历史收费状态、退出及全部成本，不能把全部规则量当LP可支配利润、个人收益率或容量。sender/to与unique tx也不是独立客户人数。不年化、不定价、不推Gerko财富目标。

逐笔1379条独立解码与各笔精确分数见`independently-decoded-fixed-day-Swaps.json`；主JSON包含文件SHA、UTC、特殊行、完整相关源码片段及全部输入指纹。保留单提供商返回范围，不冒充独立归档无漏。实际model/effort为UNKNOWN。
