# 人工智能三级模拟试卷（第05套）

## 考试说明

- 本卷共 6 道大题，满分 100 分。
- 本卷仅提供题目，不提供参考答案。
- 请结合各题包内 `exam_preview.html` 完成作答。

## 题目

### 一、业务分析（25分）  
**题号：1.1.5 智能交通系统的数据采集、处理和审核流程设计**

请围绕智能交通场景，设计数据采集、处理与审核流程。要求体现流程完整性、规范性与业务闭环可追踪性。  
素材路径：`practices/1.1.5_智能交通系统的数据采集、处理和审核流程设计/exam_preview.html`

任务说明（摘自考试预览）：
- 某智能交通系统希望通过车辆行驶数据进行交通流量预测和拥堵预警，需对 `vehicle_traffic_data.csv` 完成采集、清洗、审核和预处理。
- 字段包括：`VehicleID`、`DriverName`、`Age`、`Gender`、`Speed`、`TravelDistance`、`TravelTime`、`TrafficEvent`。
- （1）数据采集：运行 `1.1.5.ipynb` 读取本地文件并加载到 DataFrame，显示前 5 行并截图保存为 `1.1.5-1.jpg`。
- （2）数据清洗与预处理：删除缺失值、转换字段类型、删除异常年龄/车速/行驶距离/行驶时间；保存清洗后文件 `cleaned_vehicle_traffic_data.csv`。
- （3）数据合理性审核：按区间审核并标记不合理数据（年龄 18-70、车速 0-200、行驶距离 1-1000、行驶时间 1-1440），截图保存 `1.1.5-2.jpg`。
- （4）数据统计：统计交通事件次数、不同性别平均车速/距离/时长、不同年龄段人数（18-25、26-35、36-45、46-55、56-65、65+），截图保存 `1.1.5-3.jpg`、`1.1.5-4.jpg`、`1.1.5-5.jpg`。
- 所有结果保存在桌面考生文件夹（命名“准考证号+身份证号后六位”）。

代码文件（完整代码）：
```python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt

# 1. 数据采集
# 从本地文件中读取数据  2分
data = _____________
print("数据采集完成，已加载到DataFrame中")

# 打印数据的前5条记录 2分
print(_____________)

# 2. 数据清洗与预处理
# 处理缺失值（删除）  2分
data = _____________

# 数据类型转换
data_____________ = _____________(int)       #Age数据类型转换为int 1分
data_____________ = _____________(float)     #Speed数据类型转换为float 1分
data_____________ = _____________(float)     #TravelDistance数据类型转换为float 1分
data_____________ = _____________(float)     #TravelTime数据类型转换为float 1分

# 处理异常值  2分
data = data[(_____________(18, 70))  & 
            (_____________(0, 200)) & 
            (_____________(1, 1000)) & 
            (_____________(1, 1440))]

# 保存清洗后的数据  1分
_____________('cleaned_vehicle_traffic_data.csv', index=False)
print("数据清洗完成，已保存为 'cleaned_vehicle_traffic_data.csv'")

# 3. 数据合理性审核
# 审核字段合理性 1分
unreasonable_data = data[~((_____________(18, 70)) & 
                           (_____________(0, 200)) & 
                           (_____________(1, 1000)) & 
                           (_____________(1, 1440)))]
print("不合理的数据:\n", unreasonable_data)

# 4. 数据统计
# 统计每种交通事件的发生次数  2分
traffic_event_counts = _____________
print("每种交通事件的发生次数:\n", traffic_event_counts)

# 统计不同性别的平均车速、行驶距离和行驶时间  2分
gender_stats = data._____________._____________
print("不同性别的平均车速、行驶距离和行驶时间:\n", gender_stats)

# 统计不同年龄段的驾驶员数  5分
age_bins = [18, 26, 36, 46, 56, 66, np.inf]
age_labels = ['18-25', '26-35', '36-45', '46-55', '56-65', '65+']
data['AgeGroup'] = _____________(_____________,_____________,_____________, right=False)
age_group_counts = _____________
print("不同年龄段的驾驶员数:\n", age_group_counts)
```

---

### 二、智能训练-数据处理规范制定（15分）  
**题号：2.1.5 健康与营养咨询数据预处理与数据规范设计**

完成健康与营养咨询数据预处理规范设计，需覆盖缺失值处理、类型转换、异常检查、统计分析与图表验证。  
素材路径：`practices/2.1.5_健康与营养咨询数据预处理与数据规范设计/exam_preview.html`

任务说明（摘自考试预览）：
- 在健康与营养咨询场景下，补全 `2.1.5.ipynb`，对健康咨询客户数据集完成数据预处理与规范制定。
- 具体任务：加载数据并查看类型/结构/空缺值；删除缺失行；将 `Your age` 转为整数并处理异常；去重并记录删除行数；对 “How do you describe your current level of fitness ?” 做归一化；绘制健身频率饼图；进行数据标注划分。
- 保存处理后数据为 `2.1.5_cleaned_data.csv`，并编写数据清洗与数据标注规范到 `2.1.5.docx`。
- 将代码和运行结果导出为 `2.1.5.html`，所有文件放入桌面考生文件夹（命名“准考证号+身份证后6位”）。

代码文件（完整代码）：
```python
import pandas as pd

# 加载数据集
data = __________

# 查看表结构基本信息
print(__________)

# 显示每一列的空缺值数量
print(__________)

# 删除含有缺失值的行
data_cleaned = __________

# 转换 'Your age' 列的数据类型为整数类型，并处理异常值
data_cleaned.loc[:, 'Your age'] = __________(__________, errors='coerce')
data_cleaned = data_cleaned.dropna(subset=['Your age'])
data_cleaned = data_cleaned[data_cleaned['Your age'] >= 0]
data_cleaned.loc[:, 'Your age'] = data_cleaned['Your age'].__________

print(data_cleaned['Your age'].dtype)

# 检查和删除重复值
duplicates_removed = data_cleaned.duplicated().sum()
data_cleaned = __________

print(f"Removed {duplicates_removed} duplicate rows")

from sklearn.preprocessing import LabelEncoder

# 归一化 'How do you describe your current level of fitness ?' 列
label_encoder = LabelEncoder()
data_cleaned[__________] = __________

print(data_cleaned['How do you describe your current level of fitness ?'].unique())

from sklearn.preprocessing import LabelEncoder
import matplotlib.pyplot as plt

# 去掉列名中的空格
data.columns = data.columns.str.strip()
# 显示数据集的列名
print(data.columns)

# 删除包含缺失值的行
data_cleaned = data.dropna(subset=['How often do you exercise?'])

# 统计不同健身频率的分布情况
exercise_frequency_counts = data_cleaned['How often do you exercise?'].value_counts()

# 绘制饼图
plt.figure(figsize=(10, 6))
__________(autopct='%1.1f%%', startangle=90, colors=plt.cm.Paired.colors)
plt.title('Distribution of Exercise Frequency')
plt.ylabel('')
plt.show()

import pandas as pd
from sklearn.model_selection import train_test_split
import matplotlib.pyplot as plt

# 填充缺失值
data_filled = data.apply(lambda x: x.fillna(x.mode()[0]))

# 划分数据（测试集占比20%）
train_data, test_data = __________(__________, random_state=42)

# 保存处理后的数据
cleaned_file_path = '__________'
__________(__________, index=False)
```

---

### 三、智能训练-算法测试（20分）  
**题号：2.2.5 智能步数预测模型开发与测试**

请完成步数预测模型开发与测试，说明训练流程、评估指标、测试结论及后续优化方向。  
素材路径：`practices/2.2.5_智能步数预测模型开发与测试/exam_preview.html`

任务说明（摘自考试预览）：
- 根据预处理好的 `fitness analysis` 数据集，补全 `2.2.5.ipynb`，开发每日步数预测模型并完成测试分析。
- （1）正确加载数据并显示前 5 行。
- （2）使用决策树模型，以 `daily_steps` 为目标变量完成训练；保存模型为 `2.2.5_model.pkl`，结果文件为 `2.2.5_results.txt`。
- （3）使用测试工具测试并保存报告 `2.2.5_report.txt`。
- （4）对测试结果进行性能评估、错误分析和改进建议，写入 `2.2.5.docx`。
- （5）将代码与运行结果导出为 `2.2.5.html`，并保存到桌面考生文件夹（命名“准考证号+身份证后6位”）。

代码文件（完整代码）：
```python
import pandas as pd
from sklearn.model_selection import train_test_split
from sklearn.tree import DecisionTreeRegressor
import pickle
from sklearn.metrics import mean_squared_error, mean_absolute_error, r2_score

# 加载数据集
df = __________

# 显示前五行数据
print(__________)

# 选择相关特征进行建模
X = df[['Your gender ', 'How important is exercise to you ?', 'How healthy do you consider yourself?']]
X = __________(X)  # 将分类变量转为数值变量

# 设置目标变量
y = __________  

# 将数据集划分为训练集和测试集（测试集占20%）
X_train, X_test, y_train, y_test = __________(__________, random_state=42)

# 创建并训练决策树回归模型
__________ = __________(random_state=42)
# 训练决策树回归模型
__________

# 保存训练好的模型
with open('2.2.5_model.pkl', 'wb') as model_file:
    pickle.__________

# 进行预测
y_pred = __________

# 将结果保存到文本文件中
results = pd.DataFrame({'实际值': y_test, '预测值': y_pred})
results_filename = '2.2.5_results.txt'
__________(__________, index=False, sep='\t')  

# 将测试结果保存到报告文件中
report_filename = '2.2.5_report.txt'
with open(__________) as f:
    f.write(f'均方误差: {__________}\n')
    f.write(f'平均绝对误差: {__________}\n')
    f.write(f'决定系数: {__________}\n')
```

---

### 四、智能系统设计-智能系统监控与优化（15分）  
**题号：3.1.5 智能家居环境控制系统的数据分析与优化**

基于系统运行特征，分析节能与调度方面的问题，提出系统性能优化、智能调度和个性化服务优化方案。  
素材路径：`practices/3.1.5_智能家居环境控制系统的数据分析与优化/exam_preview.html`

任务说明（摘自考试预览）：
- 基于 `智能家居环境控制系统数据集.xlsx`，围绕用户环境偏好、系统响应时间、能源消耗三方面完成分析。
- 分析要求：
  - 用户环境偏好：分析一天不同时段对温度、湿度、光照强度的偏好设置；
  - 系统响应时间：评估用户操作到系统反馈的平均延迟并找出影响因素；
  - 能源消耗分析：识别系统平均能耗并寻找节能潜力。
- 形成分析报告并保存为 `3.1.5-1.docx`。
- 再给出 3 个优化方向及对应解决方案，保存为 `3.1.5-2.docx`。
- 所有结果文件保存在桌面考生文件夹（命名“准考证号+身份证号后六位”）。

答题模板（完整文本）：
```text
请勿修改答题卷，在指定单元格内填写答案

• 分析报告
用户环境偏好

平均温度
平均湿度
平均光照
06:00 - 12:00

13:00 - 18:00

19:00 - 05:00

系统响应时间
平均响应时间

影响因素

能源消耗分析
平均能源消耗

节能潜力

• 优化方向及解决方案
优化方向1：

对应解决方案1：

优化方向2：

对应解决方案2：

优化方向3：

对应解决方案3：
```

---

### 五、智能系统设计-人机交互流程设计（20分）  
**题号：3.2.5 人脸AI智能检测系统交互流程设计**

请设计人脸检测系统交互流程，覆盖图片输入、模型推理、检测结果展示、结果保存、帮助文档与反馈机制。  
素材路径：`practices/3.2.5_人脸AI智能检测系统交互流程设计/exam_preview.html`

任务说明（摘自考试预览）：
- 基于 `version-RFB-320.onnx` 与 `voc-model-labels.txt`，完成人脸检测交互流程代码补全与交互方案设计。
- 模型使用流程关键要求：
  - 加载 ONNX 模型与类别标签；
  - 读取本地 `imgs` 文件夹全部图片并做预处理；
  - 执行人脸检测；
  - 在图像上绘制人脸框并保存到 `./detect_imgs_results_onnx`；
  - 统计所有图片中检测到的人脸总数并输出。
- 工作任务：
  - 补全 `3.2.5.ipynb`，实现全部图片检测，截图保存 `3.2.5-1.jpg` 并上传检测结果图片；
  - 设计一种基于该模型的人机交互优化方案（界面布局、操作流程等），保存为 `3.2.5.docx`。
- 所有结果文件储存在桌面考生文件夹（命名“准考证号 + 身份证号后六位”）。

代码文件（完整代码）：
```python
import os
import time
import cv2
import numpy as np
import vision.utils.box_utils_numpy as box_utils
import onnxruntime as ort

# 定义预测函数，对模型输出的边界框和置信度进行后处理
def predict(width, height, confidences, boxes, prob_threshold, iou_threshold=0.3, top_k=-1):
    boxes = boxes[0]
    confidences = confidences[0]
    picked_box_probs = []
    picked_labels = []
    for class_index in range(1, confidences.shape[1]):
        probs = confidences[:, class_index]
        mask = probs > prob_threshold
        probs = probs[mask]
        if probs.shape[0] == 0:
            continue
        subset_boxes = boxes[mask, :]
        box_probs = np.concatenate([subset_boxes, probs.reshape(-1, 1)], axis=1)
        box_probs = box_utils.hard_nms(box_probs,
                                       iou_threshold=iou_threshold,
                                       top_k=top_k,
                                       )
        picked_box_probs.append(box_probs)
        picked_labels.extend([class_index] * box_probs.shape[0])
    if not picked_box_probs:
        return np.array([]), np.array([]), np.array([])
    picked_box_probs = np.concatenate(picked_box_probs)
    picked_box_probs[:, 0] *= width
    picked_box_probs[:, 1] *= height
    picked_box_probs[:, 2] *= width
    picked_box_probs[:, 3] *= height
    return picked_box_probs[:, :4].astype(np.int32), np.array(picked_labels), picked_box_probs[:, 4]

# 从标签文件中读取每一行，并去除行首尾的空白字符，得到类别名称列表 2分
class_names = [_______________ for name in open('voc-model-labels.txt').readlines()]

# 创建 ONNX Runtime 的推理会话，用于运行模型进行推理 2分
ort_session = _______________('version-RFB-320.onnx')

# 获取模型输入的名称 2分
input_name = _______________()[0].name

# 定义保存检测结果图像的目录路径
result_path = "./detect_imgs_results_onnx"

# 定义置信度阈值，用于筛选出置信度较高的检测结果
threshold = 0.7
# 定义存储待检测图像的目录路径
path = "imgs"
# 用于统计所有图像中检测到的目标框总数，初始化为 0
sum = 0

# 如果保存结果的目录不存在，则创建该目录 2分
if not os.path.exists(result_path):
    os._______________
    
# 获取指定目录下的所有文件和文件夹名称列表
listdir = os.listdir(path)

# 遍历目录下的每个文件
for file_path in listdir:
    # 拼接图像文件的完整路径
    img_path = os.path.join(path, file_path)
    # 使用 OpenCV 读取图像文件 2分
    orig_image = _______________
    # 将图像从 BGR 颜色空间转换为 RGB 颜色空间（许多模型要求输入为 RGB 格式）
    image = cv2.cvtColor(orig_image, cv2.COLOR_BGR2RGB)
    # 将图像调整为 320x240 的尺寸（符合模型输入的尺寸要求） 2分
    image = _______________(_______________, (320, 240))
    # 定义图像归一化的均值数组 2分
    image_mean = _______________([127, 127, 127])
    # 对图像进行归一化处理，减去均值并除以 128
    image = (image - image_mean) / 128
    # 将图像的维度从 (高度, 宽度, 通道数) 转换为 (通道数, 高度, 宽度)
    image = np.transpose(image, [2, 0, 1])
    # 在第一个维度上扩展一个维度，将图像变为 (1, 通道数, 高度, 宽度)，以符合模型输入的维度要求  1分
    image = _______________(image, axis=0)
    # 将图像数据类型转换为 float32 类型
    image = image.astype(np.float32)
    # 记录开始时间，用于计算模型推理的耗时
    time_time = time.time()
    # 使用 ONNX Runtime 运行模型，输入图像数据，得到模型输出的置信度和边界框  2分
    confidences, boxes = _______________(None, {input_name: image})
    # 计算并打印模型推理的耗时
    print("cost time:{}".format(time.time() - time_time))
    # 调用 predict 函数对模型输出的边界框和置信度进行后处理，得到最终的边界框、类别标签和置信度
    boxes, labels, probs = predict(orig_image.shape[1], orig_image.shape[0], confidences, boxes, threshold)
    # 遍历每个检测到的目标框
    for i in range(boxes.shape[0]):
        # 获取当前目标框的坐标
        box = boxes[i, :]
        # 生成当前目标框的标签字符串，包含类别名称和置信度
        label = f"{class_names[labels[i]]}: {probs[i]:.2f}"

        # 在原始图像上绘制目标框，颜色为 (255, 255, 0)，线条粗细为 4
        cv2.rectangle(orig_image, (box[0], box[1]), (box[2], box[3]), (255, 255, 0), 4)
        # 将绘制了目标框的图像保存到结果目录中
        cv2.imwrite(os.path.join(result_path, file_path), orig_image)
    # 累加当前图像中检测到的目标框数量到总数中
    sum += boxes.shape[0]
# 打印所有图像中检测到的目标框总数
print("sum:{}".format(sum))
```

---

### 六、培训与指导（5分）  
**题号：4.1.5 Python数据可视化培训大纲编写**

请编写 Python 数据可视化培训大纲，需包含教学目标、知识模块、实操安排与学习效果评估方式。  
素材路径：`practices/4.1.5_Python数据可视化培训大纲编写/exam_preview.html`

任务说明（摘自考试预览）：
- A 企业为康复训练机构，计划对新进技术人员进行数据可视化工具使用培训，以提升人工智能技术应用效果。
- 培训目标是让新进人员掌握 Python 数据可视化工具，能够对重要数据进行可视化操作，达到人工智能训练师四级/中级工技能水平。
- 需根据要求补全素材 `4.1.5.docx` 中的培训大纲，并提交 `4.1.5.docx`。

答题模板（完整文本）：
```text
Python数据可视化培训大纲

一、培训背景与目标
1. 培训背景：
   A企业是一家康复训练机构，需要利用人工智能技术为康复患者提供个性化康复训练计划，并实时监控训练效果。企业已采集大量康复数据，现计划开展新进技术人员的数据可视化培训。
2. 总体目标：
   使新进技术人员掌握 Python 数据可视化工具的使用方法，能够对关键康复数据开展可视化分析，达到人工智能训练师四级/中级工技能水平。

二、培训对象
新进技术人员（初级到中级能力梯度）。

三、培训内容模块
1. Python数据可视化基础
   - 可视化在康复数据分析中的作用
   - 常见图表类型与适用场景
2. 常用可视化工具与库
   - Matplotlib 基础绘图
   - Seaborn 统计可视化
   - （可选）Pandas 内置绘图
3. 康复数据可视化实操
   - 关键指标选择（训练频次、时长、效果变化等）
   - 图表设计与结果解读
4. 结果表达与汇报
   - 图表规范、可读性与业务表达

四、培训实施安排
1. 理论讲解
2. 上机实操
3. 案例演练
4. 课堂答疑与复盘

五、考核与评估
1. 过程考核：课堂练习完成情况、规范性与准确性
2. 结果考核：独立完成一份康复数据可视化作业
3. 学习成效评估：是否能正确选择图表、完成可视化并进行结果解释

六、培训输出物
1. 培训讲义（逻辑清晰、语句通顺）
2. 实操示例与作业结果
3. 最终培训大纲文档（4.1.5.docx）
```
