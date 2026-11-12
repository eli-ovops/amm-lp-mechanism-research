# NFT1338529：mint原件与仓位事件接口核验

审阅UTC：2026-10-16T07:11:18.570779+00:00；实际model/effort UNKNOWN。沿用PERMISSIONS-2026-10-14-v1、ROUTING-2026-10-13-v4。本分支只新增一次官方GitHub接口源码GET，其余均本地原件被动解析；无EVM、eth_call、trace、模拟、模型、回测、策略或交易。

**限定层PASS：新的历史receipt与旧HTML/静态mint审阅支持同一次真实成功建仓，金额及实际gas一致；没有完整生命周期或盈利证据。**

## 新receipt与旧证据

原件SHA256 `46db402f2a4447ac9193e2629cd31886c73eeacd2ce3122ae4de95d258d542a9`，5095字节；根保存的HTTP200及读取回执hash/长度相符。交易`0xc7b663a1635627a529e6536417f6225a66278070b5ee108de442a634aa3fc8cc`，status0x1、区块25585845、日志时间2026-07-22T04:20:59Z、From为eeded…314f6、To为NPM `0xc36442b4a4522e871399cd717abdd847ab11fe88`，与旧证据一致。

6条日志均tx/block身份一致、removed=false、logIndex不重复。NPM唯一Null→初始持有人ERC721 Transfer铸出tokenId1338529；同NPM唯一IncreaseLiquidity中tokenId与下表相符。pool Mint、WETH包装/付pool、USDT持有人付pool逐项对应：

| 实际项目 | 原量 |
|---|---:|
| liquidity | 590034172147953513 |
| token0/WETH实际投入 | 634074933604560966689 |
| token1/USDT实际投入 | 1353746011618 |
| gasUsed | 396666 |
| effectiveGasPrice | 92936821 wei |
| gasUsed×effectiveGasPrice | 36864877038786 wei = 0.000036864877038786 ETH |

pool为`0x4e68ccd3e89f51c3074ca5072bbac773960dfa36`；pool Mint owner字段为NPM，不是持有人。按旧证据采用的WETH18/USDT6小数假设，上述为634.074933604560966689 WETH及1,353,746.011618 USDT。WETH实际投入略小于amount0Desired=634074941999687971482，不能混用desired；USDT实际投入恰等于desired。新receipt并未再次读取token decimals。

旧HTML的`data-gas`及`data-txfee`元素内数字有`<b>.</b>`标签，静态去标签后分别是0.092936821 Gwei与0.000036864877038786 ETH，与新receipt一致；直接字符串探针不命中并非原件缺值。

新receipt不含完整calldata、msg.value和internal退款，不能称它单独重新证明旧HTML的msg.value/退款。此前HTML/audit保留的退款0.000008395127004793 ETH是未用本金，非收入。旧HTML没有新receipt完整blockHash字符串，因此新blockHash不冒充已与旧HTML独立匹配。新提供者数据与旧发布页面的对应也不是独立全节点证明。

## 固定官方接口

复用已存v1.0.0 annotated tag链：tag对象268ceeba9686544f90db2593e700c59bf56971f2 → commit `464a8a49611272f7349c970e0fadb7ec1d3c1086`。tagger日期2021-05-04仅为Git元数据，不独自证明精确首次公开时点。

本次唯一GET取得[固定INonfungiblePositionManager.sol](https://github.com/Uniswap/v3-periphery/blob/464a8a49611272f7349c970e0fadb7ec1d3c1086/contracts/interfaces/INonfungiblePositionManager.sol)，blob `023b266136d9546787b45be41cfaf6d306175180`；安全解码并核Git blob SHA-1，接口SPDX为GPL-2.0-or-later。真实URL、UTC、HTTP原回应及hash见本目录回执。

| 事件 | indexed | data顺序 |
|---|---|---|
| IncreaseLiquidity | uint256 tokenId | uint128 liquidity、uint256 amount0、uint256 amount1 |
| DecreaseLiquidity | uint256 tokenId | uint128 liquidity、uint256 amount0、uint256 amount1 |
| Collect | uint256 tokenId | address recipient、uint256 amount0、uint256 amount1 |

三者tokenId都在topic1，所以限定NPM emitter、topic1=id可取得这三类的返回记录，再按topic0分类并核data形状；不能把topic1-only所有命中都自动当其中一类。mint同时触发IncreaseLiquidity，已观察topic0为`0x3067048beee31b25b2f1681f88dac838c8bba36af25bfb2b7cf7473a5847e35f`。未外查另外两个topic，也未自行安装/实现hash库。

ERC721 Transfer的tokenId在**topic3**，须另按同NPM地址、Transfer topic0与topic3=id查询，才包含返回范围内mint/转移/burn；不能将topic1=id查询当完整所有权变化。id的32字节word为`0x0000000000000000000000000000000000000000000000000000000000146ca1`。

Collect金额可能含已减少的本金，不能全当手续费。接口明确说明其报告金额因舍入可能不与实际转账完全一致，后续须对照receipt实际token/native路径；Decrease是记入可领金额，不等于外部已到账。

## 部署来源与边界

旧官方网页原件`protocol/official-web-responses.json`中Ethereum Deployments表L121明确将C364…列为NonfungiblePositionManager，支持本次地址名称归属。原URL为`https://docs.uniswap.org/contracts/v3/reference/deployments/ethereum-deployments`，当时重定向至developers.uniswap.org对应V3部署页。未新读网页或核部署字节码。

目前只关闭“这个免费读取路径能返回已知mint、字段与旧原件一致”和“官方接口的事件索引/顺序”两层。没有证明当前owner、剩余liquidity/tokensOwed、完整退出、手续费、全部费用或净收益；公开区间参数也不证明私人择时/退出规则事前公开。等待根取得生命周期原件后独立审阅。

全部实际输入hash列于同名JSON；未改root原件/累计报告或其他Owner文件，无账户/凭证、付款、安装、广播或外发。
