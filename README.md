# 📈 研报情感分析系统 | Research Report Sentiment Analysis

> **面向金融研报的智能情感分析系统——NLP 文本分析、情感倾向识别、关键词提取、市场情绪看板，透视市场投资情绪。**
>
> *Intelligent sentiment analysis system for financial research reports — NLP text analysis, sentiment tendency detection, keyword extraction, market sentiment dashboard, insight into market investment sentiment.*

---

## ⭐ 核心卖点 | Why Star This

| 卖点 | Feature | 一句话 |
|------|---------|--------|
| 📊 **研报分析** | Report Analysis | 专业面向金融研究报告的情感分析 |
| 🧠 **NLP 处理** | NLP Processing | 中文分词、词向量、情感分类 |
| 😊 **情感识别** | Sentiment Detection | 正面/中性/负面自动识别，量化情感分数 |
| 🔑 **关键词提取** | Keyword Extraction | TF-IDF/TextRank 提取核心投资关键词 |
| 📈 **市场情绪看板** | Sentiment Dashboard | 可视化市场投资情绪变化趋势 |

---

## 🏆 技术栈 | Tech Stack

![Python](https://img.shields.io/badge/Python-3.8+-blue?logo=python)
![SnowNLP](https://img.shields.io/badge/SnowNLP-0.12+-green?logo=python)
![Jieba](https://img.shields.io/badge/Jieba-0.42+-red?logo=python)
![Scikit-learn](https://img.shields.io/badge/Scikit--learn-1.0+-orange?logo=scikitlearn)
![Pandas](https://img.shields.io/badge/Pandas-1.3+-blue?logo=pandas)
![ECharts](https://img.shields.io/badge/ECharts-5.0+-orange?logo=apacheecharts)
![Flask](https://img.shields.io/badge/Flask-2.0+-black?logo=flask)

---

## 🚀 快速开始 | Quick Start

```bash
git clone https://github.com/Windyhhh/research-report-sentiment-analysis.git
cd research-report-sentiment-analysis

# 1. 安装依赖
pip install -r requirements.txt

# 2. 下载中文停用词
python scripts/download_stopwords.py

# 3. 分析单篇研报
python analyze.py --file data/sample_report.pdf

# 4. 批量分析研报
python batch_analyze.py --dir data/reports/ --output result.csv

# 5. 启动可视化看板
python app.py --port 5000

# 6. 访问
# 情绪看板: http://localhost:5000
```

---

## 📂 项目结构 | Project Structure

```
research-report-sentiment-analysis/
├── analyze.py                 # 单篇分析入口
├── batch_analyze.py           # 批量分析
├── app.py                     # 可视化看板
├── nlp/                       # NLP 模块
│   ├── tokenizer.py           # 分词
│   ├── sentiment.py           # 情感分析
│   ├── keywords.py            # 关键词提取
│   └── summary.py             # 摘要生成
├── data/                      # 数据
├── result/                    # 分析结果
└── requirements.txt
```

---

## 🔬 核心实现 | Core Implementation

### 情感分析引擎 | Sentiment Analysis

```python
# 基于词典 + 机器学习的情感分析
from snownlp import SnowNLP
import jieba
import jieba.analyse

class SentimentAnalyzer:
    def analyze(self, text):
        """综合情感分析"""
        # 1. 情感分数 (SnowNLP)
        s = SnowNLP(text)
        sentiment_score = s.sentiments  # 0-1
        
        # 2. 关键词提取
        keywords = jieba.analyse.extract_tags(text, topK=20, withWeight=True)
        
        # 3. 情感判断
        if sentiment_score > 0.6:
            sentiment = '正面'
        elif sentiment_score < 0.4:
            sentiment = '负面'
        else:
            sentiment = '中性'
        
        # 4. 投资观点词识别
        invest_keywords = self.extract_invest_keywords(keywords)
        
        return {
            'sentiment': sentiment,
            'score': round(sentiment_score, 3),
            'keywords': [{'word': k, 'weight': round(w, 3)} for k, w in keywords],
            'invest_keywords': invest_keywords,
            'summary': s.summary(2)
        }
```

---

## 📊 分析效果 | Analysis Output

```
研报: 2024年AI行业深度报告
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
😊 整体情绪: 正面 (0.78)
📊 情绪强度: 强烈看多

🔑 核心关键词:
  人工智能(0.89)  大模型(0.85)  算力(0.82)
  芯片(0.78)      应用落地(0.75)  商业化(0.70)

💡 投资观点:
  推荐关注: AI应用、算力基础设施
  风险提示: 估值过高、竞争加剧

📝 摘要:
  AI行业正处于快速发展期，大模型技术持续突破，
  算力需求旺盛，商业化进程加速推进。
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
```

---

## 🎯 应用场景 | Use Cases

- 📈 **投资研究**：研报情绪量化分析
- 🏦 **券商研究**：行业深度报告自动分析
- 💼 **基金公司**：市场情绪监控
- 🧠 **NLP 教学**：金融文本情感分析项目

---

## 📄 License

MIT License — 自由使用、修改和分发。

---

> 💡 **金融研报智能情感分析，Star ⭐ 用 NLP 透视市场情绪！**
