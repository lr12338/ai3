# 人工智能三级模拟试卷（第03套）

## 考试说明

- 本卷共 6 道大题，满分 100 分。
- 本卷仅提供题目，不提供参考答案。
- 请结合各题包内 `exam_preview.html` 完成作答。

## 题目

### 一、业务分析（25分）  
**题号：1.1.3 金融机构信用评估系统中的业务数据审核流程设计**

素材路径：`practices/1.1.3_金融机构信用评估系统中的业务数据审核流程设计/exam_preview.html`

#### 任务说明（摘自考试预览）

某金融机构计划引入智能信用评估系统，通过分析客户的历史交易数据和信用记录，使用机器学习算法预测客户的信用风险等级，从而辅助贷款审批和风险控制。为了确保数据的准确性和可靠性，该机构需要设计并实现一套全面的业务数据审核流程，确保数据在进入信用评估系统之前经过严格的审核和清洗。
我们提供一个客户信用数据集（credit_data.csv），包含以下字段：
CustomerID: 客户ID
Name: 客户姓名
Age: 年龄
Income: 收入
LoanAmount: 贷款金额
LoanTerm: 贷款期限（月）
CreditScore: 信用评分
Default: 是否违约（0: 否，1: 是）
TransactionHistory: 历史交易记录（JSON格式）
你作为人工智能训练师，根据提供的credit_data.csv数据集和Python代码框架（1.1.3.ipynb），完成以下数据的审核和处理任务，确保数据的准确性和可靠性。请按照以下要求完成任务，确保结果准确并保存相应的截图。
（1）数据完整性审核：
通过运行Python代码（1.1.3.ipynb）检查数据集中的每个字段是否存在缺失值和重复值。将上述审核结果截图以jpg的格式保存，命名为“1.1.3-1”。
（2）数据合理性审核：
通过运行Python代码（1.1.3.ipynb）审核以下字段的合理性：
年龄：应在18到70岁之间。
收入：应大于2000。
贷款金额：应小于收入的5倍。
信用评分：应在300到850之间。
对不合理的数据进行标记，并将审核结果截图以jpg的格式保存，命名为“1.1.3-2”。
（3）通过运行Python代码（1.1.3.ipynb）对数据进行清洗，处理异常值。具体要求如下：
将不合理的数据进行标记，并对异常值所在行进行删除；
清洗后的数据保存为新文件cleaned_credit_data.csv。
所有结果文件储存在桌面新建的考生文件夹中，文件夹命名为“准考证号+身份证号后六位”。

注意事项：
考生文件夹可以保存在桌面。
jupyter notebook 工作目录（根目录）：虚拟机环境中的D:\jupyter_notebook。
jupyter notebook 打开方式：在终端中输入jupyter notebook启动。
ipynb填充代码运行后，附带结果保存为html格式上传。保存方法：jupyter notebook中File->Download as->HTML(.html)。
ipynb代码在下划线上填充，请勿随意添加、删除或修改源代码的其他部分，以免影响考试结果。
截图工具：Windows附件->截图工具。截图只截取输出结果部分，其余多余内容不截取。

答案上传要求：
1. 上传1.1.3.html
2. 上传cleaned_credit_data.csv
3. 上传1.1.3-1.jpg
4. 上传1.1.3-2.jpg

#### 代码文件（完整代码）

```python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
# 读取数据集
data = pd.read_csv('data/credit_data.csv')
data.head()

# 1. 数据完整性审核
missing_values = data._________       #数据缺失值统计 2分
duplicate_values = data._________     #数据重复值统计 2分
# 输出结果
print("缺失值统计:")
print(missing_values)
print("重复值统计:")
print(duplicate_values)

# 2. 数据合理性审核
data['is_age_valid'] = _________._________(18, 70)              #Age数据的合理性审核 2分
data['is_income_valid'] = _________ > _________                 #Income数据的合理性审核 2分
data['is_loan_amount_valid'] = _________ < (_________ * 5)      #LoanAmount数据的合理性审核 2分
data['is_credit_score_valid'] = _________._________(300, 850)   #CreditScore数据的合理性审核 2分
# 合理性检查结果
validity_checks = data[['is_age_valid', 'is_income_valid', 'is_loan_amount_valid', 'is_credit_score_valid']].all(axis=1)
data['is_valid'] = validity_checks
# 输出结果
print("数据合理性检查:")
print(data[['is_age_valid', 'is_income_valid', 'is_loan_amount_valid', 'is_credit_score_valid', 'is_valid']].describe())

# 3. 数据清洗和异常值处理
# 标记不合理数据
invalid_rows = data[data['is_valid']]
# 删除不合理数据行
cleaned_data = data[data['is_valid']]
# 删除标记列
cleaned_data = cleaned_data.drop(columns=['is_age_valid', 'is_income_valid', 'is_loan_amount_valid', 'is_credit_score_valid', 'is_valid'])
# 保存清洗后的数据
_________._________(_________, index=False)
print("数据清洗完成，已保存为 'cleaned_credit_data.csv'")
```

---

### 二、智能训练-数据处理规范制定（15分）  
**题号：2.1.3 信用评分模型数据清洗和标注流程设计**

素材路径：`practices/2.1.3_信用评分模型数据清洗和标注流程设计/exam_preview.html`

#### 任务说明（摘自考试预览）

互联网金融飞速发展，使得个人金融理财变得越来越容易。而其中信用评分技术是一种对贷款申请人（信用卡申请人）做风险评估分值的统计模型，可以根据客户提供的资料、客户的历史数据、第三方平台数据（芝麻分、京东、微信等），对客户的信用进行评估。现要求根据提供的Finance数据集，选择合适的特征，开发一个申请的评分模型，对未来一段时间内借贷人出现违约的概率进行预测，对客户信用进行评估打分。提供的数据集样本数据一共15000条，10个自变量，1个因变量（SeriousDlqin2yrs）。在开发评分模型之前，首先要对数据进行数据清洗，请补全2.1.3.ipynb代码完成下面的数据预处理任务，并设计一套标注流程规范：
（1）正确加载数据集，并显示前五行的数据；
（2）检查数据集中的异常值并处理异常值，使用箱线图检测异常值，使用IQR方法处理异常值；
设置图像的尺寸为12英寸宽和8英寸高；
将画布分成3行4列，总共可以容纳12个子图；
（3）检查数据集中的重复值并删除所有重复值，并记录删除的行数；
（4）对数据进行归一化处理；
（5）创建新的特征IncomeToDebtRatio，MonthlyIncome，并添加到数据集中；
（6）将SeriousDlqin2yrs设为目标变量并标注；
（7）对数据进行划分；
（8）保存处理后的数据，并命名为：2.1.3_cleaned_data.csv，保存到考生文件夹；
（9）制定数据清洗和特征工程规范，将答案写到答题卷文件中，答题卷文件命名为“2.1.3.docx”，保存到考生文件夹；
（10）将以上代码以及运行结果，以html格式保存并命名为2.1.3.html，保存到考生文件夹，考生文件夹命名为“准考证号+身份证后6位”。

注意事项：
考生文件夹可以保存在桌面。
jupyter notebook 工作目录（根目录）：虚拟机环境中的D:\jupyter_notebook。
jupyter notebook 打开方式：在终端中输入jupyter notebook启动。
ipynb填充代码运行后，保存为html格式上传。保存方法：jupyter notebook中File->Download as->HTML(.html)。
ipynb代码在下划线上填充，请勿随意添加、删除或修改源代码的其他部分，以免影响考试结果。

答案上传要求：
1. 上传2.1.3.html
2. 上传2.1.3.docx

#### 代码文件（完整代码）

```python
import pandas as pd

# 加载数据
data = __________

# 显示前五行的数据
__________

import matplotlib.pyplot as plt
import seaborn as sns

# 设置图像尺寸
plt.figure(figsize=(12, 8))

# 识别数值列用于箱线图
numeric_cols = data.select_dtypes(include=['float64', 'int64']).columns

# 创建箱线图
for i, col in enumerate(numeric_cols, 1):
    plt.subplot(3, 4, i)
    sns.boxplot(x=data[col])
    plt.title(col)

plt.tight_layout()
plt.show()

# 使用IQR处理异常值
Q1 = __________(0.25)
Q3 = __________(0.75)
IQR = __________

# 移除异常值
data_cleaned = data[~((data[numeric_cols] < (Q1 - 1.5 * __________)) | (data[numeric_cols] > (Q3 + 1.5 * __________))).any(axis=1)]

# 检查处理重复值
duplicates = __________()
num_duplicates = duplicates.sum()
data_cleaned = data_cleaned[~duplicates]

print(f'删除的重复行数: {num_duplicates}')

#对数据进行归一化处理
from sklearn.preprocessing import MinMaxScaler

scaler = MinMaxScaler()
data_cleaned[numeric_cols] = __________

# 设定目标变量
target_variable = __________

from sklearn.model_selection import train_test_split

# 定义特征和目标
X = __________(columns=[__________])   #1分
y = __________                         #1分

# 划分数据（训练集占80%）
X_train, X_test, y_train, y_test = __________(__________, random_state=42)

# 显示划分后的数据形状
print(f'训练数据形状: {X_train.shape}')
print(f'测试数据形状: {X_test.shape}')

# 保存清洗后的数据到CSV
cleaned_file_path = '2.1.3_cleaned_data.csv'
__________(__________, index=False)
```

---

### 三、智能训练-算法测试（20分）  
**题号：2.2.3 日常运动量随机森林预测模型开发与测试**

素材路径：`practices/2.2.3_日常运动量随机森林预测模型开发与测试/exam_preview.html`

#### 任务说明（摘自考试预览）

随着人们健康意识的增强，越来越多的人开始关注日常运动和健康管理。使用提供的训练数据，补全2.2.3.ipynb代码。选择合适的特征，开发一个预测模型，基于个体性别，个体对运动的看法和个人健康评价来预测个体年龄。利用测试工具对模型进行测试，并对测试结果进行分析，完成测试报告，并运用工具对错误原因进行纠正。
详细说明如下：
（1）正确加载数据集，并显示前五行的数据
（2）使用随机森林模型进行模型训练，要求设定自变量和因变量，并根据自变量特征进行模型训练，最终将训练好的模型以文件名2.2.3_model.pkl保存到考生文件夹，结果文件以2.2.3_results.txt保存到考生文件夹。
（3）使用测试工具对模型进行测试，并记录测试结果，命名2.2.3_report.txt，保存到考生文件夹
（4）对测试结果进行详细分析，并编写测试报告，包括模型性能评估、错误分析及改进建议，将答案写到答题卷文件中，答题卷文件命名为“2.2.3.docx”，保存到考生文件夹。
（5）运用工具分析算法中错误案例产生的原因并进行纠正，重新得到模型训练结果，以文件名2.2.3_results_xgb.txt保存到考生文件夹。
（6）将以上代码以及运行结果，以html格式保存并命名为2.2.3.html，保存到考生文件夹，考生文件夹命名为“准考证号+身份证后6位”。

注意事项：
考生文件夹可以保存在桌面。
jupyter notebook 工作目录（根目录）：虚拟机环境中的D:\jupyter_notebook。
jupyter notebook 打开方式：在终端中输入jupyter notebook启动。
ipynb填充代码运行后，保存为html格式上传。保存方法：jupyter notebook中File->Download as->HTML(.html)。
ipynb代码在下划线上填充，请勿随意添加、删除或修改源代码的其他部分，以免影响考试结果。

答案上传要求：
1. 上传2.2.3.html
2. 上传2.2.3.docx

#### 代码文件（完整代码）

```python
import pandas as pd
from sklearn.model_selection import train_test_split
from sklearn.ensemble import RandomForestRegressor
import pickle
from sklearn.metrics import mean_squared_error, r2_score
import xgboost as xgb

# 加载数据集
df = __________

# 显示前五行数据
print(__________)

# 去除所有字符串字段的前后空格
df = df.applymap(lambda x: x.strip() if isinstance(x, str) else x)

# 检查和清理列名
df.columns = df.columns.str.strip()

# 选择相关特征进行建模
X = df[['Your gender', 'How important is exercise to you ?', 'How healthy do you consider yourself?']]
X = __________(X)  # 将分类变量转为数值变量

# 将年龄段转为数值变量
y = __________(lambda x: int(x.split(' ')[0]))  # 假设年龄段为整数

# 将数据集划分为训练集和测试集（测试集占比20%）
X_train, X_test, y_train, y_test = __________(__________, random_state=42)

# 创建随机森林回归模型（创建的决策树的数量为100）
rf_model = __________(__________, random_state=42)
# 训练随机森林回归模型
__________

# 保存训练好的模型
with open('2.2.3_model.pkl', 'wb') as model_file:
    pickle.__________

# 进行结果预测
y_pred = __________
results_df = pd.DataFrame(y_pred, columns=['预测结果'])
results_df.to_csv('2.2.3_results.txt', index=False)

# 使用测试工具对模型进行测试，并记录测试结果
train_score = __________   #训练集分数
test_score = __________    #测试集分数
mse = __________  #均方误差
r2 = __________  #决定系数
with open('2.2.3_report.txt', 'w') as report_file:
    report_file.write(f'训练集得分: {train_score}\n')
    report_file.write(f'测试集得分: {test_score}\n')
    report_file.write(f'均方误差(MSE): {mse}\n')
    report_file.write(f'决定系数(R^2): {r2}\n')

# 运用工具分析算法中错误案例产生的原因并进行纠正
# 初始化XGBoost回归模型（构建100棵树）
xgb_model = __________(__________, random_state=42)
# 训练XGBoost回归模型
__________
# 使用XGBoost回归模型在测试集上进行结果预测
y_pred_xgb = __________

results_df_xgb = pd.DataFrame(y_pred_xgb, columns=['预测结果'])
results_df_xgb.to_csv('2.2.3_results_xgb.txt', index=False)

with open('2.2.3_report_xgb.txt', 'w') as xgb_report_file:
    xgb_report_file.write(f'XGBoost训练集得分: {__________}\n')
    xgb_report_file.write(f'XGBoost测试集得分: {__________}\n')
    xgb_report_file.write(f'XGBoost均方误差(MSE): {__________}\n')
    xgb_report_file.write(f'XGBoost决定系数(R^2): {__________)}\n')
```

---

### 四、智能系统设计-智能系统监控与优化（15分）  
**题号：3.1.3 智能健康手环的数据分析与优化**

素材路径：`practices/3.1.3_智能健康手环的数据分析与优化/exam_preview.html`

#### 任务说明（摘自考试预览）

智能健康手环作为个人健康管理的重要工具，已经广泛应用于日常生活中。它们能够追踪用户的运动量、心率、睡眠质量等健康指标，通过与智能手机的应用程序同步，帮助用户监测和改善生活习惯。随着生物传感技术和机器学习算法的发展，智能手环的数据分析能力不断提升，但在市场竞争中，制造商需要通过精细化的数据分析来优化产品，提升用户满意度。数据分析在此过程中至关重要。通过分析用户的行为数据，企业可以了解用户对不同健康监测功能的偏好，发现使用模式和可能的改进点。例如，分析用户在什么时间段最活跃、哪些健康指标最常被关注、以及数据同步的效率问题，有助于制定精准的产品改进策略。
（1）你作为人工智能训练师，根据给定的数据集（智能健康手环数据集.xlsx），从以下三方面：
用户活动模式：分析用户在一周内不同时间段的活动水平，识别高峰时段和低谷时段。
健康指标关注度：识别哪些健康指标（如步数、心率、睡眠时长）最受用户关注，哪些较少被查看。
数据同步性能：评估手环与手机应用之间数据传输的平均延迟，找出影响同步传输速度的因素。
给出一份在用户活动模式、健康指标关注度和数据同步性能方面的分析报告，将其保存为docx文件，命名为3.1.3-1.docx。
（2）为了增强产品功能和用户体验，给出智能健康手环产品的3个优化方向和对应解决方案，将其保存为docx文件，命名为3.1.3-2.docx。
所有结果文件储存在桌面新建的考生文件夹中，文件夹命名为“准考证号+身份证号后六位”。

注意事项：
当前题目请在答题素材文件3.1.3.docx中完成上传。

答案上传要求：
1. 上传3.1.3.docx

#### 答题模板（完整文本）

请勿修改答题卷，在指定单元格内填写答案
分析报告
用户活动模式
用户平均步数
06:00 - 08:00
17:00 - 20:00
其余时段（步数为0时段不计入）
健康指标关注度
最受关注的指标
较少关注的指标
数据同步性能
平均延迟时间（秒）
影响因素
优化方向及解决方案
优化方向1：
对应解决方案1：
优化方向2：
对应解决方案2：
优化方向3：
对应解决方案3：

---

### 五、智能系统设计-人机交互流程设计（20分）  
**题号：3.2.3 面部表情识别系统交互流程设计**

素材路径：`practices/3.2.3_面部表情识别系统交互流程设计/exam_preview.html`

#### 任务说明（摘自考试预览）

面部表情识别系统是一种先进的计算机视觉技术，它能够分析人脸的微表情，识别出诸如快乐、悲伤、惊讶等基本情绪。通过捕捉和解读面部特征，如眼睛、眉毛和嘴部的动作，这类系统能在实时或预录的视频中判断人的情感状态，广泛应用于人机交互、市场调研、医疗健康监测、安全监控及教育科技等多个领域，为提升用户体验、增进情感智能和优化社会服务提供了有力工具。
AI模型说明：提供的已训练的模型“emotion-ferplus.onnx”，其专门用于进行面部表情识别。定义情感类别与数字标签的映射表为{'neutral':0, 'happiness':1, 'surprise':2, 'sadness':3, 'anger':4, 'disgust':5, 'fear':6, 'contempt':7}。
该模型的使用交互流程为：
1)加载模型“emotion-ferplus.onnx”和加载情感类别与数字标签的映射表；
2)加载一张本地图片“img_test.png”，并预处理图像；
3)使用已训练的模型对图片面部表情识别；
4)输出识别后的表情标签。
你作为一名人工智能训练师，请完成以下工作任务：
（1）补全该模型的使用交互流程对应的Python代码（3.2.3.ipynb），实现本地测试图片“img_test.png”的识别，将其识别结果截图保存为jpg格式文件，命名为3.2.3-1.jpg。
（2）在上面的使用交互流程基础上，给出在面部表情识别系统中使用“emotion-ferplus.onnx”模型的一种人机交互的最优方式，将其保存为docx文件，命名为3.2.3.docx。
所有结果文件储存在桌面新建的考生文件夹中，文件夹命名为“准考证号+身份证号后六位”。

注意事项：
考生文件夹可以保存在桌面。
jupyter notebook 工作目录（根目录）：虚拟机环境中的D:\jupyter_notebook。
jupyter notebook 打开方式：在终端中输入jupyter notebook启动。
ipynb填充代码运行后，附带结果保存为html格式上传。保存方法：jupyter notebook中File->Download as->HTML(.html)。
ipynb代码在下划线上填充，请勿随意添加、删除或修改源代码的其他部分，以免影响考试结果。
截图工具：Windows附件->截图工具。截图只截取输出结果部分，其余多余内容不截取。
emotion-ferplus.onnx存储位置D:\jupyter_notebook\onnx。

答案上传要求：
1. 上传3.2.3.html
2. 上传3.2.3.docx
3. 上传3.2.3-1.jpg

#### 代码文件（完整代码）

```python
# 导入必要的库
import numpy as np
from PIL import Image
import onnxruntime as ort


# 定义预处理函数，用于将图片转换为模型所需的输入格式
def preprocess(image_path):
    input_shape = (1, 1, 64, 64)    # 模型输入期望的形状，这里是 (N, C, H, W)，N=batch size, C=channels, H=height, W=width
    img = Image.open(image_path).convert('L')    # 打开图像文件并将其转换为灰度图  1分
    img = img.resize((64, 64), Image.ANTIALIAS)    # 调整图像大小到模型输入所需的尺寸
    img_data = np.array(img, dtype=np.float32)    # 将PIL图像对象转换为numpy数组，并确保数据类型是float32
    # 调整数组的形状以匹配模型输入的形状
    img_data = np.expand_dims(img_data, axis=0)  # 添加 batch 维度
    img_data = np.expand_dims(img_data, axis=1)  # 添加 channel 维度
    assert img_data.shape == input_shape, f"Expected shape {input_shape}, but got {img_data.shape}"    # 确保最终的形状与模型输入要求的形状一致
    return img_data    # 返回预处理后的图像数据


# 定义情感类别与数字标签的映射表 3分
emotion_table = {____________}


# 加载模型 3分
ort_session = ____________    # 使用onnxruntime创建一个会话，用于加载并运行模型


# 加载本地图片并进行预处理 3分
input_data = ____________


# 准备输入数据，确保其符合模型输入的要求
ort_inputs = {ort_session.get_inputs()[0].name: input_data}    # ort_session.get_inputs()[0].name 是获取模型的第一个输入的名字


# 运行模型，进行预测 3分
ort_outs = ____________(None, ____________)


# 解码模型输出，找到预测概率最高的情感类别 3分
predicted_label = ____________(ort_outs[0])


# 根据预测的标签找到对应的情感名称 3分
predicted_emotion = ____________[predicted_label]


# 输出预测的情感
print(f"Predicted emotion: {predicted_emotion}")
```

---

### 六、培训与指导（5分）  
**题号：4.1.3 数据清洗培训大纲编写**

素材路径：`practices/4.1.3_数据清洗培训大纲编写/exam_preview.html`

#### 任务说明（摘自考试预览）

A企业是一家康复训练机构，需要利用人工智能技术为康复患者提供个性化的康复训练计划，并实时监控训练效果。为了提高人工智能技术的应用效果，其采集了大量的康复数据，现计划对新进技术人员进行数据清洗工具的使用培训。通过这次培训，将会使新进技术人员掌握4中基于Python的数据清洗工具的使用，能对大量的康复数据进行清洗，达到人工智能训练师四级/中级工的技能水平。
请你根据要求补全素材4.1.3.docx中的培训大纲。

答案上传要求：
1. 上传4.1.3.docx

#### 答题模板（完整文本）

在下划线上填写答案。
根据学习大纲补充学习目标
引言
学习目标：
内容：
介绍人工智能在康复训练中的应用，数据清洗在处理康复数据中的作用。
数据清洗基础理论
学习目标：
内容：
什么是数据清洗？
数据清洗的常见任务：数据去重、缺失值处理、数据格式转换等。
数据清洗在数据分析和模型训练中的重要性。
常用数据清洗工具简介
学习目标：
内容：
Pandas：强大的数据处理与分析工具。
NumPy：高性能科学计算和数据处理库。
OpenRefine：用于数据清洗的开源工具。
Dask：用于处理大规模数据的并行计算库。
环境搭建与工具安装
学习目标：
内容：
安装Python和pip包管理工具。
安装并配置Pandas、NumPy、OpenRefine、Dask。
Pandas实战
学习目标：
内容：
数据导入与导出：读取和保存CSV、Excel等格式的数据。
数据筛选与过滤：条件筛选、去重、缺失值处理。
数据转换：数据类型转换、时间序列处理。
实践操作：使用Pandas清洗一个康复数据集。
NumPy实战
学习目标：综合运用所学知识进行数据清洗项目。
内容：
项目介绍：清洗一个多来源、多格式的康复数据集。
数据采集：导入多种格式的数据。
数据清洗：使用Pandas、NumPy、OpenRefine、Dask进行清洗。
项目评审：展示清洗成果，讲解实现思路和遇到的问题。
