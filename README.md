# 基于随机森林的恶意 URL 识别系统

## 项目简介

本项目旨在构建一个基于机器学习的恶意网址识别系统，通过分析 URL 的文本特征与结构化特征，有效识别钓鱼网站、携带恶意代码的网站等安全威胁目标。项目中采用了多种模型进行实验与对比，最终选定 XGBoost 模型作为主力分类器，并对神经网络与 Transformer 等深度学习方法进行了探索。

该项目适合作为网络空间安全方向的课程设计、科研项目或简历展示，具备完整性、复现性和一定的工程价值。

## 数据来源

- OpenPhish（恶意网址）
- URLHaus（恶意网址）
- Tranco Top Sites（可信网址）
- Kaggle 公开数据集（补充样本）

经过清洗与处理后，数据集中包含：
- 训练集：共 24万 条，平衡的正负样本
- 测试集：共 10万 条，正负样本各 5万 条

## 特征提取

- **文本特征**：使用 TF-IDF 向量化 URL 字符串
- **结构化特征**：
  - URL 长度
  - “.” 数量
  - “-” 数量
  - 可疑关键词（如 login、verify、update 等）计数
- 所有特征统一归一化后拼接用于训练

## 模型对比

| 模型             | 准确率 | 特点说明                     |
|------------------|--------|------------------------------|
| 朴素贝叶斯       | 0.79   | 快速，适用于稀疏文本数据     |
| 逻辑回归         | 0.84   | 稳定，解释性较强             |
| 神经网络         | 0.85   | 简单两层结构，表现较好       |
| **XGBoost**      | **0.87** | 效果最佳，综合性能最优     |
| Transformer 模型 | <0.45  | 实验性质，Recall 较高但不稳定（未展示） |

## 项目结构

malicious-url-detector/ <br>
├── 111_fixed.csv # 训练数据<br>
├── balanced_test_set.csv # 测试数据<br>
├── test8(随机森林).ipynb # 随机森林模型代码<br>
├── test9(贝叶斯).ipynb # 朴素贝叶斯模型代码<br>
├── test10(逻辑回归).ipynb # 逻辑回归模型代码<br>
├── test11(神经网络).ipynb # 神经网络模型代码<br>
├── test12(XGBoost).ipynb # XGBoost 模型代码<br>
├── test13(transformer).ipynb # Transformer 模型探索<br>
├── requirements.txt # 环境依赖说明<br>
├── 项目说明.docx # 报告文档<br>


## 使用说明

1、 克隆仓库并安装依赖：

   ```bash
   git clone https://github.com/your-username/malicious-url-detector.git
   cd malicious-url-detector
   pip install -r requirements.txt
2、打开对应模型的 .ipynb 文件运行即可。

3、所有模型均可直接使用 CSV 文件训练，无需额外准备。

开源许可
本项目采用 MIT License 开源，具体内容请参考仓库中的 LICENSE 文件。

致谢
感谢 OpenPhish、URLHaus、Tranco 及 Kaggle 平台提供数据支持。
