# NFT1338529生命周期事件：返回集合限定PASS

审阅UTC：2026-10-16T07:15:00.265156+00:00；实际model/effort UNKNOWN。规则PERMISSIONS-2026-10-14-v1、ROUTING-2026-10-13-v4。仅新增两次精确4byte签名GET，其他为已保存原件、官方源码的被动解析；无EVM、eth_call、trace、模拟、模型、回测、策略或交易。

**三条仓位事件、一条NFT铸造的顺序及数量对齐；所读事件累计liquidity归零。Collect含已移除本金，实际收款及费用仍待退出原件核验，不给盈利结论。**

## 精确topic及字段

精确text_signature各唯一匹配，且与固定官方接口及观察日志一致：

| 签名 | topic0 |
|---|---|
| DecreaseLiquidity(uint256,uint128,uint256,uint256) | 0x26f6a048ee9138f2c0ce266f322cb99228e8d619ae2bff30c67f8dcf9d2377b4 |
| Collect(uint256,address,uint256,uint256) | 0x40d0efd1a53d60ecbf40971b9daf7dc90178c3aadc7aab1765632738fa8b8f01 |

两者tokenId均topic1。Decrease data顺序为liquidity、amount0、amount1；Collect为recipient、amount0、amount1。签名索引是辅助映射，不证明部署、首次公开时点或链数据完整性；未安装/实现hash库，Increase仍复用已核mint receipt topic。

## 逐原件核对

四页日志原件的HTTP200、API status1/OK、长度及SHA256与根回执相符。仓位查询为NPM地址+topic1=id，NFT查询另限定Transfer topic0 AND topic3=id；均自块0至26201365，截止2026-10-16T00:00:00Z以前，page2正常成功空。保存的截止前块26201364时间为1792108799，查询含其后一块；三条实际记录均早于截止。

| UTC/事件 | liquidity变动 | amount0原量 | amount1原量 |
|---|---:|---:|---:|
| 2026-07-22 04:20:59 Increase | +590034172147953513 | 634074933604560966689 | 1353746011618 |
| 2026-08-19 16:06:59 Decrease | −590034172147953513 | 90428962086344584172 | 2449397185410 |
| 同笔Collect | 无变动 | 102939699277107850163 | 2475946784070 |

Decrease与Collect均为交易`0x7aef61fb075e5dc66e034a01fa64f2e38c9ad1b6e0cf645f435427ec9e3acda9`、块25790244；全局logIndex1065与1069，顺序明确。Collect recipient是**NPM自身C364…**，不是EOA。data为三个完整word、liquidity符合uint128、recipient符合address；tx/block hash及索引身份对应，重复0、removed记录0、transactionIndex空hex0。

NFT Transfer仅最初Null→eeded…314f6铸造，核心身份与已核mint receipt一致；Increase也逐字段匹配该receipt。日志接口Transfer data为原始空字符串，而receipt为`0x`，二者均表示零字节；原件不改、不补。所读截止范围无后续NFT转移/burn，但不冒称直接读取了当前owner。

## 归零、本金与收款边界

在所读完整分页返回及官方事件语义前提下，+L−L=0，支持本NFT名义流动性已全移除；这不是positions/storage实读，也不证明tokensOwed已清零。NFT不必随liquidity归零自动burn，不能从NFT仍存在推仓位仍有liquidity。

固定官方NPM源码273行pool.burn返回本金；281—298行将该本金与累计fee一起记入tokensOwed，303行扣liquidity。因此后续Collect是从本金/手续费合并应领余额提取，不能将其总额称手续费收入。两事件金额差仅作原量算术：amount0差12510737190763265991、amount1差26549598660；暂不把差额升级成独立核实的实收手续费或盈利。

源码361—367行取得pool.collect实际返回，369—373行按预期可领量扣减并发Collect；舍入可使实际转账略少。接口也明确警示这一点。仍须对退出receipt核pool→NPM实际两token、unwrap/sweep→受益人及gas/native退款，不得把Collect给NPM当作个人已到账或重复计算WETH/ETH。

目前未核实际退出交易收据、完整资金路径、费用或剩余应领余额，也未比较价格或计算收益。单提供商返回与正常分页不是独立全链完备证明；公开NFT配置也不等于私人择时/退出策略公开。等待根退出原件后再审现金流。

全部原始签名回应、实际URL/UTC/headers/hash及本次真实输入指纹见同名JSON与本目录`*-signature-read-receipt.json`。未改根或其他Owner文件，无安装、账户、凭证、付款、交易/广播或外发。
