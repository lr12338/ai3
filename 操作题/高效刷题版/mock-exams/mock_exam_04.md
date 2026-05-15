# 人工智能三级模拟试卷（第04套）

## 考试说明

- 本卷共 6 道大题，满分 100 分。
- 本卷仅提供题目，不提供参考答案。
- 请结合各题包内 `exam_preview.html` 完成作答。

## 题目

### 一、业务分析（25分）  
**题号：1.2.4 智能卖点生成系统业务模块效果优化**

素材路径：`practices/1.2.4_智能卖点生成系统业务模块效果优化/exam_preview.html`

#### 任务说明（摘自考试预览）

- 任务背景：当前智能卖点生成系统存在卖点生成不准确、缺乏个性化定制等问题，影响用户体验与服务质量。
- 作答任务（1）：列举用户反映最强烈的几个问题，并解释这些问题为何引发不满、如何影响使用体验。
- 作答任务（2）：设计业务模块优化方案，给出关键实施步骤，并描述预期优化效果。
- 作答文件与题号要求：
  - 任务（1）写入 `1.2.4.docx`，题号标注为 `1.2.4-1`。
  - 任务（2）写入 `1.2.4.docx`，题号标注为 `1.2.4-2`。
- 上传要求：上传 `1.2.4.docx`。
- 考核时间：30min。

#### 答题模板（完整文本）

```text
【题号 1.2.4-1】智能卖点生成系统业务模块问题分析

一、用户反映最强烈的问题
1. 问题1：
2. 问题2：
3. 问题3：
4. （可选）问题4：

二、问题引发不满的原因分析
1. 问题1对应影响：
   - 对准确性的影响：
   - 对响应速度的影响：
   - 对交互体验的影响：
   - 对个性化体验的影响：
2. 问题2对应影响：
3. 问题3对应影响：
4. （可选）问题4对应影响：

三、对系统服务质量的总体影响
1. 用户满意度变化：
2. 业务转化影响：
3. 复购/留存影响：

【题号 1.2.4-2】智能卖点生成系统业务模块优化方案

一、优化目标
1. 提升卖点生成准确性：
2. 提升响应效率：
3. 提升个性化程度：
4. 提升交互体验：

二、关键实施步骤
1. 现状诊断与数据采集：
2. 规则与模型协同优化：
3. 用户画像与个性化策略建设：
4. 人机交互流程优化：
5. A/B测试与迭代优化：

三、保障机制
1. 数据质量保障：
2. 效果评估指标：
3. 风险控制措施：

四、预期优化效果
1. 准确率改善预期：
2. 响应时间改善预期：
3. 个性化命中率改善预期：
4. 用户满意度改善预期：
5. 业务指标改善预期：
```

---

### 二、智能训练-数据处理规范制定（15分）  
**题号：2.1.4 医疗研究数据清洗和标注设计**

素材路径：`practices/2.1.4_医疗研究数据清洗和标注设计/exam_preview.html`

#### 任务说明（摘自考试预览）

- 数据集：医疗研究训练集共 5441 条记录。
- 补全 `2.1.4.ipynb`，完成以下任务：
  1. 加载数据集，查看数据类型、表结构、每列空缺值数量。
  2. 将“就诊日期”“诊断日期”规范为 `yyyy-mm-dd`，并将“病人ID”改列名为“患者ID”。
  3. 增加“诊断延迟（诊断日期-就诊日期）”和“病程（当前日期-诊断日期）”，删除不合理数据（如负数、年龄异常）。
  4. 检查并删除重复值，记录删除行数。
  5. 对 `[年龄, 体重, 身高]` 进行归一化处理。
  6. 统计不同疾病类型的治疗结果分布并绘制柱状图。
  7. 分析年龄与疾病严重程度关系并绘制散点图。
  8. 保存清洗结果为 `2.1.4_cleaned_data.csv`。
  9. 制定数据清洗与数据标注规范，写入 `2.1.4.docx`。
  10. 将代码及运行结果导出为 `2.1.4.html`。
- 文件夹要求：所有结果保存到考生文件夹（命名“准考证号+身份证后6位”）。
- 上传要求：上传 `2.1.4.html`、`2.1.4.docx`。
- 考核时间：20min。

#### 代码文件（完整代码）

```python
import pandas as pd

# 加载数据集并指定编码为gbk
data = _________

# 查看数据类型
print(data.dtypes)
# 查看表结构基本信息
print(_________)

# 显示每一列的空缺值数量
print(data.isnull().sum())

# 规范日期格式
data['就诊日期'] = pd.to_datetime(data['就诊日期'])
data['诊断日期'] = pd.to_datetime(data['诊断日期'])

# 修改列名
_________(_________, inplace=True)

# 查看修改后的表结构
print(data.head())

from datetime import datetime

# 增加诊断延迟和病程列
data['诊断延迟'] = _________.dt.days
data['病程'] = (datetime(2024, 9, 1) - data['诊断日期']).dt.days

# 删除不合理的数据
data = _________[(_________ >= 0) & (_________ > 0) & (_________ < 120)]

# 查看修改后的数据
print(data.describe())

# 删除重复值并记录删除的行数
initial_rows = data.shape[0]
_________(inplace=True)
deleted_rows = initial_rows - data.shape[0]

print(f'删除的重复行数: {deleted_rows}')

from sklearn.preprocessing import MinMaxScaler

# 对需要归一化的列进行处理
scaler = MinMaxScaler()
columns_to_normalize = [_________]
data[columns_to_normalize] = _________

# 查看归一化后的数据
print(data.head())

import matplotlib.pyplot as plt
import matplotlib.font_manager as fm


# 统计治疗结果分布
treatment_outcome_distribution = data.groupby('疾病类型')['治疗结果'].value_counts().unstack()

# 设置中文字体
font_path = 'C:/Windows/Fonts/simhei.ttf'  # 根据你的系统调整字体路径
my_font = fm.FontProperties(fname=font_path)

# 绘制柱状图
_________(_________, stacked=True)
plt.title('不同疾病类型的治疗结果分布', fontproperties=my_font)
plt.xlabel('疾病类型', fontproperties=my_font)
plt.ylabel('治疗结果数量', fontproperties=my_font)
plt.xticks(fontproperties=my_font)  # 设置x轴刻度标签的字体
plt.yticks(fontproperties=my_font)  # 设置y轴刻度标签的字体
plt.legend(prop=my_font)  # 设置图例字体
plt.show()

# 绘制散点图
_________(_________, _________)
plt.title('年龄和疾病严重程度的关系', fontproperties=my_font)
plt.xlabel('年龄', fontproperties=my_font)
plt.ylabel('疾病严重程度', fontproperties=my_font)
plt.xticks(fontproperties=my_font)  # 设置x轴刻度标签的字体
plt.yticks(fontproperties=my_font)  # 设置y轴刻度标签的字体
plt.legend(prop=my_font)  # 设置图例字体
plt.show()

# 保存处理后得数据
output_path = '2.1.4_cleaned_data.csv'
_________(_________, index=False)
```

---

### 三、智能训练-算法测试（20分）  
**题号：2.2.4 低碳生活行为影响因素预测线性回归模型开发与测试**

素材路径：`practices/2.2.4_低碳生活行为影响因素预测线性回归模型开发与测试/exam_preview.html`

#### 任务说明（摘自考试预览）

- 数据集：大学生低碳生活行为影响因素数据集。
- 补全 `2.2.4.ipynb`，完成以下任务：
  1. 正确加载数据并显示前五行。
  2. 使用线性回归完成建模训练；保存模型为 `2.2.4_model.pkl`，结果为 `2.2.4_results.txt`。
  3. 使用测试工具测试模型，保存测试结果为 `2.2.4_report.txt`。
  4. 对测试结果进行模型性能评估、错误分析、改进建议，写入 `2.2.4.docx`。
  5. 使用工具分析并纠正错误案例，重新训练后保存 `2.2.4_results_xg.txt`。
  6. 导出代码和运行结果为 `2.2.4.html`。
- 文件夹要求：所有结果保存到考生文件夹（命名“准考证号+身份证后6位”）。
- 上传要求：上传 `2.2.4.html`、`2.2.4.docx`。
- 考核时间：20min。

#### 代码文件（完整代码）

```python
import pandas as pd
from sklearn.model_selection import train_test_split
from sklearn.linear_model import LinearRegression
from sklearn.metrics import mean_squared_error, r2_score
import joblib
from xgboost import XGBRegressor

# 加载数据集
data = __________

# 显示数据集的前五行
print(__________)

# 删除不必要的列并处理分类变量
data_cleaned = __________(__________=['序号', '所用时间'])  # 删除不必要的列
data_cleaned = pd.get_dummies(data_cleaned, drop_first=True)  # 将分类变量转换为哑变量/指示变量

# 定义目标变量和特征
target = '5.您进行过绿色低碳的相关生活方式吗?'  # 确保这是目标变量

# 定义自变量和因变量
X = __________(__________=__________)
y = __________

# 将数据拆分为训练集和测试集（测试集占20%）
X_train, X_test, y_train, y_test = __________(__________, random_state=42)

# 初始化线性回归模型
model = __________
# 训练线性回归模型
__________

# 保存训练好的模型
model_filename = '2.2.4_model.pkl'
joblib.__________

# 进行预测
y_pred = __________

# 将结果保存到文本文件中
results = pd.DataFrame({'实际值': y_test, '预测值': y_pred})
results_filename = '2.2.4_results.txt'
__________(__________, index=False, sep='\t')  # 使用制表符分隔值保存到文本文件

# 将测试结果保存到报告文件中
report_filename = '2.2.4_report.txt'
with open(report_filename, 'w') as f:
    f.write(f'均方误差: {__________}\n')
    f.write(f'决定系数: {__________}\n')
    
# 分析并纠正错误（示例：使用XGBoost）
# 初始化XGBoost模型（设定树的数量为1000，学习率为0.05，每棵树的最大深度为5，）
xgb_model = __________(__________, subsample=0.8, colsample_bytree=0.8)
# 训练XGBoost模型
__________

# 使用XGBoost模型进行预测
y_pred_xg = __________

# 将XGBoost结果保存到文本文件中
results_xg_filename = '2.2.4_results_xg.txt'
results_xg = pd.DataFrame({'实际值': y_test, '预测值': y_pred_xg})
results_xg.to_csv(results_xg_filename, index=False, sep='\t')  # 使用制表符分隔值保存到文本文件

# 将XGBoost测试结果保存到报告文件中
report_filename_xgb = '2.2.4_report_xgb.txt'
with open(report_filename_xgb, 'w') as f:
    f.write(f'均方误差: {__________}\n')
    f.write(f'决定系数: {__________}\n')
```

---

### 四、智能系统设计-智能系统监控与优化（15分）  
**题号：3.1.4 智能健康监测系统的数据分析与优化**

素材路径：`practices/3.1.4_智能健康监测系统的数据分析与优化/exam_preview.html`

#### 任务说明（摘自考试预览）

- 数据集：`智能健康监测系统数据集.xlsx`。
- 作答任务（1）：从以下三方面做分析并形成报告：
  - 用户活动周期：分析一天中不同时间段健康指标变化趋势，识别高风险时段与安全时段。
  - 健康指标偏好度：识别受用户青睐与使用较少的监测功能（如血压、血糖、体脂分析）。
  - 系统响应与准确性：评估各指标监测响应时间，识别导致误报或延迟的关键因素。
- 作答任务（2）：提出 3 个优化方向及对应解决方案，提升功能性与用户友好性。
- 作答文件要求：
  - 任务（1）保存为 `3.1.4-1.docx`。
  - 任务（2）保存为 `3.1.4-2.docx`。
- 文件夹要求：所有结果保存到考生文件夹（命名“准考证号+身份证号后六位”）。
- 上传要求：上传 `3.1.4.docx`。
- 考核时间：20min。

#### 答题模板（完整文本）

```text
【题号 3.1.4-1】智能健康监测系统数据分析报告

一、数据说明
1. 数据来源：智能健康监测系统数据集.xlsx
2. 分析目标：
3. 分析方法与工具：

二、用户活动周期分析
1. 不同时间段健康指标变化趋势：
2. 高风险时段识别：
3. 安全时段识别：
4. 结论与建议：

三、健康指标偏好度分析
1. 各监测功能使用频次/偏好排序：
2. 受用户青睐的功能及原因：
3. 使用较少功能及原因：
4. 优化建议：

四、系统响应与准确性分析
1. 各指标响应时间评估：
2. 误报/延迟关键因素分析：
3. 影响优先级判断：
4. 结论与建议：

五、综合结论
1. 关键发现：
2. 风险点汇总：
3. 阶段性改进建议：

【题号 3.1.4-2】智能健康监测系统优化方案

一、优化方向1
1. 优化目标：
2. 具体方案：
3. 实施步骤：
4. 预期效果：

二、优化方向2
1. 优化目标：
2. 具体方案：
3. 实施步骤：
4. 预期效果：

三、优化方向3
1. 优化目标：
2. 具体方案：
3. 实施步骤：
4. 预期效果：

四、实施保障
1. 人员与协同：
2. 数据与系统支持：
3. 评估指标与验收标准：
```

---

### 五、智能系统设计-人机交互流程设计（20分）  
**题号：3.2.4 花朵智能识别系统交互流程设计**

素材路径：`practices/3.2.4_花朵智能识别系统交互流程设计/exam_preview.html`

#### 任务说明（摘自考试预览）

- AI 模型说明：
  - 模型：`flower-detection.onnx`（基于 Pytorch 训练）
  - 标签：`labels.txt`
  - 测试图片：`flower_test.png`
- 模型使用交互流程要求：
  1. 加载模型 `flower-detection.onnx` 与标签 `labels.txt`。
  2. 加载本地图片 `flower_test.png` 并完成预处理。
  3. 使用模型进行识别推理。
  4. 输出预测类型与识别准确率。
- 作答任务：
  1. 补全 `3.2.4.ipynb` 对应 Python 代码，实现本地图片识别，并将识别结果截图保存为 `3.2.4-1.jpg`。
  2. 基于上述流程，给出一种人机交互最优流程，保存为 `3.2.4.docx`。
- 文件夹要求：所有结果保存到考生文件夹（命名“准考证号+身份证号后六位”）。
- 上传要求：上传 `3.2.4.html`、`3.2.4.docx`、`3.2.4-1.jpg`。
- 考核时间：20min。

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


# 加载模型  2分
session = _________________


# 加载类别标签 2分
with _________________ as f:
    labels = [line.strip() for line in f.readlines()]


# 获取模型输入和输出的名称
input_name = session.get_inputs()[0].name
output_name = session.get_outputs()[0].name


# 加载图片  2分
image = _________________('RGB')


# 预处理图片  2分
processed_image = _________________


# 确保输入数据是 float32 类型
processed_image = processed_image.astype(np.float32)


# 进行图片识别  2分
output = _________________([output_name], {input_name: processed_image})[0]


# 应用 softmax 函数获取识别分类后的准确率  2分
accuracy = _________________(output, axis=-1)


# 获取预测的类别索引
predicted_idx =  __________


# 获取预测的准确值（转换为百分比）
prob_percentage =  __________


# 获取预测的类别标签
predicted_label = __________


# 输出预测结果，包含百分比形式的概率
print(f"Predicted class: {predicted_label}, Accuracy: {prob_percentage:.2f}%")
```

---

### 六、培训与指导（5分）  
**题号：4.2.4 自动驾驶汽车感知系统数据采集与标注指导**

素材路径：`practices/4.2.4_自动驾驶汽车感知系统数据采集与标注指导/exam_preview.html`

#### 任务说明（摘自考试预览）

- 业务背景：自动驾驶感知系统需通过摄像头、雷达、激光雷达等采集环境数据，并依赖高质量标注训练 AI 算法。
- 业务需求关键信息：
  1. 数据多样性：覆盖不同天气、时段、地域与驾驶场景。
  2. 高精度标注：车辆、行人、自行车、动物、交通标志、车道线、红绿灯等。
  3. 实时数据处理：支持传感器数据流实时接收与处理。
  4. 数据安全性：保障采集、传输、存储合规与安全。
  5. 高效数据管理：支持检索、构建、清洗、版本控制。
  6. 持续学习与更新：支持持续训练优化以适配道路环境与规则变化。
- 作答任务：根据上述业务需求，补全素材文件夹中的 `4.2.4.docx`（数据采集与标注指导方案）。
- 文件夹要求：所有结果保存到考生文件夹（命名“准考证号+身份证号后六位”）。
- 上传要求：上传 `4.2.4.docx`。
- 考核时间：10min。

#### 答题模板（完整文本）

```text
【题号 4.2.4】自动驾驶汽车感知系统数据采集与标注指导方案

一、目标与适用范围
1. 指导目标：
2. 适用场景：
3. 适用角色（五级/初级工、四级/中级工等）：

二、数据采集指导
1. 采集任务规划：
   - 天气覆盖：
   - 时间覆盖：
   - 地域覆盖：
   - 场景覆盖（城市道路/高速/乡村/隧道/夜间等）：
2. 传感器配置与同步：
   - 摄像头：
   - 雷达/激光雷达：
   - 时间戳同步：
3. 采集流程规范：
   - 采集前检查：
   - 采集中监控：
   - 采集后验收：
4. 数据安全与合规：
   - 隐私保护：
   - 传输加密：
   - 存储权限控制：

三、数据标注指导
1. 标注对象与类别体系：
   - 车辆、行人、自行车、动物、交通标志、车道线、红绿灯等。
2. 标注规则与精度标准：
   - 边界框/语义分割/关键点规则：
   - 遮挡、模糊、小目标处理规则：
3. 标注流程：
   - 任务分发：
   - 初标：
   - 复核：
   - 终审：
4. 常见问题与处理：
   - 类别混淆：
   - 漏标与重标：
   - 低质量样本处理：

四、质量控制与数据管理
1. 质检机制：
   - 抽检比例：
   - 一致性检查：
   - 返工机制：
2. 数据管理机制：
   - 数据检索：
   - 数据清洗：
   - 数据集版本控制：
3. 指标体系：
   - 标注准确率：
   - 一致性指标：
   - 交付及时率：

五、持续优化与协作机制
1. 错例回流与持续学习机制：
2. 模型迭代驱动的数据补采策略：
3. 团队协作分工与沟通机制：
4. 培训与指导安排：

六、交付物清单
1. 数据采集记录：
2. 标注规范文档：
3. 质检报告：
4. 版本记录：
```
