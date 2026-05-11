# 2.1.4 医疗研究数据清洗和标注设计 学习版

## 题目要点

- 题型定位：数据清洗、预处理与标注流程设计
- 这是最模板化的一组题，重点在流程完整。
- 常见动作包括缺失值处理、类型转换、标准化、特征选择、训练测试集划分。
- 文字部分通常要写“数据清洗规范”和“数据标注规范”。

## 解题步骤

1. 读取数据，查看前几行和字段类型。
2. 统计缺失值并处理异常值或错误类型。
3. 对必要的数值字段做标准化处理。
4. 明确特征列和目标变量。
5. 划分训练集与测试集，保存清洗结果和规范文档。

## 高频代码模板

```python
import pandas as pd
from sklearn.preprocessing import StandardScaler
from sklearn.model_selection import train_test_split

data = pd.read_csv("data/xxx.csv")
print(data.head())
print(data.isnull().sum())

data["某列"] = pd.to_numeric(data["某列"], errors="coerce")
data = data.dropna()

scaler = StandardScaler()
data[num_cols] = scaler.fit_transform(data[num_cols])
```

## 易错点

- 只做代码，不写答题卷中的清洗规范/标注规范。
- 把目标变量也一起标准化或错误放进特征列。
- 导出文件名和格式不对。

## 5分钟速记版

- 五步法：看结构、查缺失、转类型、做标准化、定特征与目标。
- 文字题至少准备 4-6 条规范表达。

## 建议练习顺序

- 先看 `exam_preview.html` 理解题面。
- 再做 `example.ipynb` 或 `answer_template.docx`。
- 最后对照题目要求检查文件保存格式与命名。