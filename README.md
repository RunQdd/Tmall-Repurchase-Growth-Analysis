# Tmall Repurchase Growth Analysis

## 项目简介

本项目基于阿里云天池天猫用户复购预测数据集，围绕用户在商家维度下的历史行为日志，构建用户复购预测模型，并从增长运营视角进行用户分层与策略分析。

项目模拟互联网增长策略产品运营中的典型分析流程：理解用户行为数据、构建复购预测特征、识别高潜复购用户，并基于模型结果提出差异化触达策略。

## 项目流程

1. 数据读取与字段检查
2. label 分布分析与建模样本筛选
3. activity_log 行为日志解析
4. 用户行为特征与转化率特征构建
5. RandomForest baseline 建模
6. 阈值优化与特征重要性分析
7. 用户复购潜力分层
8. 增长运营策略输出

## 数据说明

本项目使用 data_format2 数据，核心字段包括：

| 字段 | 含义 |
|---|---|
| user_id | 用户 ID |
| age_range | 用户年龄段 |
| gender | 用户性别 |
| merchant_id | 商家 ID |
| label | 是否复购标签 |
| activity_log | 用户在该商家下的历史行为日志 |

其中，`activity_log` 记录用户在特定商家下的点击、加购、购买、收藏等行为，格式类似：

```text
item_id:cat_id:brand_id:time_stamp:action_type
