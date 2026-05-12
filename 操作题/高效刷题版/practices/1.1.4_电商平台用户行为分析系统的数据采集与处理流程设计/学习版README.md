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

## 知识点

data = pandas.read_csv('')
print(data.head())

### 数据清洗、格式转化 
data = data.dropna() # .dropna() 删除任何列中存在空值的数据行

data['Age'] = data['Age'].astype(int) # .astype(int) .astypre(float) 将值转化成指定格式
data['PurchaseAmount'] = data['PurchaseAmount'].astype(float)
data['ReviewScore'] = data['ReviewScore'].astype(int)
    #多条件筛选必须用 &（且）连接，每个条件必须用括号括起来。
    #between(a, b) 等价于 (>=a) & (<=b)，是范围校验的标准写法。
    #筛选后，data 中只保留满足所有条件的有效数据行。
data  = data[
    (data['Age].between(18,70))&
    (data['PurchaseAmount'] > 0)&
    (data['ReviewScore'].between(1,5))
]
    #标准化处理 = （值 - 均值 .mea() ）/ 方差 .std()
pa_m, pa_s = data['PurchaseAmount'].mean(), data['PurchaseAmount'].std()
rs_m, rs_s = data['ReviewScore'].mean(), data['ReviewScore'].std()

data['PurchaseAmount'] = (data['PurchaseAmount'] - pa_m) / ps_s
data['ReviewScore'] = (data['ReviewScore'] - rs_m) / rs_s

data.to_csv('cleaned_user_behavior_data.csv', index=False)
print("数据清洗完成，已保存为 cleaned_user_behavior_data.csv")

### 分组统计

purchase_category_counts = data['PurchaseCategory'].value_counts()
    #groupby('列名')：按指定列分组，后续对分组结果进行聚合计算。
    #['列名']：指定要聚合计算的目标列。
    #.mean()：计算每组的平均值，也可以用 .sum() .count() 等其他聚合函数。
gender_purchase_amount_mean = data.groupby('Gender')['PurchaseAmount'].mean()

age_bins = [0, 18, 26, 36, 46, 56, 66, np_inf]
age_labels = ['18-25', '26-35', '36-45', '46-55', '56-65', '65+']

data['AgeGroup'] = pandas.cut(data['Age'], bins = age_bins, labels = age_labels, right = False) #right = False 左闭右开区间 
age_group_counts = data['AgeGroup'].value_counts().sort_index() # sort_index()：按分段标签的顺序排序，而不是按数量降序

