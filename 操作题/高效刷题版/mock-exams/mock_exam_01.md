# 人工智能三级模拟试卷（第01套）

## 考试说明

- 本卷共 6 道大题，满分 100 分。
- 本卷仅提供题目，不提供参考答案。
- 请结合各题包内 `exam_preview.html` 完成作答。

## 题目

### 一、业务分析（25分）  
**题号：1.1.1 智能医疗系统中的业务数据处理流程设计**

请围绕智能医疗业务场景，完成业务数据处理流程设计。需覆盖数据采集、处理、审核与输出闭环，并体现关键环节的规范要求与质量控制点。  
素材路径：`practices/1.1.1_智能医疗系统中的业务数据处理流程设计/exam_preview.html`

#### 任务说明（摘自考试预览）

- 背景：某医疗机构计划引入智能医疗系统，通过患者历史数据和机器学习算法预测健康风险，辅助医生诊断与治疗。
- 数据集：`patient_data.csv`，字段包括 `PatientID`、`Age`、`BMI`、`BloodPressure`、`Cholesterol`、`DaysInHospital`。
- 任务1：补全并运行 `1.1.1.ipynb`，统计住院天数超过7天患者数量及占比（超过7天定义为高风险患者，反之为低风险患者），结果截图保存为 `1.1.1-1.jpg`。
- 任务2：统计不同 BMI 区间中高风险患者比例与患者数，区间为偏瘦（<18.5）、正常（18.5-23.9）、超重（24.0-27.9）、肥胖（>=28.0），结果截图保存为 `1.1.1-2.jpg`。
- 任务3：统计不同年龄区间中高风险患者比例与患者数，区间为 <=25岁、26-35岁、36-45岁、46-55岁、56-65岁、>65岁，结果截图保存为 `1.1.1-3.jpg`。
- 结果提交：`1.1.1.html`、`1.1.1-1.jpg`、`1.1.1-2.jpg`、`1.1.1-3.jpg`；考生文件夹命名为“准考证号+身份证号后六位”。

#### 代码文件（完整代码）

```python
import pandas as pd
import numpy as np

# 读取数据集 1分
data = _____________

# 1. 统计住院天数超过7天的患者数量及其占比
# 创建新列'RiskLevel'，根据住院天数判断风险等级 3分
_____________ = _____________(_____________, '高风险患者', '低风险患者')
# 统计不同风险等级的患者数量 2分
risk_counts = data_____________._____________
# 计算高风险患者占比 1分
high_risk_ratio = risk_counts['高风险患者'] / _____________
# 计算低风险患者占比 1分
low_risk_ratio = risk_counts['低风险患者'] / _____________

# 输出结果
print("高风险患者数量:", risk_counts['高风险患者'])
print("低风险患者数量:", risk_counts['低风险患者'])
print("高风险患者占比:", high_risk_ratio)
print("低风险患者占比:", low_risk_ratio)

# 2. 统计不同BMI区间中高风险患者的比例和统计不同BMI区间中的患者数
# 定义BMI区间和标签
bmi_bins = [0, 18.5, 24, 28, np.inf]
bmi_labels = ['偏瘦', '正常', '超重', '肥胖']
# 根据BMI值划分指定区间 4分
data['BMIRange'] = _____________(_____________, _____________, _____________, right=False)  # 使用左闭右开区间
# 计算每个BMI区间中高风险患者的比例 2分
bmi_risk_rate = _____________(_____________)['RiskLevel'].apply(lambda x: (x == '高风险患者').mean())
# 统计每个BMI区间的患者数量 1分
bmi_patient_count = data_____________

# 输出结果
print("BMI区间中高风险患者的比例和患者数:")
print(bmi_risk_rate)
print(bmi_patient_count)

# 3. 统计不同年龄区间中高风险患者的比例和统计不同年龄区间中的患者数
# 定义年龄区间和标签
age_bins = [0, 26, 36, 46, 56, 66, np.inf]
age_labels = ['≤25岁', '26-35岁', '36-45岁', '46-55岁', '56-65岁', '＞65岁']
# 根据年龄值划分指定区间 4分
data['AgeRange'] = _____________(_____________, _____________, _____________, right=False)  # 使用左闭右开区间
# 计算每个年龄区间中高风险患者的比例 2分
age_risk_rate = _____________(_____________)['RiskLevel'].apply(lambda x: (x == '高风险患者').mean())
# 统计每个年龄区间的患者数量 1分
age_patient_count = data_____________

# 输出结果
print("年龄区间中高风险患者的比例和患者数:")
print(age_risk_rate)
print(age_patient_count)
```

---

### 二、智能训练-数据处理规范制定（15分）  
**题号：2.1.1 智慧交通中燃油效率模型的数据清洗和标注流程设计**

针对燃油效率建模任务，完成数据预处理与标注规范制定。请明确数据检查、缺失值处理、异常值处理、特征处理、数据划分与结果保存要求。  
素材路径：`practices/2.1.1_智慧交通中燃油效率模型的数据清洗和标注流程设计/exam_preview.html`

#### 任务说明（摘自考试预览）

- 背景：基于汽车燃油效率数据集开发预测模型，建模前需完成数据清洗与标注并制定规范。
- 数据与环境：`auto-mpg.csv`，Python 环境。
- 要求1：加载数据并展示前5行及数据类型。
- 要求2：检查缺失值并删除缺失值所在行。
- 要求3：将 `horsepower` 转换为数值类型并处理转换异常值。
- 要求4：对数值型数据标准化处理。
- 要求5：选取特征 `cylinders`、`displacement`、`horsepower`、`weight`、`acceleration`、`model year`、`origin`。
- 要求6：将 `mpg` 设为目标变量并标注，完成数据标注与划分。
- 要求7：保存清洗后数据为 `2.1.1_cleaned_data.csv`；制定清洗和标注规范并写入 `2.1.1.docx`；代码与运行结果导出为 `2.1.1.html`。
- 文件保存：均存入考生文件夹（命名“准考证号+身份证后6位”）。

#### 代码文件（完整代码）

```python
import pandas as pd

# 加载数据集并显示数据集的前五行 1分
data = __________
print("数据集的前五行:")
print(__________)

# 显示每一列的数据类型
print(data.dtypes)

# 检查缺失值并删除缺失值所在的行  2分
print("\n检查缺失值:")
print(__________.__________.__________)
data = __________

# 将 'horsepower' 列转换为数值类型，并（删除）处理转换中的异常值 1分
data['horsepower'] = __________(data['horsepower'], errors='coerce')
data = __________

# 显示每一列的数据类型
print(data.horsepower.dtypes)

# 检查清洗后的缺失值
print("\n检查清洗后的缺失值:")
print(data.isnull().sum())

from sklearn.preprocessing import StandardScaler
# 对数值型数据进行标准化处理 1分
numerical_features = ['displacement', 'horsepower', 'weight', 'acceleration']
scaler = StandardScaler()
data[numerical_features] = __________

from sklearn.model_selection import train_test_split
# 选择特征、自变量和目标变量 2分
selected_features = __________
X = __________
y = __________

# 划分数据集为训练集和测试集（训练集占8成） 1分
X_train, X_test, y_train, y_test = __________(__________, random_state=42)


# 将特征和目标变量合并到一个数据框中
cleaned_data = X.copy()
cleaned_data['mpg'] = y

# 保存清洗和处理后的数据（不存储额外的索引号） 1分
__________('2.1.1_cleaned_data.csv', __________)

# 打印消息指示文件已保存
print("\n清洗后的数据已保存到 2.1.1_cleaned_data.csv")
```

---

### 三、智能训练-算法测试（20分）  
**题号：2.2.1 智能信用评分Logistic回归模型开发与测试**

完成信用评分模型开发与测试流程。包括数据集划分、模型训练、模型保存、预测评估及不平衡样本处理，并输出测试分析结论。  
素材路径：`practices/2.2.1_智能信用评分Logistic回归模型开发与测试/exam_preview.html`

#### 任务说明（摘自考试预览）

- 背景：基于 `finance` 数据集完成信用评分 Logistic 回归模型开发、测试、分析与纠正。
- 要求1：正确加载数据并显示前5行。
- 要求2：设置自变量和因变量，完成模型训练，保存模型为 `2.2.1_model.pkl`，预测结果保存为 `2.2.1_results.txt`。
- 要求3：使用测试工具测试并记录结果，保存为 `2.2.1_report.txt`。
- 要求4：对测试结果进行性能评估、错误分析和改进建议，写入 `2.2.1.docx`。
- 要求5：分析错误案例并纠正后重新训练，结果保存为 `2.2.1_results_xg.txt`。
- 要求6：代码与运行结果导出为 `2.2.1.html`，所有结果保存至考生文件夹（命名“准考证号+身份证后6位”）。
- 数据字段说明：含 `SeriousDlqin2yrs`、`RevolvingUtilizationOfUnsecuredLines`、`age`、逾期次数、`DebtRatio`、`MonthlyIncome`、`NumberOfDependents` 等字段。

#### 代码文件（完整代码）

```python
import pandas as pd
from sklearn.model_selection import train_test_split
from sklearn.linear_model import LogisticRegression
import pickle
from sklearn.metrics import classification_report
from imblearn.over_sampling import SMOTE

# 加载数据
data = __________

# 显示前五行的数据
print(__________)

# 选择自变量和因变量
X = data.drop(['SeriousDlqin2yrs', 'Unnamed: 0'], axis=1)
y = data['SeriousDlqin2yrs']

# 分割训练集和测试集（测试集20%）
X_train, X_test, y_train, y_test = __________(__________, random_state=42)

# 训练Logistic回归模型（最大迭代次数为1000次）
model = __________
#训练 Logistic 回归模型
__________

# 保存模型
with open('2.2.1_model.pkl', 'wb') as file:
    pickle.__________

# 预测并保存结果
y_pred = __________
pd.DataFrame(y_pred, columns=['预测结果']).to_csv('2.2.1_results.txt', index=False)

# 生成测试报告
report = classification_report(y_test, y_pred, zero_division=1)
with open('2.2.1_report.txt', 'w') as file:
    file.write(report)

# 分析测试结果
accuracy = __________
print(f"模型准确率: {accuracy:.2f}")

# 处理数据不平衡
smote = SMOTE(random_state=42)
X_resampled, y_resampled = __________

# 重新训练模型
__________
# 重新预测
y_pred_resampled = __________

# 保存新结果
pd.DataFrame(y_pred_resampled, columns=['预测结果']).to_csv('2.2.1_results_xg.txt', index=False)

# 生成新的测试报告
report_resampled = classification_report(y_test, y_pred_resampled, zero_division=1)
with open('2.2.1_report_xg.txt', 'w') as file:
    file.write(report_resampled)

# 分析新的测试结果
accuracy_resampled = __________
print(f"重新采样后的模型准确率: {accuracy_resampled:.2f}")
```

---

### 四、智能系统设计-智能系统监控与优化（15分）  
**题号：3.1.1 智能音箱产品的数据分析与优化**

根据给定业务与监控信息，分析系统瓶颈并提出优化方案。方案需覆盖性能、稳定性和用户体验提升方向，并说明预期改进效果。  
素材路径：`practices/3.1.1_智能音箱产品的数据分析与优化/exam_preview.html`

#### 任务说明（摘自考试预览）

- 背景：围绕智能音箱产品持续优化，基于用户行为数据挖掘偏好、使用模式和潜在痛点。
- 数据集：`智能音箱数据集.xlsx`。
- 任务1：从用户使用习惯、功能使用频率、响应时间三方面完成分析，输出报告 `3.1.1-1.docx`。
- 任务2：提出3个优化方向及对应解决方案，输出 `3.1.1-2.docx`。
- 所有结果文件存入考生文件夹（命名“准考证号+身份证号后六位”）。
- 上传要求：上传 `3.1.1.docx`。

#### 答题模板（完整文本）

> 说明：题包内存在 `answer_template.docx`，但当前环境无法直接提取 docx 文本内容；以下模板按 `exam_preview.html` 的任务说明与作答要求重组，保持原任务结构用于完整作答。

```text
3.1.1 智能音箱产品的数据分析与优化

一、任务背景
智能音箱作为智能家居生态的重要组成部分，近年来增长迅速。随着NLP和语音识别技术进步，智能音箱已广泛用于音乐播放、天气查询、新闻播报、智能家居控制、提醒和购物等场景。为应对市场竞争，需要通过数据分析持续优化产品性能和用户体验。

二、数据与分析目标
数据集：智能音箱数据集.xlsx
分析目标：
1. 用户使用习惯：分析哪些功能最常被使用；
2. 功能使用频率：识别最受欢迎和较少使用的功能；
3. 响应时间：统计不同功能平均响应时间，定位性能瓶颈。

三、分析报告（对应 3.1.1-1.docx）
（一）用户使用习惯分析
1. 数据口径与统计方法：
2. 主要使用时段/场景：
3. 高频使用人群或行为特征：
4. 结论：

（二）功能使用频率分析
1. 各功能调用次数统计：
2. Top功能与低频功能识别：
3. 可能原因分析：
4. 结论：

（三）响应时间分析
1. 各功能平均响应时间统计：
2. 响应时间分布与异常点：
3. 瓶颈定位（模型、网络、设备或流程）：
4. 结论：

（四）综合结论
1. 关键发现汇总：
2. 对用户体验影响最大的因素：
3. 优先改进建议：

四、优化方向与解决方案（对应 3.1.1-2.docx）
优化方向1：
- 目标：
- 解决方案：
- 预期效果：

优化方向2：
- 目标：
- 解决方案：
- 预期效果：

优化方向3：
- 目标：
- 解决方案：
- 预期效果：

五、提交与命名要求
1. 分析报告文件命名：3.1.1-1.docx
2. 优化方案文件命名：3.1.1-2.docx
3. 按考试平台要求汇总到：3.1.1.docx
4. 文件保存路径：桌面考生文件夹（命名“准考证号+身份证号后六位”）
```

---

### 五、智能系统设计-人机交互流程设计（20分）  
**题号：3.2.1 图像识别评估系统交互流程设计**

请设计图像识别评估系统的人机交互流程。需包含界面要素、输入上传、模型加载、推理结果展示、帮助支持与反馈闭环。  
素材路径：`practices/3.2.1_图像识别评估系统交互流程设计/exam_preview.html`

#### 任务说明（摘自考试预览）

- 背景：基于深度学习图像识别评估系统，模型为 `resnet.onnx`，标签文件为 `labels.txt`。
- 模型使用交互流程：加载模型与标签 -> 加载本地测试图 `img_test.jpg` 并预处理 -> 模型识别 -> 输出 top5 类别及概率。
- 任务1：补全 `3.2.1.ipynb`，实现本地图像识别，截图保存为 `3.2.1-1.jpg`。
- 任务2：基于上述流程给出一种最优人机交互方式，保存为 `3.2.1.docx`。
- 结果导出：代码及运行结果导出为 `3.2.1.html`。
- 文件保存：所有结果存入考生文件夹（命名“准考证号+身份证号后六位”）。

#### 代码文件（完整代码）

```python
import onnxruntime as ort
import numpy as np
import scipy.special
from PIL import Image


# 预处理图像
def preprocess_image(image, resize_size=256, crop_size=224, mean=[0.485, 0.456, 0.406], std=[0.229, 0.224, 0.225]):
  image = image.resize((resize_size, resize_size), Image.BILINEAR)
  w, h = image.size
  left = (w - crop_size) / 2
  top = (h - crop_size) / 2
  image = image.crop((left, top, left + crop_size, top + crop_size))
  image = np.array(image).astype(np.float32)
  image = image / 255.0
  image = (image - mean) / std
  image = np.transpose(image, (2, 0, 1))
  image = image.reshape((1,) + image.shape)
  return image


# 模型加载 2分
session = _________________


# 加载类别标签
labels_path = 'labels.txt'
with open(labels_path) as f:
  labels = [line.strip() for line in f.readlines()]


# 获取模型输入和输出的名称
input_name = session.get_inputs()[0].name
output_name = session.get_outputs()[0].name


# 加载图片 2分
image = _________________('RGB')


# 预处理图片 2分
processed_image = _________________


# 确保输入数据是 float32 类型
processed_image = processed_image.astype(np.float32)


# 进行图片识别 2分
output = _________________([output_name], {input_name: processed_image})[0]


# 应用 softmax 函数获取概率 2分
probabilities = _________________(output, axis=-1)


# 获取最高的5个概率和对应的类别索引 3分
top5_idx = _________________[-5:][::-1]
top5_prob = _________________


# 打印结果
print("Top 5 predicted classes:")
for i in range(5):
  print(f"{i+1}: {labels[top5_idx[i]]} - Probability: {top5_prob[i]}")
```

---

### 六、培训与指导（5分）  
**题号：4.1.1 Label studio培训大纲编写**

请编写面向目标学员的培训大纲，包含培训目标、核心内容模块、实操安排与考核方式。  
素材路径：`practices/4.1.1_Label studio培训大纲编写/exam_preview.html`

#### 任务说明（摘自考试预览）

- 背景：A企业为康复训练机构，计划通过人工智能技术为康复患者提供个性化训练计划并监控训练效果，需要培训新进技术人员进行数据标注。
- 培训目标：使新进技术人员掌握 Label studio 标注工具，能够进行文本、图像、视频、音频标注，达到人工智能训练师五级/初级工水平。
- 工作任务：按要求补全素材 `4.1.1.docx` 中的培训大纲。
- 上传要求：提交 `4.1.1.docx`。

#### 答题模板（完整文本）

```text
4.1.1 Label studio培训大纲编写

一、培训背景
A企业是一家康复训练机构，需要利用人工智能技术为康复患者提供个性化康复训练计划，并实时监控训练效果。为提高人工智能应用效果，拟对新进技术人员开展数据标注培训。

二、培训目标
1. 掌握 Label studio 的基本功能与操作流程；
2. 能够完成文本、图像、视频、音频四类数据标注；
3. 达到人工智能训练师五级/初级工技能水平；
4. 具备在康复训练业务场景中执行数据标注任务的能力。

三、培训对象
新进技术人员（具备基础计算机操作能力）。

四、培训内容模块
模块1：数据标注基础与规范
- 标注概念、标注流程、质量控制要点
- 康复业务场景中的数据标注要求

模块2：Label studio 工具基础
- 项目创建与任务导入
- 标注界面配置与标签体系设置
- 标注结果导出与管理

模块3：文本标注实操
- 文本分类、实体标注、关系标注
- 常见错误与纠正方法

模块4：图像标注实操
- 框选、分割、关键点等标注方式
- 多目标/复杂场景标注规范

模块5：视频标注实操
- 目标跟踪与时间片段标注
- 连续帧一致性控制

模块6：音频标注实操
- 语音片段切分、语义/情感标注
- 音频噪声与异常片段处理

五、实操安排
1. 训练任务1：文本数据标注练习；
2. 训练任务2：图像数据标注练习；
3. 训练任务3：视频与音频数据标注练习；
4. 每个任务包含：讲解 -> 演示 -> 独立操作 -> 讲评反馈。

六、考核方式
1. 过程考核：出勤、课堂练习完成度、规范执行情况；
2. 结果考核：提交标注成果并检查准确率、一致性、完整性；
3. 综合评定：理论理解 + 实操表现 + 质量达标情况。

七、培训产出
1. 形成可复用的标注规范与作业模板；
2. 新进技术人员具备独立完成基础标注任务能力；
3. 为后续模型训练提供质量可控的数据基础。

八、提交要求
将培训大纲整理到答题文件并命名为：4.1.1.docx。
```
