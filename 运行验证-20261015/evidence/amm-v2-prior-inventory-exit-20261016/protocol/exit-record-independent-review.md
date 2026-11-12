# 固定退出及最小LP来源范围独立审阅

限定PASS。退出tx/receipt成功，9条日志的公共身份对应；其中本池5条与既存同日page1原件逐字段一致。From为`0xc91a369b080638a1e1d0cfc81f3c420414e66aee`，To为官方Router `0x7a25…488d`，顶层value为0。

- LP从该地址进入pair并销毁：443621122331 raw。
- Burn报告及实际USDC Transfer：62245542 raw，经router回该地址。
- Burn报告及实际WETH Transfer：25749446682452769 raw，经router Withdrawal后，已记录native两腿分别WETH→router→该地址，原量一致。
- 实际gas：`209164 × 2082951190 = 435678402705160 wei`。

解包和中间native只计一次。退出所得含本金/库存，未取得建仓资金之前不能把返还减gas称利润。另有向其他地址铸LP的事件已保留，不当调用者奖励，不忽略费用份额机制。

新的最小来源scope只查同owner、同LP，从已核Factory创建块10008355到固定退出块26194229的两方向Transfer，条件与分页合理，不是全钱包史。现已保存两方向原页各成功返回1条，短页结束：唯一入为零地址铸给owner，唯一出为此次退出同量LP，净事件余额归零。原量、topics、hash、block和退出日志一致；不升级为独立归档完整性或现实主体所有权证明。

唯一具体建仓线索为`0xe465cfe40b621da03bd4848311873cfb810b5dbaa8a5aeec0b6ada650e58b6c5`，2024-08-06T10:52:11 UTC。它足以定位下一项必要建仓原件问题，尚不证明建仓输入、成本、费用收入或完整生命周期利润；本审阅未读取该交易的收据。

native索引行本身未含txhash/blockHash，绑定来自已存精确txhash查询URL及对应block/time/receipt原量，不回填缺字段。全部五份当前原响应hash/字节与回执核合；其余来源、UTC、逐笔Transfer与两方向完整返回见同名JSON。

0网络、模型、回测、来源代码/策略/EVM/SDK执行或交易。实际model/effort为UNKNOWN。不新增完整私人bot或未来盈利门槛，也不换候选。
