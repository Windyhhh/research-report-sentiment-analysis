<div align="center">

# 研报情感分析 | research-report-sentiment-analysis

### NLP sentiment analysis on financial research reports.

Project scaffolding for analyzing sentiment in financial research reports.

[![License](https://img.shields.io/badge/license-MIT-blue.svg)](LICENSE)

</div>

---

**research-report-sentiment-analysis** is the project for **NLP sentiment analysis on financial research reports** — turning qualitative analyst reports into quantitative sentiment signals.

> [!NOTE]
> 中文项目：研报情感分析——对金融研究报告做 NLP 情感分析，将定性研报转化为定量情绪信号。

---

## Status

This repository currently holds the **project documentation / scaffolding** — the analysis pipeline is planned as follows:

- Text loading & cleaning of research reports.
- Chinese tokenization and sentiment scoring.
- Key-topic extraction (TF-IDF / TextRank).
- Output as structured sentiment signals.

The README will be updated with runnable code as modules land.

---


## 技术实现细节

### 架构概览

研报情感分析系统采用 **数据采集 → 文本预处理 → 情感分析 → 结果可视化** 的四阶段流水线架构，针对金融研报文本的专业性和长文本特性进行优化。

### 核心模块

- **数据采集模块**：支持 PDF/HTML 格式研报解析，提取标题、摘要、正文、评级等结构化字段
- **文本预处理模块**：金融领域分词、停用词过滤、术语归一化（如"增持/买入/强烈推荐"统一映射）
- **情感分析模块**：融合词典法与机器学习模型，对研报整体情感和段落级情感进行双重判定
- **结果输出模块**：生成情感评分、关键词云、评级分布统计，支持导出 CSV/JSON

### 技术栈与依赖

**核心框架/库**：Python, NLTK, jieba, scikit-learn, pandas, NumPy

**主要技术选型**：
- 分词：jieba（金融领域自定义词典）
- 特征工程：TF-IDF + 情感词典特征融合
- 分类模型：SVM / 逻辑回归 / 朴素贝叶斯对比实验
- 长文本处理：分段情感打分 + 加权聚合

### 实现要点

- 针对研报长文本特性，采用**分段情感打分 + 位置加权聚合**策略，避免全文平均导致的情感稀释
- 构建**金融领域情感词典**（含看多/看空/中性三类，覆盖 2000+ 金融术语），提升领域适配性
- 支持**评级一致性校验**：将模型情感输出与研报原始投资评级对比，识别评级偏差
- 输出**可解释性结果**：标注驱动情感判定的关键句子，便于人工复核

---
## License

MIT — free to use, modify and distribute.
