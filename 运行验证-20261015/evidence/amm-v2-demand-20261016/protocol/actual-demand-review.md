# 固定日实际交换需求独立审阅

限定PASS。独立读取三页原始返回、provider ABI及源码，核哈希/URL/状态、逐条解码和原量求和，未执行root辅助程序。0新增网络。

三页为1000/1000/840条，最后短页足以终止此提供商分页，无需第四页。2840条均在2026-10-15完整UTC日与固定块范围内，地址/结构有效、无重复。按ABI形状独立重算为1395 Sync、1379 Swap、7 Mint、9 Burn，以及50条尚未区分的Transfer/Approval同形状事件。1379 Swap属于1378个unique tx；逐条四原量、时间及indexed地址与root解码完全一致。

原量合计：USDC输入686511160099、输出623366576983；WETH输入263566511930682726460、输出287922929667070319212。这里不折美元、不相加为资本或收益、不推算手续费。82个sender、201个to只是地址数，不是独立人或客户数。

发现8条transactionIndex为`0x`，已原样列入JSON警告；未回填，排序采用block/globalLogIndex。提供商分页完结不等于独立全链无漏证明。Swap唯一对应实际ABI的3topic/4uint形状，返回topic全一致；没有计算Keccak或以SHA3代替。Transfer/Approval未强行按形状区分。

provider双大括号JSON安全解析后，主Pair合约正文仅经CRLF→LF及外沿strip，与固定GitHub主合约正文相同。原始整文件不相同，imports未全比对；Proxy0及编译参数为提供商声明，不是独立编译或历史runtime证明。目标日feeTo仍UNKNOWN，不能把全部0.3%当LP收入。

按块/log排序的首Mint为`0x4ada8c5018e158f6cd039bef1756533d43380780c21f348624d487fb2cc40e51`，log889；同一交易同一pair还存在Burn log929。因此只能说是该返回集合首个Mint，不能仅据此展示持续持仓，亦未核该交易全部业务或计算其利润。

结论只支持固定池/日、此提供商返回范围内实际交换需求存在；不是个人可复制盈利策略、已实现LP净利、预测优势或容量证明。UTC、全部真实输入SHA、逐项计数、首末Swap及警告见同名JSON。实际model/effort为UNKNOWN。
