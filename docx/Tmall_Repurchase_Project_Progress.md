# 天猫用户复购预测与增长策略分析项目进程记录

> 项目定位：面向互联网增长策略/产品运营/数据分析实习岗位，基于天猫用户复购预测数据，完成数据理解、建模评估、用户分层与增长策略输出。

---

## 1. 项目基本信息

| 项目项 | 内容 |
|---|---|
| 项目名称 | 基于天猫用户行为特征的复购预测与增长策略分析 |
| 数据来源 | 阿里云天池 / IJCAI-15 Repeat Buyers Prediction 相关数据集 |
| 当前数据版本 | data_format2 |
| 当前文件 | train_format2.csv、test_format2.csv |
| 当前进度 | 已完成 data_format2 解压缩，尚未整理项目文件夹 |
| 目标岗位 | 阿里巴巴增长策略产品运营日常实习生 |
| 项目关键词 | 用户增长、复购预测、用户分层、AUC、F1、SQL、Python、LightGBM |

---

## 2. 当前项目进程

### 已完成

- [x] 明确项目方向：天猫用户复购预测与增长策略分析
- [x] 确定项目适配岗位：增长策略产品运营 / 数据分析 / 用户运营
- [x] 下载并解压 `data_format2`
- [x] 确认解压后包含以下文件：
  - `train_format2.csv`
  - `test_format2.csv`

### 尚未完成

- [ ] 创建标准项目文件夹
- [ ] 将数据文件放入 `data/raw/`
- [ ] 使用 Python 读取并检查数据字段
- [ ] 检查 `label` 分布及是否存在 `-1`
- [ ] 完成缺失值处理
- [ ] 完成基础 EDA 分析
- [ ] 训练基础模型
- [ ] 输出 AUC、F1、Precision、Recall
- [ ] 完成用户复购潜力分层
- [ ] 输出增长策略建议
- [ ] 整理 README 和简历项目描述

---

## 3. 建议项目目录结构

建议新建项目文件夹：

```text
Tmall-Repurchase-Growth-Analysis/
├── data/
│   ├── raw/
│   │   ├── train_format2.csv
│   │   └── test_format2.csv
│   └── processed/
├── notebooks/
│   ├── 01_data_check.ipynb
│   ├── 02_eda_analysis.ipynb
│   ├── 03_model_training.ipynb
│   └── 04_user_segmentation.ipynb
├── output/
│   ├── model_metrics.csv
│   ├── feature_importance.csv
│   └── user_segment_summary.csv
├── report/
│   └── growth_strategy_report.md
├── sql/
│   ├── 01_data_check.sql
│   └── 02_feature_summary.sql
├── README.md
└── requirements.txt
```

---

## 4. 下一步操作清单

### Step 1：创建项目文件夹

在电脑本地创建：

```text
Tmall-Repurchase-Growth-Analysis
```

然后在里面创建：

```text
data/raw
data/processed
notebooks
output
report
sql
```

### Step 2：移动数据文件

将解压后的文件移动到：

```text
Tmall-Repurchase-Growth-Analysis/data/raw/
```

最终应为：

```text
data/raw/train_format2.csv
data/raw/test_format2.csv
```

### Step 3：创建第一个 Notebook

在 `notebooks/` 文件夹中新建：

```text
01_data_check.ipynb
```

用于完成数据读取、字段检查、缺失值检查和 label 分布检查。

### Step 4：运行数据检查代码

```python
import pandas as pd
import numpy as np

train = pd.read_csv("../data/raw/train_format2.csv")
test = pd.read_csv("../data/raw/test_format2.csv")

print("train shape:", train.shape)
print("test shape:", test.shape)

display(train.head())
display(test.head())

print(train.info())
print(test.info())

print(train.columns.tolist())
print(test.columns.tolist())

print(train["label"].value_counts(dropna=False))
print(train["label"].value_counts(normalize=True, dropna=False))
```

---

## 5. GitHub 仓库方案

### 方案 A：先本地整理，再上传 GitHub

适合当前阶段。先把项目文件夹结构整理好，再上传到 GitHub。

推荐仓库名：

```text
Tmall-Repurchase-Growth-Analysis
```

推荐仓库描述：

```text
A user repurchase prediction and growth strategy analysis project based on Tmall repeat buyer dataset.
```

### 方案 B：直接建立 GitHub 仓库并同步本地项目

#### 1. 在 GitHub 创建新仓库

仓库名建议：

```text
Tmall-Repurchase-Growth-Analysis
```

是否公开：

```text
Public
```

说明：

```text
基于天猫用户复购预测数据的用户增长与复购预测分析项目
```

#### 2. 在本地项目文件夹初始化 Git

进入项目文件夹后运行：

```bash
git init
```

#### 3. 创建 `.gitignore`

建议不要上传原始数据文件，尤其是大 CSV 文件。创建 `.gitignore`：

```gitignore
# data files
data/raw/
data/processed/

# notebook checkpoints
.ipynb_checkpoints/

# python cache
__pycache__/
*.pyc

# environment
.env
.venv/
venv/

# output files
output/*.csv
```

#### 4. 添加项目文件

```bash
git add .
git commit -m "Initialize Tmall repurchase analysis project"
```

#### 5. 连接远程仓库

将下面的链接替换成你自己的 GitHub 仓库地址：

```bash
git remote add origin https://github.com/你的用户名/Tmall-Repurchase-Growth-Analysis.git
git branch -M main
git push -u origin main
```

---

## 6. README 初稿结构

后续 `README.md` 可以按这个结构写：

```markdown
# Tmall Repurchase Prediction and Growth Strategy Analysis

## Project Background

This project focuses on predicting whether a new buyer will repurchase from the same merchant in the future, based on user behavior and merchant interaction features.

## Dataset

- Dataset: Tmall Repeat Buyer Prediction / IJCAI-15 Repeat Buyers Prediction
- Current version: data_format2
- Files:
  - train_format2.csv
  - test_format2.csv

## Project Workflow

1. Data understanding
2. Data cleaning
3. Exploratory data analysis
4. Feature preparation
5. Model training
6. Model evaluation
7. User segmentation
8. Growth strategy recommendations

## Model Evaluation

Main metrics:

- AUC
- F1
- Precision
- Recall

## Business Output

The project aims to identify high-potential repurchase users and provide growth strategies such as coupon targeting, cart abandonment recall, member retention, and low-potential user frequency control.
```

---

## 7. 当前简历项目描述草稿

当前阶段暂时不要写得太满，建议写成“进行中项目”：

```text
基于天猫用户行为特征的复购预测与增长策略分析（进行中）
基于阿里云天池天猫复购预测 data_format2 数据集，围绕用户画像、商家信息及用户-商家交互特征，计划完成数据清洗、样本筛选、模型训练与用户分层分析；项目将使用 Random Forest、LightGBM 等二分类模型预测用户未来是否复购，并采用 AUC、F1、Precision、Recall 等指标评估模型表现，最终输出高/中/低复购潜力用户分层及增长运营策略建议。
```

---

## 8. 近期任务优先级

| 优先级 | 任务 | 目标 |
|---|---|---|
| 高 | 建立项目目录 | 让项目可管理、可复现 |
| 高 | 放入数据文件 | 保证代码路径统一 |
| 高 | 读取数据并检查字段 | 明确数据结构 |
| 高 | 检查 label 分布 | 判断是否为样本不均衡问题 |
| 中 | 建立 README | 方便未来上传 GitHub |
| 中 | 创建 `.gitignore` | 避免上传大文件和缓存文件 |
| 中 | 开始基础建模 | 跑通 AUC / F1 |
| 低 | 做可视化报告 | 后续增强简历展示 |

---

## 9. 备注

当前项目尚未进入建模阶段。下一次继续推进时，应优先完成：

1. 项目文件夹创建；
2. 数据文件移动到 `data/raw/`；
3. 运行 `01_data_check.ipynb`；
4. 截图或复制字段名，用于判断后续建模和简历表达。
