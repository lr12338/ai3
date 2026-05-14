# 2.1.5 健康与营养咨询数据预处理与数据规范设计 学习版

## 一、代码题目要求（来自刷题模板）

1. 读取 `data/健康咨询客户数据集.csv`，输出数据类型、表结构和各列缺失值。
2. 删除含缺失值的样本行。
3. 将 `Your age` 转为整数，并处理异常值（非数字、负值）。
4. 删除重复值并记录删除数量。
5. 对 `How do you describe your current level of fitness ?` 做编码/归一化处理。
6. 绘制 `How often do you exercise?` 分布饼图。
7. 完成数据标注与 8:2 划分。
8. 保存 `2.1.5_cleaned_data.csv`，并准备 `2.1.5.docx` 与 `2.1.5.html`。

## 二、example.ipynb 考察要点（填空位）

- `pd.read_csv` + `info()` + `isnull().sum()` 基础检查。
- `dropna()` 删除缺失样本。
- `pd.to_numeric(..., errors='coerce')` + `astype(int)` 年龄清洗链。
- `duplicated().sum()` 与 `drop_duplicates()`。
- `LabelEncoder` 对健身水平列编码。
- 列名清洗：`data.columns.str.strip()`。
- `value_counts()` 后 `plot.pie(...)` 生成频率饼图。
- `train_test_split(..., test_size=0.2, random_state=42)` 与导出。

## 三、文本题（2.1.5.docx）作答要点

### 数据清洗规范

- 年龄字段必须先转数值再做范围过滤，避免字符串脏值污染。
- 缺失与重复处理顺序固定，处理数量需记录。
- 问卷字段名中英混合时，先做空格与格式统一。
- 编码前确认枚举取值，避免“同义不同写法”导致标签分裂。
- 所有清洗规则需有业务依据（如年龄不可为负）。

### 数据标注规范

- 明确目标字段与特征字段的角色边界。
- 类别编码映射应保留说明，便于解释模型结果。
- 数据划分前完成清洗和编码，防止训练测试口径不一致。
- 图表统计口径与最终导出数据保持一致。
- 严格使用题面命名：`2.1.5_cleaned_data.csv`、`2.1.5.docx`、`2.1.5.html`。

## 四、易错点速记

- 清洗后又回到原始 `data` 继续处理，导致前面步骤失效。
- 导出文件名写成 `2.1.5_cleaned_split.csv`（不符合题面）。
- 只画图不解释图表结论，文本题得分受限。
- 编码后未说明标签映射关系。