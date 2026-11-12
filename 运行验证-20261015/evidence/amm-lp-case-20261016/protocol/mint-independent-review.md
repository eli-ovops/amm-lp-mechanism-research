# NFT1338529 mint 独立本地静态审阅

结论：这笔原HTML支持一次真实成功建仓；根派生JSON的ABI、币对/区间、实际注资、NFT和pool日志、gas及退款算术对齐，未见改变该建仓结论的实质差错。**不能由此证明已收手续费、已盈利、已完整退出或完整后续历史。**

本次读取UTC：2026-10-16T04:07:32.751104+00:00。仅本地文本/ABI数据解码、Decimal算术、SHA256；未联网，未执行下载代码、EVM、模型、策略或回测。actualmodel/effort UNKNOWN。未修改root。

## 原始交易与ABI

原交易 [0xc7b663a1635627a529e6536417f6225a66278070b5ee108de442a634aa3fc8cc](https://etherscan.io/tx/0xc7b663a1635627a529e6536417f6225a66278070b5ee108de442a634aa3fc8cc) 在原HTML标Success，block25585845，2026-07-22T04:20:59Z，From `0xeedeD7912e2F4AaC5781e8bEfeAb728f715314F6`，To NPM `0xC36442b4a4522E871399CD717aBDD847Ab11FE88`，nonce59。

我从HTML原始 `0xac9650d8` calldata独立按ABI动态bytes[]偏移解码，确认两子调用：356bytes `0x88316456` mint及4bytes `0x12210e8a`，两段完整hex与根JSON逐字节一致；非执行调用。mint11字段全部与根JSON一致：token0=WETH(C02a…Cc2)，token1=USDT(dAC1…1ec7)，fee3000（1e6单位下0.30%）、ticks[-201720,-199680]；recipient与From相同；deadline1784695217即2026-07-22T04:40:17Z，晚于交易时间。

按WETH18、USDT6的币种小数假设，`1.0001^tick ×10^12`静态换算得到约1737.[REDACTED_PHONE]—2130.30288766064 USDT/WETH，与派生JSON精度范围一致。该换算不是交易执行或收益路径；本次未独立链读目标token decimals、pool fee或部署bytecode。

## 资金与事件交叉核对

| 项目 | 原HTML/算术核验 |
|---|---|
| msg.value | 634.074941999687971482 ETH |
| 实际包装并付pool的WETH | 634.074933604560966689 WETH（634074933604560966689最小单位） |
| 实际由From转给pool的USDT | 1,353,746.011618 USDT（1353746011618最小单位） |
| ETH退款给From | 0.000008395127004793 ETH |
| 流动性 | 590034172147953513 |
| pool收款和Mint来源 | 0x4e68Ccd3E89f51C3074ca5072bbAC773960dFa36 |
| NFT | NPM的ERC721 Transfer由Null铸给From，tokenId1338529；同NPM IncreaseLiquidity的tokenId/流动性/amount0/1吻合 |

WETH Deposit/Transfer、USDT Transfer、pool Mint及NPM IncreaseLiquidity中的实际amount0/amount1逐项一致。pool Mint的owner为NPM，这是core聚合position拥有者；ERC721的初始持有人为From，二者不矛盾，不能将pool owner字段误读成个人EOA。这里证明的是铸造时NFT归属，不能仅凭该事件宣称后续当前owner未变。

`msg.value − refund = 634.074933604560966689 ETH`，精确等于包装/付入pool的WETH。退款是未使用本金，**不是手续费收入或投资收益**。实际两token数量均不超过amountDesired且达到amountMin；USDT实际amount与desired相等，WETH略小，符合建仓使用量与退款。

## gas与余额口径

原HTML gasUsed396666、页面实际Gas Price0.092936821Gwei：相乘为 **0.000036864877038786 ETH**，与页面Transaction Fee及根JSON精确一致。不能用gasLimit418301或1559 maxFee0.101535335当实际gas，也不把burnt fee、tip或txn savings再次加扣。

该单笔From的ETH净付出（原值－退款＋gas）为634.074970469438005475ETH，另付上述USDT。NPM→WETH包装转账和NPM→pool的WETH Transfer是同一资金路径的两个环节，不能双计本金；NFT Transfer和IncreaseLiquidity也不是额外资金入账。原HTML美元价格展示不统一且可能为页面读取时估值，不用于历史美元成本/ROI。

## 结论边界

1. 该笔只有建仓与退款证据，没有后续Decrease/Collect/实际退出到账/剩余liquidity与tokensOwed数据；未知不能记零，不能推算手续费或净收益。Collect若以后取得，仍须从其中拆本金及实际付费。
2. NFT创建的币对/fee/区间在上链时公开，并约束其后公开AMM规则执行；它不证明创建前择币、择时、资本规模、退出/对冲/再平衡策略事前公开或预锁，也不是私人寻单程序的源码证据。
3. 本笔mint成功不足以证明完整账户/NFT历史、连续盈利或扣费alpha；已知后续具体资源403和根报告的Blockscout正对照403只说明原件读取受阻，不能推断链上没有后续事件，也不授权绕过限制。
4. pool身份此处由收款地址和receipt Mint/参数相互吻合支撑；未独立核Factory.getPool、pool不可变字段或目标字节码。不得把这项静态对应扩大成独立合约部署审计。

## 输入指纹

- candidate1338529-mint.html：SHA256 `5d18049b26201112446df482221e974627af41533a2e3b9d85a7d5269b189941`；296219 bytes。
- candidate1338529-static-mint-audit.json：SHA256 `065ef23ae549ef47519d747244f2fd45ed3f03036c8023f53fcaf2b368f51c0c`；2686 bytes。
