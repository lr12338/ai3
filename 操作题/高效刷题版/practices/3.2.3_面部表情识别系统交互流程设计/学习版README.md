# 3.2.3 面部表情识别系统交互流程设计 学习版

## 题目要点

- 题型定位：模型推理与人机交互流程设计
- 这组题本质是把已有模型跑起来，再补一份交互设计说明。
- 流程通常固定：加载模型、加载标签、读取输入、预处理、推理、输出结果。
- 文字题重点写清楚用户怎么和系统交互，系统如何反馈结果。

## 解题步骤

1. 确认模型文件、标签文件和测试图片路径。
2. 完成预处理并保证输入张量格式正确。
3. 运行推理，输出预测类别或 TopN 概率。
4. 写一版简洁的人机交互最优方案。

## 高频代码模板

```python
import onnxruntime as ort

session = ort.InferenceSession("data/model.onnx")
input_name = session.get_inputs()[0].name
output_name = session.get_outputs()[0].name
result = session.run([output_name], {input_name: processed})[0]
```

## 易错点

- 预处理尺寸、通道顺序或数据类型不对。
- 忘记 softmax 或 TopN 输出。
- 交互方案只写“上传图片”，没有结果展示和反馈机制。

## 5分钟速记版

- 五步固定流程：模型、标签、输入、预处理、推理输出。

## 建议练习顺序

- 先看 `exam_preview.html` 理解题面。
- 再做 `example.ipynb` 或 `answer_template.docx`。
- 最后对照题目要求检查文件保存格式与命名。