# analyzing-parking-operations-data

一个用于分析停车场 Excel/CSV 出场明细的 Codex Skill（中文：停车场运营数据分析）。它帮助生成车流、车辆类型、可用收入、每日趋势、数据异常和运营观察，并保留字段映射与统计口径。

## 使用

将本目录放入支持 `SKILL.md` 的 Skills 目录，或在支持 Skill 的工作环境中引用此目录。提供 Excel/CSV 出场明细并提出分析需求，例如：

> 请用 analyzing-parking-operations-data 分析这份停车场出场明细，按出场日期统计每日车流、分类和可用的实收，并列出异常记录。

运行时会根据实际列名和数据语义识别字段；歧义会请用户确认。此 Skill 是分析说明，不包含特定停车系统的固定字段模板或数据处理程序。

## 核心口径

- 一条有效出场记录计一次车流；同车牌多次有效出场分别计数。
- 按实际出场日期统计，月度结果汇总每日数据。
- 保留原始类型；仅在含义可靠时归并为临停、月租等。
- 仅在可信金额字段和记录粒度明确时分析收入；缺失时不补零。
- 疑似重复、缺失、无效日期等异常单独报告；不静默删除或覆盖原数据。

输出样式见 [examples/example-output.md](examples/example-output.md)，虚构输入见 [examples/sample-data.csv](examples/sample-data.csv)，边界验收见 [tests/test-cases.md](tests/test-cases.md)。

## 隐私与适用范围

仓库只包含虚构示例，不包含任何真实车牌、客户或项目经营数据。使用真实文件时，应遵循文件所有者的数据处理要求。Skill 适用于出场明细；只有入场、订单或支付流水时，须先确认其与出场事件的对应关系。

## License

MIT，见 [LICENSE](LICENSE)。
