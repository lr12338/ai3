# 1.1.2 智能农业系统中的业务数据采集和处理流程设计 学习版

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

## 知识点整理

### 读取表格
data = pd.read_csv('path') # 
data.head() 

### 统计某列的数量和平均值
stats = data.groupby('分组列')['指标列'].agg(['count', 'mean']) # 计算 数量 count， 平均值 mean
print('stats') # 输出 分组列 下的 数量和平均值

### 统计 某个位置的 温度和传感器（筛选条件）平均值
locate_stats = (
    data[data['a'].isin(['b','c'])] # data[筛选条件] 筛选a列中值为b和c的值
    .groupby(['d','a'])['d'] # 按照d和a依次分组。并只对 d列数据 进行后续处理
    .mean() # 对d列求平均值 
    .unstack() # 透视展开
)
print('locate_stats')

### 异常标记与缺失值处理并导出

data['新数据列'] = np.where（ #(条件, 真值，假值)
                ((data['a'] == A) 
                & ((data['B'] < -10) | (data['c'] > 50))
                ) | (
                (data['a'] == A) 
                & ((data['B'] < -10) | (data['c'] > 50))                    
                ),
                True,
                False, # 多行输入，一般都加逗号，可加可不加
                ）

counts = data[''].sum() # 统计所有True的数量
print("异常值",counts)

data['a'] = data['a'].ffill().bfill() # .ffill()用前值补充 .bfill()用后值补充 先前再后

cleaned_data = data.drop(column=['b']) # 删除b列 data.drop(column=[''])
cleaned_data.to_csv('cleaned_data.csv', index=False) # 保存新表格 data.to_csv(''.index=False)
print("数据清洗完成，已保存为 cleaned_data.csv")

