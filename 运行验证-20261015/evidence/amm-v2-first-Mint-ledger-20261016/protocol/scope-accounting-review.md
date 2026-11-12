# 最早Mint单交易会计范围审阅

限定PASS。新scope与上阶段冻结的下一步原件逐字节一致，固定交易`0x4ada8c5018e158f6cd039bef1756533d43380780c21f348624d487fb2cc40e51`、块26195058、同一USDC/WETH池。scope SHA为`3ce8013e6e0a6908e02c7e85834ad46879113ae095008c11d99058aa8fd3be63`。选择发生在市场日志已取得之后，属于描述性首Mint选择，非按利润排序或前瞻样本外验证。

本轮足够且必要的会计边界如下：

- receipt/tx的hash、block、状态、From/To/value及log身份须绑定；API错误不填空或0。gas用实际receipt的gasUsed×effectiveGasPrice，由From支付。
- 顶层value、已记录native出入、退款及wrap/unwrap分腿记录；self及明确条件地址组内转账抵消。WETH解包与其ETH入账不能双计。提供商内转索引不冒充独立完整trace或余额快照。
- ERC20按topics/data原量解析；ERC721 Transfer不当ERC20。同金额同地址的合法重复付款不按金额合并，只按确切log身份去重。
- Mint得到LP权利不是额外现金收入；Burn取回资产包含本金和库存。已知同tx有Mint及Burn、其间无本池Swap，不能据Mint宣称持续持仓收费。feeTo当时状态UNKNOWN不妨碍核实际付款，但不能自动忽略可见协议铸份额。
- 其他池换币、借款或中间流转本金不是本池费用收入；需匹配偿还，剩余按地址和资产分别保留。未知内部债权或业务限制完整经济利润结论，不抹除已观察现金事实。
- From、目标合约、中间地址与最终受益地址分开。可显示明确列出地址的条件向量，不据此断言同现实主体或个人到账。
- 各币不直接相加；ETH/WETH若用数量平价须明示，不能称实际兑换。单笔gas不称全部经营成本，也不擅自扩钱包史补全年费用。

承认这笔历史现金事实不以完整私人bot、私人动机、未来OOS或全经营实体历史为门槛；任何正数亦不能升级成持续做市策略或未来复制优势。拿不到字段保留UNKNOWN，不换交易找赢家。

本轮0网络，等待root固定receipt/tx/native原件。实际model/effort为UNKNOWN，规则版本沿用；输入SHA与UTC见同名JSON。未执行来源源码、模型、回测、EVM、SDK、策略或交易。
