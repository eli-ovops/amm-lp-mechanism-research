# 群组NFT身份与覆盖：限定原件层PASS

审阅UTC：2026-10-16T07:51:14.877934+00:00；实际model/effort UNKNOWN。沿用PERMISSIONS-2026-10-14-v1、ROUTING-2026-10-13-v4。0联网，仅原始JSON/receipt、ABI/hex、整数/hash被动核对；无EVM、模型、回测、策略、安装、账户、交易或外发。

**未发现cohort-identities.json的实质身份错误。限定通过：截至固定区块25790244，同一提供商返回的12个收到NFT、0个转出，与12次成功mint输入及原receipt一一绑定；其中11个属于预定目标池。本阶段不审收益或评分。**

## 四页Transfer与12份mint receipt

incoming page1/2为12/0，outgoing为0/0，均HTTP200、API status1/OK。逐文件hash/bytes与保存回执一致。URL确为NPM地址、块0—25790244、Transfer topic0，并分别AND topic2=owner（收到）、topic1=owner（转出），没有把NFT id与from/to的topic位置混用。

12条incoming均来自Null、发给固定owner，tokenId及日志身份无重复，包含原已核NFT1338529。全部txhash集合与既有calldata交叉中的12次索引成功mint相同；失败nonce3没有mint NFT，保留为另审成本候选，不混入成功数量。

原始receipt共12份：新11份保存原件及回执，1338529复用旧原件并重核hash，未重取。均成功、from=owner、to=NPM，tx/block身份与日志一致。每笔唯一NPM NFT mint及唯一Increase、pool Mint逐项核tokenId、topics/hash/height/logIndex、ticks、liquidity和实际两币数量；实际付pool的两条token Transfer亦吻合，且实际数量满足对应mint上下限，没有以desired代替实际投入。

## data表示差异保持原状

incoming索引12条中，8条data为原始空字符串，4条为`0x`；12份receipt对应ERC721 Transfer的data全部为`0x`。Transfer所有参数均indexed，空payload在这里没有非indexed字段待解码，但**原字符串并不逐字节相同**。

本次仅比较topics与核心日志身份，不把空字符串回填成`0x`或称data原样一致。全部8项差异、原data与receipt data保存在审阅JSON；原件未改。这个提供者格式差异不影响已对齐的NFT身份，也不替代独立节点完整性证明。

## 目标池名单

精确匹配WETH地址、USDT地址、fee3000、实际pool `0x4e68ccd3e89f51c3074ca5072bbac773960dfa36`的11个NFT为：

| tokenId | mint nonce |
|---:|---:|
| 1319375 | 17 |
| 1321691 | 22 |
| 1324363 | 25 |
| 1334916 | 34 |
| 1335240 | 39 |
| 1335246 | 41 |
| 1335613 | 45 |
| 1336197 | 48 |
| 1336999 | 50 |
| 1338391 | 56 |
| 1338529 | 59 |

另一个收到NFT **1307592**来自nonce4：token0=A0b8…、token1=C02…、fee500，实际pool `0x88e6a0c2ddd26feeb64f039a2c41296fcb3f5640`，因此按预先精确币对/费率/地址范围排除。没有读取或依据它的盈亏作排除。

## 通过与未通过层

该返回集合中没有未匹配到mint输入的helper/二级取得NFT；这不是断言所有别的钱包、helper、其他manager或提供者遗漏均不存在。仅能说这次完整正常分页的收到/转出返回集合与直接成功mint清单闭合，不能称独立全链证明。

12份初始mint身份不证明11个目标仓位后来都关闭、无残余、手续费已实收或扣费盈利；后续所有记账日志、失败成本、开放仓位与评分仍待独立原件。本阶段不反推私人入场/退出规则，不把owner已由正例选中这一事实改写成前瞻样本外抽样。

本次全部真实输入路径、bytes、SHA256，12个NFT的实际初始数量/receipt定位及8项data差异见`population-identity-independent-review.json`。根/其他Owner及原始失败记录未改。
