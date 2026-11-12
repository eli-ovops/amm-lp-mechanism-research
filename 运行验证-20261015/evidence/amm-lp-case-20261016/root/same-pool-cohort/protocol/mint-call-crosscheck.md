# owner直调NPM的mint calldata交叉清单

UTC: 2026-10-16T07:44:27.695321+00:00; actual model/effort UNKNOWN. PERMISSIONS-2026-10-14-v1 / ROUTING-2026-10-13-v4.

仅既有固定区间直调calldata清单层PASS。0公开GET，0 EVM/模型/回测/策略执行。

已存88条普通交易中，owner→NPM为33笔（索引失败4笔），静态解码83个leaf调用。mint调用13次，含1次失败交易中的尝试，索引成功12次；成功中11次匹配token0=WETH、token1=USDT、fee3000，recipient均为R。nonce4是另一币对/费率的成功调用；nonce3失败mint尝试不能计作NFT。

Owner/recipient R: `0xeeded7912e2f4aac5781e8befeab728f715314f6`. NPM: `0xc36442b4a4522e871399cd717abdd847ab11fe88`. Cutoff inclusive block: 25790244.

代币地址别名（精确地址）：

- A: `0xa0b86991c6218b36c1d19d4a2e9eb0ce3606eb48`
- B: `0xc02aaa39b223fe8d0a0e5c4f27ead9083c756cc2`
- C: `0xdac17f958d2ee523a2206206994597c13d831ec7`

B/C/3000仅表示预期同池参数匹配。A在本报告仅按地址识别，不补查符号。所有mint recipient均为R。

| nonce | indexed result | token0/token1 | fee | ticks | recipient | txhash |
|---:|---|---|---:|---|---|---|
| 3 | FAILED attempt | A/B | 500 | [201140,202990] | R | `0x7f29a1ceb7da261b1f46dd1198a5a020149cb9c4ba2ef61e692a0a45dbf2cda4` |
| 4 | success | A/B | 500 | [201550,202550] | R | `0x2b2b561890d93ae57537f13e5873a8e78dbec6991769fe093bd6bc7c7cd4b6aa` |
| 17 | success | B/C | 3000 | [-203280,-202200] | R | `0xeed1b5d73f82fe813b229beedf98fb6494b63574f08235f28a8eb0fd8439f1a7` |
| 22 | success | B/C | 3000 | [-203340,-201780] | R | `0xd7be307faedc4ef24046c700b5b9f25703f108a5921e96866cc57860bf29441d` |
| 25 | success | B/C | 3000 | [-202140,-201060] | R | `0x59b00930cc40e556284defe4b1989804970de95a686eaa9eef1edffcf5457700` |
| 34 | success | B/C | 3000 | [-201780,-199740] | R | `0x28cf8e45425306c5d2719e5d34d738a72dc7a0896861e194060dcc29a372f5e7` |
| 39 | success | B/C | 3000 | [-202140,-199860] | R | `0xb9aa1bad6e2324ccff1bbf86f1292ae6484424f268c19b620f70c79cd13cbf43` |
| 41 | success | B/C | 3000 | [-201420,-200400] | R | `0xd4f0ef229912ff11fb91cb26b3a1d4e7297c479460d08b92b6735bcee0ea62da` |
| 45 | success | B/C | 3000 | [-202260,-200280] | R | `0xf9f05d08db6b4b5ab6e5ec1d4149de89a772464937168fa1c28ffc50b097b9cc` |
| 48 | success | B/C | 3000 | [-201660,-200640] | R | `0x317eb40974add0e8354dca27edb477333bbb096c0268b43a0d4ecf20030760e7` |
| 50 | success | B/C | 3000 | [-202080,-200040] | R | `0xb7c8b746a65296e5628dacc228e5f998437c72dfe2e7ad1813b60466b7522232` |
| 56 | success | B/C | 3000 | [-201240,-200220] | R | `0x9de40e6802a0932139ec58b72f020226a3278a603770cca4cd8509315d321024` |
| 59 | success | B/C | 3000 | [-201720,-199680] | R | `0xc7b663a1635627a529e6536417f6225a66278070b5ee108de442a634aa3fc8cc` |

## 清单边界

来源仅为直接owner→NPM交易，不完整覆盖内部helper调用或NFT取得/转移。预期币对/费率及recipient不提供tokenId、实际pool部署、实际投入或成功receipt证明。desired金额不是实际本金。

完整leaf selector/参数原字节与mint全部11字段保存在JSON。失败交易单列，不反推私人入场/区间/退出规则。owner及截止点来自已经观察到的正例，不能称前瞻样本外或全市场样本。

等待完整incoming/outgoing NPM Transfer分页与原mint receipt交叉。它们可能补出helper收到或二级取得的NFT，并绑定实际tokenId/pool；不能据本清单静默排除这些候选或称完整持仓/盈利。

固定范围实际位于free-route-check/next-cohort-list-scope-before-data.json；最初same-pool-cohort输出目录尚不存在，仅创建本Owner的protocol子树，其他文件未改。所有实际输入路径/bytes/SHA256见mint-call-crosscheck.json。
