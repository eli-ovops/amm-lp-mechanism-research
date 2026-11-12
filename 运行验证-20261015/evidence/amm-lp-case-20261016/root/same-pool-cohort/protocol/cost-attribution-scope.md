# 61笔owner出站用途与费用归属范围

审阅UTC：2026-10-16T07:55:13.611314+00:00；实际model/effort UNKNOWN。规则PERMISSIONS-2026-10-14-v1、ROUTING-2026-10-13-v4。0联网，仅已存索引、calldata、receipt/源码与整数/hash被动核对；未执行EVM、模型、回测、策略或交易。

**用途与归属清单层PASS，不是全部成本原账或盈利审定。** 88条普通交易中61笔为owner发起，nonce0—60连续。逐笔用途、目标、请求参数、索引状态及gas都保存在JSON；未知经济用途没有凭时间顺序补造。

## 直接绑定与失败归属

| nonce | 实际输入/索引支持 | 归属及索引gas ETH |
|---:|---|---|
| 19 | increaseLiquidity，tokenId1319375，失败 | 目标NFT明确；0.000014229341478144 |
| 26 | increaseLiquidity，tokenId1324363，失败 | 目标NFT明确；0.000017883518723154 |
| 43 | 4c82…execute批量调用，commands=0b0000001004，失败 | 无外层NFT id；0.000118749652628676，不擅自归1335613 |
| 3 | 另一币对/fee500的mint尝试，失败 | 无成功NFT，不归目标池；0.000068719656502053 |
| 5 | NFT1307592的decrease/collect等，失败 | 已排除的另一pool，不归目标池；0.000079430396989800 |

nonce43请求value375 ETH是失败调用的value，**不是375 ETH本金损失**。其外层没有NFT id参数；未核路由器命令实现与实际receipt流量，不能因之后nonce45创建1335613就说这笔失败专门服务它。命令有多个字节也不等于服务多个NFT。

现有33笔直调NPM中，29笔显式绑定目标11NFT（包括19/26失败），另4笔为其他池链条。没有一笔显式涉及超过一个不同NFT id；同笔decrease+collect+辅助unwrap/sweep通常重复同一id，不能按子调用数重复扣整笔gas。

## 共享、准备与未知

- WETH/USDT审批共8笔，其他代币审批7笔；可按calldata确认token/spender/请求量，不能证明只供某个NFT使用。全部扣给一个范围是可明确声明的保守分配，不能在群组汇总时重复向每个仓位全扣。
- 未独立取得实际资金路径的路由器交易8笔，保留为共享准备/换币用途UNKNOWN；包含失败43。仅索引函数名或请求参数不能证明实际兑换量、利润或独享归属。
- nonce58已由此前receipt/native核实际125,221.177122 USDT→64.581943113032031780 ETH，单列已确认准备兑换。其库存价格变化不是LP手续费；前置资金组与LP阶段不同起点，不能相加。是否只为随后NFT而做的私人目的未因此证实。
- nonce32为WETH withdraw请求，是包装形式转换，不能当收入；另有2笔代币transfer请求和1笔普通native转账，不把转账本金当费用或LP亏损。实际转账及角色仍须receipt/上下文归属。

## 费用证据等级

下表gas均为保存索引中的gasUsed×gasPrice，含失败，不用gasLimit/maxFee。它不是61笔都已独立逐receipt核effectiveGasPrice的声明；根后续取得对应receipt时应确认实际状态与费用。此前已核个别receipt的确定费用不受影响。

仅应把可直接绑定的目标NFT操作/失败费计入相应范围；共享审批、准备换币与未知路由费应单列、说明分配原则。没有全实体多年成本要求，但融资、其他账户、离线维护/税、无法关联的尝试仍不能冒称已全部核清。不能把UNKNOWN记零，亦不能把所有61笔不相关费用都必然归本池。

所有原始输入路径/bytes/SHA256及61笔完整txhash、请求字段见`cost-attribution-scope.json`。不评分、不回测、不推私人操作政策；根及其他Owner文件未改。

## 全61笔清单

目标别名和用途字段仅为阅读简化；路由器用途UNKNOWN的标记不代表已核合约部署或私人意图。各完整目标地址及索引原函数名保存在JSON。

- D1: `0xa0b86991c6218b36c1d19d4a2e9eb0ce3606eb48`
- D2: `0x3b0221b59bfa5dec15e028600b0ca2b6af03d5b7`
- D3: `0xc36442b4a4522e871399cd717abdd847ab11fe88`
- D4: `0xc02aaa39b223fe8d0a0e5c4f27ead9083c756cc2`
- D5: `0xdac17f958d2ee523a2206206994597c13d831ec7`
- D6: `0x4c82d1fbfe28c977cbb58d8c7ff8fcf9f70a2cca`
- D7: `0x2260fac5e5542a773aa44fbcfedf7c193bc2c599`
- D8: `0x68b3465833fb72a70ecdf485e0e4c7bd8665fc45`


| nonce | status | target | purpose | explicit NFT ids | indexed gas ETH |
|---:|---|---|---|---|---:|
| 0 | success | D1 | token transfer request |  | 0.000013199989515068 |
| 1 | success | D2 | plain native transfer |  | 0.000006005145909 |
| 2 | success | D1 | token approve request |  | 0.000008501638446098 |
| 3 | FAILED | D3 | mint; refund helper |  | 0.000068719656502053 |
| 4 | success | D3 | mint #1307592; refund helper | 1307592 | 0.00007028865898281 |
| 5 | FAILED | D3 | decreaseLiquidity #1307592; collect #1307592; unwrap helper; sweep helper | 1307592 | 0.0000794303969898 |
| 6 | success | D3 | decreaseLiquidity #1307592; collect #1307592; unwrap helper; sweep helper | 1307592 | 0.00006643981732909 |
| 7 | success | D1 | token transfer request |  | 0.000014497438314384 |
| 8 | success | D4 | token approve request |  | 0.00000349174110796 |
| 9 | success | D5 | token approve request |  | 0.000004684724607249 |
| 10 | success | D1 | token approve request |  | 0.000004355625056846 |
| 11 | success | D1 | token approve request |  | 0.000002871993342294 |
| 12 | success | D1 | token approve request |  | 0.000002828339765028 |
| 13 | success | D1 | token approve request |  | 0.00000289907940816 |
| 14 | success | D4 | token approve request |  | 0.000003125276768592 |
| 15 | success | D6 | router execute batch (indexed function label; internal economic purpose UNKNOWN) |  | 0.000016324984473026 |
| 16 | success | D6 | router execute batch (indexed function label; internal economic purpose UNKNOWN) |  | 0.00004348544529428 |
| 17 | success | D3 | mint #1319375 | 1319375 | 0.000029280635503185 |
| 18 | success | D3 | decreaseLiquidity #1319375; collect #1319375 | 1319375 | 0.000013416237134601 |
| 19 | FAILED | D3 | increaseLiquidity #1319375 | 1319375 | 0.000014229341478144 |
| 20 | success | D3 | increaseLiquidity #1319375 | 1319375 | 0.00001647632775455 |
| 21 | success | D3 | decreaseLiquidity #1319375; collect #1319375; unwrap helper; sweep helper | 1319375 | 0.000031097804015875 |
| 22 | success | D3 | mint #1321691 | 1321691 | 0.000474555160836948 |
| 23 | success | D3 | decreaseLiquidity #1321691; collect #1321691 | 1321691 | 0.000328867622473772 |
| 24 | success | D3 | decreaseLiquidity #1321691; collect #1321691; unwrap helper; sweep helper | 1321691 | 0.000030891671284101 |
| 25 | success | D3 | mint #1324363 | 1324363 | 0.00003986328134866 |
| 26 | FAILED | D3 | increaseLiquidity #1324363 | 1324363 | 0.000017883518723154 |
| 27 | success | D3 | increaseLiquidity #1324363 | 1324363 | 0.000020277206347284 |
| 28 | success | D3 | decreaseLiquidity #1324363; collect #1324363 | 1324363 | 0.000018935879590133 |
| 29 | success | D3 | decreaseLiquidity #1324363; collect #1324363 | 1324363 | 0.000015311261964229 |
| 30 | success | D4 | token approve request |  | 0.000002130191499556 |
| 31 | success | D6 | router execute batch (indexed function label; internal economic purpose UNKNOWN) |  | 0.0000307521825264 |
| 32 | success | D4 | WETH withdraw request |  | 0.00000298426820124 |
| 33 | success | D6 | router execute batch (indexed function label; internal economic purpose UNKNOWN) |  | 0.00003939206508675 |
| 34 | success | D3 | mint #1334916; refund helper | 1334916 | 0.00002338049816718 |
| 35 | success | D3 | decreaseLiquidity #1334916; collect #1334916; unwrap helper; sweep helper | 1334916 | 0.000058835843861184 |
| 36 | success | D7 | token approve request |  | 0.000022970503876992 |
| 37 | success | D7 | token approve request |  | 0.000013751909355224 |
| 38 | success | D6 | router execute batch (indexed function label; internal economic purpose UNKNOWN) |  | 0.00023755426586304 |
| 39 | success | D3 | mint #1335240; refund helper | 1335240 | 0.00013379597244408 |
| 40 | success | D3 | decreaseLiquidity #1335240; collect #1335240; unwrap helper; sweep helper | 1335240 | 0.000392122139728088 |
| 41 | success | D3 | mint #1335246; refund helper | 1335246 | 0.000813883330331176 |
| 42 | success | D3 | decreaseLiquidity #1335246; collect #1335246; unwrap helper; sweep helper | 1335246 | 0.000086881324456566 |
| 43 | FAILED | D6 | router execute batch (indexed function label; internal economic purpose UNKNOWN) |  | 0.000118749652628676 |
| 44 | success | D6 | router execute batch (indexed function label; internal economic purpose UNKNOWN) |  | 0.000284526620236305 |
| 45 | success | D3 | mint #1335613; refund helper | 1335613 | 0.000101320118959584 |
| 46 | success | D3 | decreaseLiquidity #1335613; collect #1335613; unwrap helper; sweep helper | 1335613 | 0.00012624887458 |
| 47 | success | D5 | token approve request |  | 0.000004506218852667 |
| 48 | success | D3 | mint #1336197; refund helper | 1336197 | 0.000035504749943588 |
| 49 | success | D3 | decreaseLiquidity #1336197; collect #1336197; unwrap helper; sweep helper | 1336197 | 0.000016368339543612 |
| 50 | success | D3 | mint #1336999; refund helper | 1336999 | 0.00002960610505293 |
| 51 | success | D3 | decreaseLiquidity #1336999; collect #1336999; unwrap helper; sweep helper | 1336999 | 0.000052088328026724 |
| 52 | success | D5 | token approve request |  | 0.000012897041466582 |
| 53 | success | D5 | token approve request |  | 0.00000546875381826 |
| 54 | success | D5 | token approve request |  | 0.000011158917280686 |
| 55 | success | D8 | router multicall(deadline,bytes[]) (indexed label) |  | 0.000039949397265948 |
| 56 | success | D3 | mint #1338391; refund helper | 1338391 | 0.000144523793373264 |
| 57 | success | D3 | decreaseLiquidity #1338391; collect #1338391; unwrap helper; sweep helper | 1338391 | 0.000022644541744419 |
| 58 | success | D8 | verified actual preparation swap USDT -> ETH |  | 0.00001171412885881 |
| 59 | success | D3 | mint #1338529; refund helper | 1338529 | 0.000036864877038786 |
| 60 | success | D3 | decreaseLiquidity #1338529; collect #1338529; unwrap helper; sweep helper | 1338529 | 0.00157086317748312 |
