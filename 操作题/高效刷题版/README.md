# 高效刷题版索引
考试题型分布如下，共六道题，每个题有五个例题，如1.1.1至1.1.5 
每个例题目录下 exam_preview.html 为题目示例，example.ipynb含有待填空的代码题，answer_template.docx是待填的文本题
基于以下题型分布，综合（exam_preview.html 为题目示例，example.ipynb含有待填空的代码题，answer_template.docx是待填的文本题），为我设计5套模拟试卷用于练习，md格式即可，制定计划并执行
## 1.1, 1.2 业务分析 抽一 25分

## 1.1 业务流程设计 1.1 代码题

## 1.2 业务模块效果优化 1.2 文本题…

## 2.1 智能训练 - 数据处理规范制定 操作 必考 15分…

## 2.2 智能训练 - 算法测试 操作 必考 20分…

## 3.1 智能系统设计 - 智能系统监控与优化 文本 必考 15分…

## 3.2 智能系统设计 - 人机交互流程设计 必考 20分 …

## 4.1, 4.2 培训与指导 抽一 5分…

## 考试

## 1.1，1.2 业务分析 抽一 25分

## 1.1 业务流程设计 1.1 代码题

### 1.1.1 智能医疗系统数据处理

data = pd.read_csv(r'')

data['RiskLevel'] = np.where(data['DaysInHospital']>7, '高风险患者', '低风险患者')

- 根据BMI值划分指定区间 4分
data['BMIRange'] = pd.cut(data['BMI'], bins=bmi_bins, labels=bmi_labels, right=False)  # 
- 计算每个BMI区间中高风险患者的比例 2分
bmi_risk_rate = data.groupby('BMIRange')['RiskLevel'].apply(lambda x: (x == '高风险患者').mean())
bmi_patient_count = data['BMIRange'].value.counts()
data['AgeRange'] = pd.cut(data['Age'], bins=age_bins, labels=age_labels, right=False)
- 计算每个年龄区间中高风险患者的比例 2分
age_risk_rate = data.groupby('AgeRange')['RiskLevel'].apply(lambda x: (x == '高风险患者').mean())
age_patient_count = data[''AgeRange''].value_counts

### 1.1.2

- 对传感器类型分组，统计数量和平均值 数据.groupby('分组列')['被统计列'].agg(['统计1','统计2'])
sensor_stats = data.groupby('SensorType')['Value'].agg(['count', 'mean'])
.agg['','']
data[data[''].isin(['','',])].group['','']['']
- data[''].fillna(method=ffill, ) bfill
data[''].fillna(method='ffill',) bfill

### 1.1.3

missing_values = data.isnull().sum()       #数据缺失值统计 2分
duplicate_values = data.duplicated().sum()   #数据重复值统计 2分
data['Age'].between(18,70)

### 1.1.4

- 数据标准化 (data - mean())/ std()
data['PurchaseAmount'] = (data['PurchaseAmount'] - data['PurchaseAmount'].mean()) / data['PurchaseAmount'].std()  # PurchaseAmount数据标准化 2分
data['ReviewScore'] = (data['ReviewScore'] - ________________) / ________________        # ReviewScore数据标准化 

# 1.1.5
- 统计不同性别的平均车速、行驶距离和行驶时间  数据.group(分组列).agg(要计算的列 : 用什么函数计算)
gender_stats = data.group('Gender').agg['Speed':'mean',]

## 1.2 业务模块效果优化 1.2 文本题

### 1.2.1 顾客情感模块优化
两个问题：
情感识别准确性不高：
用户的第一需求是获得准确的情感识别结果，但结果准确性不高导致分析有误差，不能给用户提供正确的决策参考，甚至会有误导风险，影响用户体验
响应速度慢：
情感识别慢，响应时间长，导致用户等待时间久，增加用户时间成本，降低用户使用意愿
优化方案：
关键步骤：
模型与算法优化：深度分析情感识别的流程，针对算法流程和模型进行优化，补充样本数据集和特征改进等，提高情感识别的准确性；
算法服务优化：优化算法架构，简化相关流程，优化缓存等机制，提高并发处理和响应速度
优化用户界面：简化用户界面，使界面 简介、直观，让客户上手简单
增加定制化服务模块：增加定制化服务模块，满足用户个性化需求，提高用户体验

期望效果：通过上述方案，能够有效提高情感识别结果的准确性和服务响应速度，优化用户界面和个性化功能，有效提升体验和服务质量

### 1.2.2 老年人模块优化：
问题
1、心率检测数据受环境影响大，导致准确性不高，且异常预警响应慢，不能及时处理
准确性不高，是由于数据采集集和传输过程中受环境影响较大，导致准确性下降
异常预警响应慢：数据传输慢，且没有有效的医护处理机制，导致医护人员不能及时处理
优化方案包括采用更精确的数据采集和预处理技术，并提高模型性能，引入高效的数据处理机制等
优化数据采集过程：升级硬件模块，提高数据采集的准确性，搜集更多样本数据来训练模型，提高模型性能
数据处理机制：建立高效的医护响应机制，能够异常预警快速通知到医护人员并快速响应，优化数据传输模块，积极协调团队资源，要与技术团队紧密合作，高效协调资源，确保方案实现
预期效果：能够有效提高心率检测数据的准确性，并提高异常预警响应速度和水平

### 1.2.3 金融服务模块优化
问题
数据准确性不高
；用户使用该平台的第一需求是获得准确的数据分析结果，当前平台结果准确性不高，导致不能给用户正确的决策支持，甚至会误报用户，降低用户的使用意愿
异常预警响应慢
异常预警响应需要有实时性，若太过缓慢则会给用户带来负面影响，甚至会带来损失
服务个性化不足：无法按照用户个性化需求提供服务
优化方案：
数据准确性提升：深度分析金融数据的预测算法，优化样本数据，与预测模型进行加强训练，提高性能，提高数据分析的准确性：
异常预警响应速度提升：深刻分析异常预警响应流程，优化流程架构，降低复杂度，提高预警速度
服务优化：优化服务的缓存等机制，优化并发处理和实时传输性能
个性化优化：基于用户需求提供更多个性化服务，

效果能够

### 1.2.4 智能卖点生成
问题
卖点生成不准确：用户使用该系统的第一需求是获得准确卖点，而当前系统生成卖点准确性较低，导致不能给用户提供正确的决策支持，甚至会误报用户决策，给用户带来损失，严重影响用户体验
卖点生成速度较慢：卖点生成速度较慢，不能及时给用户反馈，会给用户造成损失
界面不友好：界面较复杂，操作不便，学习成本高
缺乏个性化定制服务：目前系统功能较单一，用户可能有其他需求，无法满足，影响用户的使用意愿
优化：
模型优化：丰富数据样本，对模型进行微调训练，提高模型性能，提高生成卖点的准确性；
算法流程优化：详细分析卖点生成的算法流程，降低算法度，优化处理流程，提高算法处理的速度
服务优化：优化服务的缓存等机制，提高服务并发处理和实时数据处理能力
界面：优化界面，提高模型简洁、美观性能，方便用户使用
个性化服务

### 1.2.5 数智人模块优化
问题： 
数智人回复内容不准确：用户使用该系统的第一需求是获得准确的回复，然后目前回复内容准确度较低，导致不能给用户提供正确的决策支持，甚至会误报用户决策，给用户带来损失，严重影响用户体验
缺乏个性化交互能力：平台功能单一，无法满足用户个性化需求，影响用户使用意愿
响应速度较慢：增加用户等待时间成本
优化：
优化模型性能：丰富样本数据，选用更高性能的模型，采用模型微调等，强化模型性能，提高生成内容的准确性
优化服务：优化服务的缓存等机制，强化服务并发处理和实时信息处理能力，提高响应速度
个性化服务：基于用户实际使用场景，开发个性化服务功能，提升用户体验

## 2.1 智能训练 - 数据处理规范制定 操作 必考 15分

### 2.1.1 智慧交通中燃油效率模型的数据清洗和标注流程设计
data = data.read_csv('')
print(data.head())
print(data.isnull().sum())
data = data.dropna()
- 某列转换成数值类型并删除异常值
data[''] = pd.to_numeric(data[''], )
data = data.dropna(subset=['horsepower'])
data[numerical_features] = scaler.fit_transform(numerical_features)
selected_features = ['cylinders','displacement'、'horsepower'、'weight'、'acceleration'、'model year'、'origin']
X = data[selected_features]
y = data['mpg']
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_rate=42)

index = False
数据清洗和标注规范
数据加载和检查
缺失值处理：
异常值处理：
数据复核：
数据标注规范：
数据来源：
数据描述
特征选择：
数据划分
数据保存：按规范保存数据

### 2.1.2 低碳生活行为影响因素数据清洗和标注流程设计

data = data.read_excel()
initial_row_count = data.shape[0]   #处理前的数据行数
data = data.dropna()                #删除缺失值所在行
final_row_count = len(data)  #处理后的数据行数
- 删除重复行
data = data.drop_duplicates()
scaler = StandardScaler()
data[numerical_features] = scaler.fit_transform(data[numerical_features])
selected_features = [__________] 从数据集中复制
X = data[selected_features]
y = data['低碳行为积极性']
- 合并处理后得数据，并将其保存（保存中不用额外创建索引 pd.concat([],)合并
cleaned_data = pd.concat([X,y], axis=1)
cleaned_data.to_csv('2.1.2_cleaned_data.csv', index = False)

数据清洗和标注规范
数据加载和检查
缺失值处理：
异常值处理：
数据复核：
数据标注规范：
数据来源：
数据描述
特征选择：
数据划分
数据保存：按规范保存数据

### 2.1.3 信用评分模型数据清洗和标注流程设计
- 使用IQR处理异常值 data.quantile() 0.75 0.25  IQR = Q3 - Q1
Q1 = data[numeric_cols].quantile(0.25)   # 下四分位数（25%分位）
Q3 = data[numeric_cols].quantile(0.75)   # 上四分位数（75%分位）
IQR = Q3 - Q1              # 四分位距
- 移除异常值
data_cleaned = data[~((data[numeric_cols] < (Q1 - 1.5 * IQR)) | (data[numeric_cols] > (Q3 + 1.5 * IQR))).any(axis=1)]
duplicates = data_cleaned.duplicated()
scaler = MinMaxScaler()
data_cleaned[numeric_cols] =scaler.fit_transform(data_cleaned[numeric_cols])
target_variable = 'SeriousDlqin2yrs'
X = data.drop(columns=[target_variable])   #1分
y = data[target_variable]   

### 2.1.4 医疗研究数据清洗和标注设计

data = pd.read_csv('path', encoding = 'gbk')
print(data,info())
- 修改列名 data.rename([a:b],)
data.rename(['病人ID':'患者ID'],inplace=True)
data['诊断延迟'] = (data['诊断日期'] - data['就诊日期']).dt.days

data = data.drop_duplicates()

- 绘制柱状图
treatment_outcome_distribution.plot(kind='bar',stacked=True)
- 绘制散点图
plt.scatter(data[''],data[''])
### 2.1.5 健康与营养咨询数据预处理与数据规范设计

data.isnull().sum()
data.dropna()
- 转换 'Your age' 列的数据类型为整数类型，并处理异常值
data_cleaned.loc[:, 'Your age'] = pd.to_numeric(data_cleaned['Your age'], errors='coerce')
data_cleaned.loc[:, 'Your age'] = data_cleaned['Your age'].astype(int)
exercise_frequency_counts = data_cleaned['How often do you exercise?'].value_counts()
- 绘制饼图
plt.figure(figsize=(10, 6))
exercise_frequency_counts.plot.pie(autopct='%1.1f%%', startangle=90, colors=plt.cm.Paired.colors)

## 2.2 智能训练 - 算法测试 操作 必考 20分

### 2.2.1 智能信用评分Logistic回归模型开发与测试

data = pd.read_csv(path)
X_train, X_test, y_train, y_test =  train_test_split(X, y, test_size=0.2, random_state=42)
- 训练Logistic回归模型，最大迭代1000次 max_iter
model = LogisticRegression(max_iter=1000)
mdoel.fit(X_train, y_train)
with ...
    pickle.dump(model, file)
y_pred = model.predict(X_test)
- 分析测试结果
accuracy = (y_test==y_pred).mean()  
- 处理数据不平衡
smote = SMOTE()
X_resampled, y_resampled = smote.fit_resample(X_train, y_train)
model.fit(X_resampled, y_resampled)
y_pred_resample = model.predict(X_test)
accuracy_resampled = (y_test==y_pred_resample).mean()

测试报告：模型性能评估、错误分析及改进建议
              precision    recall  f1-score   support

           0       0.95      0.99      0.97     26779
           1       0.58      0.14      0.22      1737
错误分析
0没有严重逾期：：准确率和召回率都很高，模型针对该类别的性能比较好，仅有少量漏报和误报情况
1 有严重逾期：准确率较低，召回率极低，模型针对该类别判断性能很差，且大量有严重逾期的类别没有被正确识别
改进建议
数据处理策略调整：采用重采样，由于数据集比例不均，因此需要对数据进行处理，平衡两种样本的比例
特征功能：可能是当前特征没有完全描述样本的复杂关系，需要重新分析数据，选用更具代表性的特征，并去除冗杂特征

### 2.2.2 智慧交通中燃油效率随机森林模型开发与测试

df = pd.read_csv(path)
- 将某列转化为数值 pd.to_numeric() pd.get_dummies()多维数据
df['horsepower'] = pd.to_numeric(df['horsepower', errors='coerce'])
X = df[['','','']]
y = df['mpg']
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size = 0.2, random_state=42)
- 创建包含标准化和线性回归的管道
pipeline = Pipeline({('scaler',StandardScaler),('linreg',LinearRegression)})
pipeline.fit(X,y)
with 
    pickle.dump(pipeline, model_file)
y_pred = pipeline.predict(X_test)
results_df.to_csv()
rf_model = RandomForestRegressor(n_estimators =100,random_state=42)
rf_model.fit(X_train, y_train)
y_pred_rf = rf_model.predict(X_test)
results_rf_df.to_csv()

测试报告：
错误分析：
过拟合：训练集效果由于测试集，说明存在轻微的过拟合现象，模型在训练集上性能较好，但是针对测试集中未见过的数据 性能变差
特征工程：当前特征可能没有充分描述样本数据的复杂关系
模型选择：当前选用线性回归模型，认定样本数据存在线性关系，若表现差则可能说明不满足此关系
改进建议：
特征工程：再次分析数据，选用更具代表性的特征，去除冗余特征
模型测试：结合多种模型，如随机森林、神经网络】向量机等模型综合测试，交叉验证，选用最合适的模型

### 2.2.3 日常运动量随机森林预测模型开发与测试

df = pd.read_csv(path)
print(df.head())
X = pd.get_dummies(X)
#将年龄段转为数值变量
y = df['Your age'].apply(lambda x: int(x.split('')[0]))
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=42)
rf_model = RandomForestRegressor(n_estimators=100, random_state=42)
rf_model.fit(X_train, y_train)
with 
    pickle.dump(rf_model, model_file)
y_pred = rf_model(X_test)
- 评分
train_score = rf_model.score(X_train, y_train)
test_score = rf_model.score(X_test, y_test)
mse = mean_squared_error(y_test, y_pred)
r2 = r2_score(y_test, y_pred)
- 初始化XGBBoost回归模型
xgb_model = xgb.XGBRegression(n_estimators=100,random_state=42)
xgb_model.fit(X_train, y_train)
y_pred_xgb = xgb_model.predict(X_test)

xgb_model.score(X_train, y_train)
xgb_model.score(X_test, y_test)
mean_squared_error(y_test, y_pred_xgb)
r2_score(y_test, y_pred_xgb)

测试报告：
错误分析：
特征不足：所选特征无法充分描述变量间的关系，导致模型性能较差
模型选择：当前模型参数需调整，或者  变量关系不适用于本模型
改进建议：
特征工程：需再分析变量间关系，选择更具代表性的特征，除去冗杂特征
模型测试：调整该模型参数，并结合其他模型如 神经网络等模型综合测试，交叉验证，选择最优

### 2.2.4 低碳生活行为影响因素预测线性回归模型开发与测试

data = pd.read_excel(path)
print(data.head())
data_cleaned = data.drop(columns=['',''])
X = data_cleaned.drop(columns=[target])
y = data_cleaned[target]
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_rate=42)
model = LinearRegression()
model.fit(X_train, y_train)
joblib.dump(model, model_filename)
y_pred = model.predict(X_test)
results_filename.to_csv(path,)
mean_squared_error(y_test, y_pred)
r2_score(y_test, y_pred)
xgb_model = XGBRegressor(n_estimators,learing_rate=0.05, max_depth=5, ..)
xgb_model.fit(X_train, y_train)

y_pred_xg = xgb_model.predict(X_test)
mean_squared_error(y_test, y_pred_xg)
r2_score(y_test, y_pred_xg)

测试报告：
错误分析：
### 2.2.5 智能步数预测模型开发与测试
mean_absolute_error(y_test, y_pred)



## 3.1 智能系统设计 - 智能系统监控与优化 文本 必考 15分

模板：
系统性能 网络延迟 硬件限制
优化方向和解决方案 
网络连接和设备交互优化：强化网络连接的稳定性，采用更高效的通信协议，减少网络延迟，降低资源消耗
硬件优化：升级某数据的传感器，提高数据采集的准确性和传输稳定性等性能
系统性能优化：系统分析某某检测系统架构，简化相关流程，提高系统运行效率
个性化支持：基于用户的实际使用场景，提供 某某 个性化服务，数据自定义等，提高服务质量与用户体验

### 3.1.1 智能音箱产品等数据分析与优化 硬件
优化方向和解决方案：
（响应时间较长 控制家居）网络连接和设备交互优化：强化网络连接稳定性，采用更高效的通信协议，减少控制家居的响应时间
提升信息检索效率：优化查询知识的检索算法，加快数据处理速度，提升用户体验
增强本地处理能力：增加本地缓存和预处理机制，特别是播放音乐和查天气功能，减少外部资源依赖
个性化服务
### 3.1.2 智能照明系统
延迟瓶颈 网络延迟、硬件限制
网络连接优化：强化网络连接稳定性，，采用更高效的通信协议，减少控制设备的响应时间
设备优化：对硬件进行升级，提高硬件性能与治疗
个性化服务优化：基于用户使用需求，提供个性化服务，比如定时配置设备参数等

### 3.1.3  智能健康手环
	用户平均步数
06:00 - 08:00	
17:00 - 20:00	
其余时段（步数为0时段不计入）	

健康指标关注度
最受关注的指标	
较少关注的指标		

数据同步性能
平均延迟时间（秒）	
影响因素		网络延迟 设备电量低
优化方向：
网络连接与设备交互优化：强化网络连接的稳定性，采用更高效的通信协议，减少网络延迟
硬件升级：针对硬件的传感器等模块进行升级，优化数据采集的准确性和传输速率和稳定性
个性化服务优化：基于用户实际使用场景，添加个性化服务，比如步数数据总结、心率异常报警等，提升用户体验

### 3.1.4 健康监测系统
健康指标变化趋势
用户血压 早上7点半昨天血压值最高，其他时间血压较稳定
血糖处于正常水平，餐后会升高，后续会降为正常水平
体脂连续一周维持在0.7

早上时间段6-10血压

安全时段
除去早上时段的血压，以及全天的血糖

优化方向：
网络连接优化：强化网络服务的稳定性，选用更高效的通信协议，减小网络延迟
硬件优化：升级健康数据的传感器模块，提高数据采集的准确性和传输稳定性
个性化优化：基于用户实际应用场景，开发个性化服务，比如支持用户自定义血压、血糖数据推送与自动预警通知等，提升用户体验

### 3.1.5 智能家居环境控制系统

节能潜力 智能调度 系统系能优化 
优化方向：
系统性能优化：强化网络连接稳定性，选用更高效的通信协议，降低网络延迟，减少资源消耗
智能调度： 引入数据分析，基于用户使用习惯设计智能调度模块，合理调用资源
个性化需求：支持用户基于个人习惯配置个性化场景的参数，能够定时调用，提升用户体验



## 3.2 智能系统设计 - 人机交互流程设计 必考 20分 

### - [3.2.1 图像识别评估系统交互流程设计]

模型加载 
session = onnxruntime.InferenceSession('path')
图片加载
img = Image.open('image_path'),convert('RGB')
img = preprocess_image(image)
图片推理
outputs = session.run()
- softmax函数
probabilities = scipy.special.softmax()
- 获取该最高5个概率 np.argsort()取索引； pro[0][top5_idx]按索引取值
top5_idx = np.argsort(probabilities[0])[-5:][::-1] 
top5_prob = probabilities[0][top5_idx]

交互流程设计
用户界面设计：设计简洁易懂的用户界面，包含图片资源上传选项与推理结果显示框
图片资源上传与预处理：支持用户自主上传待识别图片，并自动预处理
模型选择与预加载：支持选择模型 resent.onnx,并预加载
推理结果展示：推理结果展示，并支持用户自主下载
帮助与支持：内置帮助文档与客户支持，提升用户体验
反馈：有反馈渠道，改进性能

### - [3.2.2 手写数字识别系统交互流程设计]

模型加载
ort_session = onnxruntime.InferenceSession('model_path')
加载图像
image = Image.open('imagepath').convret('L')
- 图像预处理
image = image.resize((28.28))
image_array = np.array(image, )
image_array = np.expand_dims(image, )
image_array = np.expand_dims(image, )
- 返回模型输入列表
ort_inputs = {ort_session.get_inputs()[0].}
执行预测
ort_outs = ort_session.run()
- 获取预测结果 argmax 返回索引
predicted_class = np.argmax(ort_outs[0])

交互流程设计：
用户界面设计：设计友好易懂的用户界面，含有本地手写数字图片上传选项和结果显示窗口
图片资源上传：支持用户自主上传本地手写数字图片，并自动预处理
模型加载：支持自主选择mnist模型并预加载
结果展示：支持用户自主启动推理并清洗展示结果，支持自主保存
帮助与支持：
反馈：

### - [3.2.3 面部表情识别系统交互流程设计]

定义映射表
emotion_table = {'neutral':0, 'happiness':1, 'surprise':2, 'sadness':3, 'anger':4, 'disgust':5, 'fear':6, 'contempt':7}
加载模型
ort_session = ort.InferenceSession('path')
input = preprocess(imagepath)
ort_outs = ort_session.run(None, imput_data)

- 解码模型输出，找到预测概率最高的情感类别 argmax 返回索引
predicted_label = np.argmax(ort_outs[0])
- 根据预测的标签找到对应的情感名称  .keys取回字典对应的值 ； list() 转化为普通列表
predicated_emotion = list(emotion_table.keys())[predicted_label]

交互流程设计：
用户界面设计：设计友好易懂的用户界面，含有本地图片上传选项和结果显示窗口
图片资源上传：支持用户自主上传本地表情图片，并自动预处理
模型加载：系统启动时自动加载模型和标签
结果展示：支持用户自主启动推理并清洗展示结果，支持自主保存
帮助与支持：
反馈：

### - [3.2.4 花朵智能识别系统交互流程设计]
session = ort.InferenceSession(model_path)
with open('imagepath', 'r')as f:...
image = Image.open(imagepath).convert('RGB')
processed_image = preprocess_image(image)
output = session.run
- 应用softmax获取准确率
accuracy = scipy.special.softmax()
- 获取预测的类别索引 argmax 最大值索引
predicted_idx = np.argmax(accuracy)
- 获取预测的准确值（转换为百分比） 获取置信度最高的概率，转化为百分比
prob_percentage = accuracy[0,predicted_idx]*100
- 获取预测的类别标签
predicted_label = labels[predicted_idx]

交互流程设计：
图片界面设计：用户友好，
图片资源上传：
模型与标签加载：
结果展示：
帮助文档
反馈：


###- [3.2.5 人脸AI智能检测系统交互流程设计]

- 从标签文件读取每一行，并去除首尾的空白字符 name.strip 去除多余字符
class_names = [name.strip for name in open('voc-model-labels.txt').readlines()]
ort_session = ort.InferenceSession('')
input_name = ort_session.get_inputs()[0].name
if ..
    os.makedirs(result_path)
for .
    orig_image = cv2.imread(img_path)
    image = cv2.resize(image,())
- 定义图像归一化的均值数组 
    image_mean = np.array([])
    image = np.expand_dims()
    confidence,boxes = ort_sesson.run()

交互流程设计：
用户界面设计：
图片资源上传：
模型与标签加载：
结果展示：
帮助与支持
反馈

## 4.1，4.2 培训与指导 抽一 5分

### 4.1 培训 填空题

### 4.2 指导 填空题




## 1.1

- [1.1.1 智能医疗系统中的业务数据处理流程设计](./practices/1.1.1_智能医疗系统中的业务数据处理流程设计/README.md)
- [1.1.2 智能农业系统中的业务数据采集和处理流程设计](./practices/1.1.2_智能农业系统中的业务数据采集和处理流程设计/README.md)
- [1.1.3 金融机构信用评估系统中的业务数据审核流程设计](./practices/1.1.3_金融机构信用评估系统中的业务数据审核流程设计/README.md)
- [1.1.4 电商平台用户行为分析系统的数据采集与处理流程设计](./practices/1.1.4_电商平台用户行为分析系统的数据采集与处理流程设计/README.md)
- [1.1.5 智能交通系统的数据采集、处理和审核流程设计](./practices/1.1.5_智能交通系统的数据采集、处理和审核流程设计/README.md)

## 1.2

- [1.2.1 顾客评价情感识别业务模块效果优化](./practices/1.2.1_顾客评价情感识别业务模块效果优化/README.md)
- [1.2.2 老年人健康监测与管理服务业务模块效果优化](./practices/1.2.2_老年人健康监测与管理服务业务模块效果优化/README.md)
- [1.2.3 智慧金融服务业务模块效果优化](./practices/1.2.3_智慧金融服务业务模块效果优化/README.md)
- [1.2.4 智能卖点生成系统业务模块效果优化](./practices/1.2.4_智能卖点生成系统业务模块效果优化/README.md)
- [1.2.5 腾讯云智能数智人系统业务模块效果优化](./practices/1.2.5_腾讯云智能数智人系统业务模块效果优化/README.md)

## 2.1



## 2.2

- [2.2.1 智能信用评分Logistic回归模型开发与测试](./practices/2.2.1_智能信用评分Logistic回归模型开发与测试/README.md)
- [2.2.2 智慧交通中燃油效率随机森林模型开发与测试](./practices/2.2.2_智慧交通中燃油效率随机森林模型开发与测试/README.md)
- [2.2.3 日常运动量随机森林预测模型开发与测试](./practices/2.2.3_日常运动量随机森林预测模型开发与测试/README.md)
- [2.2.4 低碳生活行为影响因素预测线性回归模型开发与测试](./practices/2.2.4_低碳生活行为影响因素预测线性回归模型开发与测试/README.md)
- [2.2.5 智能步数预测模型开发与测试](./practices/2.2.5_智能步数预测模型开发与测试/README.md)

## 3.1

- [3.1.1 智能音箱产品的数据分析与优化](./practices/3.1.1_智能音箱产品的数据分析与优化/README.md)
- [3.1.2 智能照明系统的数据分析与优化](./practices/3.1.2_智能照明系统的数据分析与优化/README.md)
- [3.1.3 智能健康手环的数据分析与优化](./practices/3.1.3_智能健康手环的数据分析与优化/README.md)
- [3.1.4 智能健康监测系统的数据分析与优化](./practices/3.1.4_智能健康监测系统的数据分析与优化/README.md)
- [3.1.5 智能家居环境控制系统的数据分析与优化](./practices/3.1.5_智能家居环境控制系统的数据分析与优化/README.md)

## 3.2

- [3.2.1 图像识别评估系统交互流程设计](./practices/3.2.1_图像识别评估系统交互流程设计/README.md)
- [3.2.2 手写数字识别系统交互流程设计](./practices/3.2.2_手写数字识别系统交互流程设计/README.md)
- [3.2.3 面部表情识别系统交互流程设计](./practices/3.2.3_面部表情识别系统交互流程设计/README.md)
- [3.2.4 花朵智能识别系统交互流程设计](./practices/3.2.4_花朵智能识别系统交互流程设计/README.md)
- [3.2.5 人脸AI智能检测系统交互流程设计](./practices/3.2.5_人脸AI智能检测系统交互流程设计/README.md)

## 4.1

- [4.1.1 Label studio培训大纲编写](./practices/4.1.1_Label studio培训大纲编写/README.md)
- [4.1.2 爬虫培训大纲编写](./practices/4.1.2_爬虫培训大纲编写/README.md)
- [4.1.3 数据清洗培训大纲编写](./practices/4.1.3_数据清洗培训大纲编写/README.md)
- [4.1.4 Pandas数据清洗培训大纲编写](./practices/4.1.4_Pandas数据清洗培训大纲编写/README.md)
- [4.1.5 Python数据可视化培训大纲编写](./practices/4.1.5_Python数据可视化培训大纲编写/README.md)

## 4.2

- [4.2.1 智能零售分析系统数据采集和处理指导](./practices/4.2.1_智能零售分析系统数据采集和处理指导/README.md)
- [4.2.2 AI辅助的医疗影像诊断系统数据采集和处理指导](./practices/4.2.2_AI辅助的医疗影像诊断系统数据采集和处理指导/README.md)
- [4.2.3 AI智能安防监控系统采集和处理指导](./practices/4.2.3_AI智能安防监控系统采集和处理指导/README.md)
- [4.2.4 自动驾驶汽车感知系统数据采集与标注指导](./practices/4.2.4_自动驾驶汽车感知系统数据采集与标注指导/README.md)
- [4.2.5 智能化数据标注在文化遗产数字化保护中的应用指导](./practices/4.2.5_智能化数据标注在文化遗产数字化保护中的应用指导/README.md)
