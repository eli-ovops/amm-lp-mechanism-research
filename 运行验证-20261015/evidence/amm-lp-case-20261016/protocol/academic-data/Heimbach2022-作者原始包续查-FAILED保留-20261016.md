# Heimbach等2022：作者原始数据入口续查（UNKNOWN／未准入）

结论：**Heimbach作者原始包仍未取得，状态为UNKNOWN／未准入。**没有找到可静态核字段的固定数据版本，故不标记净盈利证据进展；不据此宣称作者未发布或数据不存在。只补清论文原始数据来源、收益定义和本轮实际入口覆盖。

命名澄清：此前本分支用“FAILED”表示原账取得/验收未完成，容易与实验结果混淆，现明确纠正为UNKNOWN／未准入；不是Heimbach策略实测亏损或论文无效。本报告从未运行其策略。原Kronos实验FAILED保持，未改动其文件、状态或结果。文件名保留旧字样供历史定位，不能将其当实验结论。

只拥有本academic-data目录；没有改此前academic报告、root、累计报告或状态。仅公开GET与文本/JSON字段检查，没有下载大包、安装、运行论文/分析代码、模型、回测、EVM、交易、注册、付款或外发。实际model/effort UNKNOWN；沿用PERMISSIONS-2026-10-14-v1、ROUTING-2026-10-13-v4。

## 原论文实际确认

[作者托管论文](https://liobaheimbach.github.io/assets/pdf/Papers/Risks_and_Returns_of_Uniswap_V3_Liquidity_Providers.pdf)，DOI10.1145/3558535.3559772，AFT2022。此次不重复首页，读取正文数据采集和收益定义段：

- §5.1说明自建Erigon，从Ethereum过滤Uniswap V3相关事件，区间block12369739（2021-05-04）至14497033（2022-03-31）。这是论文的数据采集描述，未取得其原始事件文件或receipt。
- 式(3)的回报为LP仓位价值加费用相对同一初始资产被动持有价值的差额比例；§5.3按完整日计算该回报。该公式未列链上gas扣项，不足以把图中的正值称已实现扣全部gas的账户盈利；也不据单一关键词阴性断言所有方法完全忽略成本。
- 论文明确分析单个流动性position而非钱包/实体。position未由本次材料绑定为特定ERC721 tokenId及连续完整原账，不能用模型模拟图、正收益分布或经验日收益代替实际mint/increase/decrease/collect及退出核验。

## 已检查的作者/机构入口

1. `https://api.github.com/users/liobaheimbach/repos?per_page=100&type=owner` 返回7个公开仓库，一页不足100，无本论文标题/Uniswap V3 LP数据相关命名。其内容涉及其他论文；没有下载和运行它们，也没有把其他论文代码冒称本论文复制包。该查询不覆盖全体合作者、组织、私有/未索引仓库，不能推出不存在。
2. [作者当前首页](https://liobaheimbach.github.io/)重定向[liobaheimba.ch](https://liobaheimba.ch/)，页面是selected publications，所见代码链接对应别的论文；没有本论文数据入口。精选列表不是作者全部出版物，不作排除性证明。
3. [ETH TIK论文条目5049](https://tik-old.ee.ethz.ch/db/public/tik/?db=publications&form=report_single_publication&publication_id=5049)列BibTeX、论文PDF、SlidesPDF三项资源，所见无代码/数据下载项。
4. 论文全文索引find `github`未命中；find `available`产生普通正文词而非开放数据声明。两条针对合作者/题名的数据检索未返回可确认作者原包。检索结果中的第三方Zenodo项目是引用该论文的其他研究，不是这三位作者本论文的数据，未越界追取。

## 仍未取得/UNKNOWN

| 验收项 | 结果 |
|---|---|
| 作者明确的公开代码/数据可用性声明 | 未取得，UNKNOWN |
| 精确原始下载包、版本/commit、发布日期 | 未取得，UNKNOWN |
| tokenId / NFT—pool—owner映射 | 未取得原始数据字段 |
| 全mint/increase/decrease/collect、金额、txhash、logIndex | 未取得原始数据字段 |
| receipt gasUsed/effectiveGasPrice及失败交易 | 未取得原始数据字段 |
| 完整退出/期末残余与手续费本金拆分 | 未核任何单个position |
| 数据/程序个人复用许可 | UNKNOWN；论文文本个人复制许可不代替数据库或代码许可 |
| 净正真实单个NFT案例 | 未确认，UNKNOWN／未准入 |

没有运行采集器或重建模型来填原账缺项。本轮8次公开读取已到，停止扩展。下一项能改变结论的原件应是作者或机构明确发布的原始文件清单/数据可用性声明（含精确下载URL及许可），随后只读核字段、指定NFT和费用；再读正收益摘要不能替代。

## 证据保存

public-web-tool-responses.json为本轮公开工具返回的文本/页面响应，**不是整份PDF原二进制或历史存档**。author-public-repos.json为GH原JSON，gh-receipts.json含准确取得UTC/URL/hash。receipts.json列8次请求及文本响应SHA256；工具未暴露精确逐web请求时间，明确记UNKNOWN，保存UTC不冒充读取时刻。未联系作者或要求凭证。
