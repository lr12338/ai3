# 2.1.1 智慧交通中燃油效率模型的数据清洗和标注流程设计 学习版

## 一、代码题目要求（来自刷题模板）

1. 读取 `data/auto-mpg.csv`，输出前 5 行与字段类型。
2. 检查缺失值并删除缺失行。
3. 将 `horsepower` 转为数值（`errors='coerce'`）并清理转换异常。
4. 对数值特征做标准化：`displacement`、`horsepower`、`weight`、`acceleration`。
5. 按题目指定选择特征：`cylinders`、`displacement`、`horsepower`、`weight`、`acceleration`、`model year`、`origin`。
6. 将 `mpg` 设为目标变量并完成标注。
7. 按 8:2 划分训练集与测试集。
8. 保存 `2.1.1_cleaned_data.csv`，并准备 `2.1.1.docx` 与 `2.1.1.html`。

## 二、example.ipynb 考察要点（填空位）

- `pd.read_csv()`、`head()`、`isnull().sum()`、`dropna()` 基础清洗链。
- `pd.to_numeric(..., errors='coerce')` 与 `dropna(subset=...)` 联动。
- `StandardScaler().fit_transform(...)` 的标准化写法。
- 目标变量与特征拆分：`X = data[selected_features]`，`y = data['mpg']`。
- `train_test_split(..., test_size=0.2, random_state=42)` 参数完整性。
- 导出要求：`to_csv(..., index=False)`。

## 三、文本题（2.1.1.docx）作答要点

### 数据清洗规范

- 明确原始字段类型检查规则（数值、类别、日期）。
- 缺失值处理采用“删除缺失行”，并记录处理前后样本量。
- 对 `horsepower` 的非法字符统一转 `NaN` 后剔除，避免脏值入模。
- 标准化仅作用于连续数值字段，类别字段不进行同类变换。
- 清洗流程应具备可复现性（固定步骤、固定参数、固定随机种子）。

### 数据标注规范

- 目标变量统一定义为 `mpg`，并写明业务含义（燃油效率）。
- 特征命名与字段口径保持一致，不随意重命名导致映射丢失。
- 数据集划分比例固定 8:2，随机种子固定为 42。
- 训练/测试集来源应同分布，避免信息泄漏。
- 文件命名按题面统一：`2.1.1_cleaned_data.csv`、`2.1.1.docx`、`2.1.1.html`。

## 四、易错点速记

- 把 `mpg` 误放进标准化特征列表。
- 忘记对 `horsepower` 做数值转换，导致模型前报错。
- `train_test_split` 参数不完整（漏 `test_size` 或 `random_state`）。
- 导出 CSV 忘记 `index=False`。