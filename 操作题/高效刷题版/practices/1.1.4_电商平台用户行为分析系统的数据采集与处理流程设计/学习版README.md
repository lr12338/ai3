# 1.1.4 电商平台用户行为分析系统的数据采集与处理流程设计 学习版

## 题目要点

- 题型定位：业务数据采集、处理、统计与异常识别
- 先读懂业务规则，再把业务规则翻译成字段标签或筛选条件。
- 重点掌握分组统计、区间划分、异常标记、缺失值处理这几类基础操作。
- 最后别忘了结果截图、文件保存和命名要求。

## 解题步骤

1. 读取数据并查看字段含义。
2. 根据题目要求构造统计口径或标签列。
3. 使用 `groupby`、`value_counts`、`pd.cut` 等方法完成统计。
4. 如涉及异常值或缺失值，先标记再清洗。
5. 输出结果并按题目要求保存截图或文件。

## 高频代码模板

```python
import pandas as pd
import numpy as np

data = pd.read_csv("data/xxx.csv")
print(data.head())

data["标签列"] = np.where(条件, "A", "B")
stats = data.groupby("分组列")["指标列"].agg(["count", "mean"])
print(stats)
```

## 易错点

- 把业务条件写反，例如高风险阈值方向错了。
- 分组后忘记展开结果，导致输出格式不直观。
- 清洗完没有删除辅助列，或者保存文件名不符合要求。

## 5分钟速记版

- 读数据 -> 打标签 -> 分组统计 -> 异常处理 -> 保存结果。
- 高频 API：`read_csv`、`np.where`、`groupby`、`value_counts`、`fillna`。

## 建议练习顺序

- 先看 `exam_preview.html` 理解题面。
- 再做 `example.ipynb` 或 `answer_template.docx`。
- 最后对照题目要求检查文件保存格式与命名。