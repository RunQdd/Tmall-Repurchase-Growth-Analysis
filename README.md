# Tmall Repurchase Growth Analysis

## 项目简介

本项目基于阿里云天池天猫用户复购预测数据集，围绕用户在商家维度下的历史行为日志，构建用户复购预测模型，并进一步从增长运营视角进行用户分层与策略分析。

项目目标不是单纯追求模型指标，而是模拟互联网增长策略产品运营岗位中的完整分析流程：

- 理解用户行为数据；
- 构建复购预测特征；
- 使用机器学习模型识别高潜复购用户；
- 基于预测结果提出用户分层和运营触达策略。

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
