# BIS Working Paper1227 成本/回报口径独立本地审阅

结论：**不能将论文的Net Return称为完整个人实付费用原账或账户全部现金净利润。**正文明确使用按交易类型的gasUsed中位数作LP成本分摊；净回报相对Vhold持币基准，另有每日估计成本图。原PDF与所给SHA一致。本次0联网，仅读既存相关页文本与11条annotation列表，未重复全文提取、运行论文/分析代码、模型、策略、回测、EVM或交易。实际model/effort UNKNOWN。

## 1. gas有真实来源，但论文成本并非逐笔全部实付费

PDF页16说明作者取得流动性相关交易的gasUsed与gasPrice。PDF页29（印刷26）进一步明确：按mint、collect或burn类型计算gasUsed的中位数，乘各交易receipt gasPrice，再用Binance小时ETH价格换USD。脚注24解释，复杂策略中把整笔gas全归LP会高估LP成本，所以用中位数分摊。

这是一项有理由的研究归因选择，不能擅判错误；但它意味着G不等于该交易实际gasUsed×实际有效gasPrice的完整收据费用，更不是个人全部钱包gas、授权、失败尝试、对冲和其他复合操作成本的总和。receipt gasPrice真实不使替换后的gasUsed变回实际值。若报告要称“扣gas”，应具体说“按论文LP成本分摊口径扣gas”，不称已审计个人实际全成本。

## 2. 净回报是相对持币基准，并有处理/附录口径差异

PDF页29—30（印刷26—27）公式为 `Rnet=(F+Vliq−Vhold−G)/Vhold`。Vhold为按比较时点价格衡量的原有两token被动持有组合；F为计入的费用收入，Vliq为LP库存价值。它衡量相对持币的净超额回报，不等于“全部提款现金－全部入金现金－实付费用”的账户总损益，亦不是直接法币初始资本ROI。作者按日计算费收益和库存差、把gas归交易发生日；不能从正日收益或分组均值直接认定一个真实已完全退出NFT账户净正。

PDF49/50附录G区分：A—C为所称paid gas fees的仓位分布；D为给定日期若mint+burn所需的估计成本。必须保留下列原文不一致，不能替作者静默统一：

- 正文为类型gasUsed中位数×receipt gasPrice，包含mint/collect/burn；G.1图注说按mint/burn交易汇总的paid fees，未在该说明逐一交代collect及其他动作如何处理。
- 附录G正文说日median gasPrice，图注说mean gasUsed（mint424300、burn238300）×每日mean gasPrice；正文还把估计时间序列指为Panel B，图注指为Panel D。
- 正文币价来源Binance小时价；图注写CCData小时或日终价。脚注25及图注另有99%分位winsorization，相关研究指标不能直接当未变换的逐笔账。

这些差异需要作者方法/源程序/原表才能消歧；本次不据差异反算、修复论文或否定其整体研究结果。无论最终采用哪种解释，现有文本都不足以充当完整个人实付费ledger。

## 3. 没拿到直接原始包或数据复用许可

已存全文和11项URI annotation列表中未得到直接dataset/代码复制包或相应license入口。11条链接主要是文献DOI、FRED与语义索引，并不提供NFT原账下载。这只能说**本轮这组材料未提供直接入口**，不能断言作者/其他机构没有另行发布；普通文本URL未必都属于PDF annotation。

论文自述采集真实链上数据不等于数据已公开下载，也不证明所有NFT的mint/increase/decrease/collect、实际gas、完整退出与余额均可从此PDF复核。取得明确作者发布的数据/代码版本及许可后，仍须核指定真实NFT与完整成本，才能补足原账验收。本报告不改变此前学术分支“未取得合格新原账包”（UNKNOWN／未准入）的记录；原Kronos实验FAILED不属本次审阅、未作改动。

## 输入指纹与范围

本地审阅UTC：2026-10-16T04:13:13.901507+00:00。

- bis-working-paper1227-current.pdf：`39c043c7d27362c8e5242408936985c46de73a48e381b17f8b86d545ca3ef4ba`（3598114 bytes）
- bis-working-paper1227-extracted.txt：`3cd905972c663f1ae1183b2243d2d083923a316b38fbf1b7dca333d0dc578c23`（120176 bytes）
- bis-pdf-links.json：`c477815e59b3273bec1e1d8a8e3e86e94a0ad8ff0c6c50c37157e0a682c737ae`（963 bytes）
