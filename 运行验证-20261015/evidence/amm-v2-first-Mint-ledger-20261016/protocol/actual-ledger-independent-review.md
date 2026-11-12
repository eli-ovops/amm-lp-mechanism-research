# 最早Mint交易原账独立审阅

限定PASS：三份原件的hash/字节与回执一致；receipt成功，65条日志878—942，37条ERC20式Transfer逐条独立解码、全部币与地址净额均与root一致。From与To同为`0x0ea041260095b20feda41ef4fdbef7d801f4c438`，不据此猜EOA、合约、现实主体或受益人。顶层value为0。

实际gas为`1067896 × 272220210 = 290702873378160 wei`，即0.000290702873378160 ETH。native索引原件是`status=0 / No transactions found / result=[]`，与API错误不同；这里只支持该提供商查询无已记录native流，不冒充独立余额/trace完备证明。

| 该调用地址的Transfer净额 | 原量 |
|---|---:|
| WETH | +471180782806129 |
| USDC | −1 |
| WBTC | −1 |
| 本池LP | 0 |
| `bb2b…`另一LP | 0 |
| `f12ec…b327` | 0 |

本USDC/WETH池实际放入USDC17078021797409，退回17078021797408；WETH放入7210504871826528855471，退回7210504871826523239770。因此本池腿为USDC−1 raw、WETH−5615701 raw。Mint/Burn间没有本池Swap；这不是持续持仓收费原件。receipt内本池10日志与上一阶段三页原件逐字段一致。

另一`bb2b…`池往返留下WBTC−1 raw及WETH−48410797066 raw。最后log940从`dfcc…ac5`向调用地址转入471229199218896 raw WETH，对应该emitter的log942 Swap式事件；该流入不是本USDC/WETH池费用。另一池真实token顺序/完整实现尚未另核，不以相同topic替代其全部业务身份。

调用地址从`bbbb…ffcb`收到WETH、USDC和WBTC，之后分别返还完全相同原量，三币该往返净额各0。只能称原账往返；未经该合约源码核验，不命名flashloan、不宣称借款费0或共同现实主体。所有本金腿不当收入。

WETH净额减实际ETH gas，在明确ETH/WETH数量1:1假设下得到组件 **+0.000180477909427969**。这承认了实际正WETH流量与gas事实，但并未执行兑换。USDC/WBTC各−1 raw仍未估值；`f12ec…`净0不能当作消耗旧token库存的证据。`223…`/`222…`非Transfer奖励或债权机制、之前权利及其他余额状态UNKNOWN，故不能自动断言此组件是新增经济利润，亦不能否认已观察现金事实。不称ROI、完整投资净利或个人未来复制优势。

本审阅0网络，仅自写被动JSON/hex/整数核算，无来源代码、模型、回测、EVM、SDK或策略执行。没有增设完整私人bot或全部私人动机门槛。全部输入SHA、UTC、两池分腿、三币暂时往返、65条事件绑定与逐币逐地址净额见同名JSON；实际model/effort为UNKNOWN。
