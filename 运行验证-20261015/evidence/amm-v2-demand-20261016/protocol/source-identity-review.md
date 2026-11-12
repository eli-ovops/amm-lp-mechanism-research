# V2官方源码与池身份独立审阅

限定PASS。固定官方commit为`6a9e7c97860676e0992f22a49665760444c1cdf5`；9份官方文件及repo原HTML、Factory事件原件的SHA/字节与收据一致。本轮0网络、没有执行源码。

官方部署页列Mainnet Factory `0x5c69bee701ef814a2b6a3edd4b1652cb9cc5aa6f`。实际匹配返回仅一条PairCreated：token0为USDC `0xa0b8…eb48`，token1为WETH `0xc02a…6cc2`，data的pair为`0xb4e16d0168e52d35cacd2c6185b44281ec28c9dc`，第二word为allPairs序号1。块10008355、2020-05-05T20:22:25 UTC、交易`0xd07c…ab3a`均与派生身份一致。Factory源码排序token并拒绝已有pair；这支持此固定市场身份，不是本轮执行getPair或独立历史全量证明。

PairCreated的token0/1 indexed，data为pair/uint序号。Swap的sender/to indexed，data依次为amount0In、amount1In、amount0Out、amount1Out，共128字节。sender/to可为router或合约，不能作独立人数；LP-token的decimals也不能证明两种底层币decimals。Swap topic仍待实际池原件/ABI绑定，本轮没有自行算Keccak或以SHA3替代。

Pair核心没有直接报价函数：调用者指定输出，合约先转出并可触发callback，再由实际balance导出input，校验`(balance0*1000-input0*3)*(balance1*1000-input1*3) >= reserve0*reserve1*1000²`。这是公开的3/1000输入费机制与约束，不是已经取得可执行报价或利润。

`_mintFee`读取Factory的feeTo；若开启且sqrt(k)较kLast增长，可按源码公式向feeTo铸LP，稀释原LP。目标日实际feeTo状态UNKNOWN，不能写“全部0.3%归LP”。mint/burn调用该机制；burn取回的是当前按份额资产，包括本金和库存变化，不等于独立手续费。Swap量、费用积累、LP权利和持有者全成本净利须分开。

已读repo LICENSE为GNU GPL第3版文本，不是MIT。允许在GPL条件范围内研究/复用源码；分发、依赖与periphery许可另核，不能笼统称全部代码无条件商用。commit页面的authored/committed均为2026-04-02T12:50:41−07:00；元数据日期早于本例日，但不独证首次公开时间。当前官方文档也不当历史网页存档。部署runtime独立编译对应、目标日配置与个人盈利尚未证明；这些不妨碍继续有限的实际需求计数。

完整源行号、原URL/UTC/hash与独立事件解码见同名JSON。实际model/effort为UNKNOWN，继承设置未覆盖；不增加私人bot或未来盈利资料门槛。
