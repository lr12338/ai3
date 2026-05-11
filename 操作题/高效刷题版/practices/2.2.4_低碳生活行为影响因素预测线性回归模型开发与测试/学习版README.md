# 2.2.4 低碳生活行为影响因素预测线性回归模型开发与测试 学习版

## 题目要点

- 题型定位：模型开发、测试报告与错误纠正
- 这组题的核心是“建模 + 评估 + 分析 + 优化”。
- 基础模型常见为 Logistic 回归、随机森林、线性回归等。
- 高分点通常在测试报告和错误分析，而不只是模型跑通。

## 解题步骤

1. 读取数据并设定特征和目标变量。
2. 划分训练集和测试集。
3. 训练模型并输出预测结果。
4. 生成测试报告，分析性能表现。
5. 针对错误案例或类别不平衡做优化，再次训练并保存结果。

## 高频代码模板

```python
from sklearn.model_selection import train_test_split

X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=42)
model.fit(X_train, y_train)
y_pred = model.predict(X_test)
```

## 易错点

- 只给准确率，不分析 precision/recall/f1-score。
- 没有解释错误案例产生的原因。
- 改进方案只写一句“继续优化”，没有具体方法。

## 5分钟速记版

- 固定报告结构：模型性能 -> 错误分析 -> 改进建议。
- 遇到分类不平衡，优先想到 `SMOTE` 或重采样。

## 建议练习顺序

- 先看 `exam_preview.html` 理解题面。
- 再做 `example.ipynb` 或 `answer_template.docx`。
- 最后对照题目要求检查文件保存格式与命名。