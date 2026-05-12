# 1.1.3 金融机构信用评估系统中的业务数据审核流程设计 学习版

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

## 知识点复习

data = pd.read_csv(')

### 统计空值与重复值
missing_values = data.isnull().sum() # data.isnull() 布尔矩阵，True表示对应位置为缺失值  .sum()统计所有为True
duplicate_values = data.dumplicated().sum() # data.dumplicated() 布尔矩阵，True表示对应位置为重复值  .sum()统计所有为True

### 数据的合理性审核
data['is_age_valid'] = data['age'].between(18, 70)
data['is_income_valid'] = data['income'] > 2000
data['is_loan_valid'] = data['LoanTerm'] < ( data['income'] * 5 )
data['is_credit_valid'] = data['CreditScore'].between(300, 850)
    # 对每一行的所有布尔列进行 “与” 运算，只有全部为True时，结果才为True , axis=1表示按行操作，axis=0表示按列操作（高频考点）
    # data[['','']] 处理多列数据用双层中括号
valid_checks = data[['is_age_valid','is_income_valid','is_loan_valid','is_credit_valid']].all(axis=1) 
data['is_valid'] = valid_checks

print("检查结果")
print(data[['is_age_valid','is_income_valid','is_loan_valid','is_credit_valid']].describe()) # 结果统计

### 数据清洗与异常值处理
cleaned_data = data[data['is_valid']]# data['is_valid']是布尔类型的值，data[布尔数据]只保留 true 值，生成新表格
cleaned_data = cleaned_data.drop[colums=['is_age_valid', 'is_income_valid','is_loan_amount_valid', 'is_credit_score_valid', 'is_valid]]

cleaned_data.to_csv('cleaned_credit_data.csv',index=False)