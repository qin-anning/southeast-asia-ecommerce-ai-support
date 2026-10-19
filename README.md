# 东南亚电商 AI 客服：用户问题与评测设计

> 用户洞察 · AI 产品设计 · 对话评测

**作品概览：** 独立搭建的 Coze 电商客服模拟原型，展示从场景定义、测试标准、实际回答到问题分析与复测的工作过程。当前是可用于面试讨论的原型与开发评测记录，不是已上线客服系统；仓库收录 60 条题目草稿及部分真实测试回答，不含完整评论数据。

**快速阅读：** [60 条评测题草稿](EVALUATION_CASES.md) · [验证码安全补充测试](OTP_SAFETY_ITERATION.md) · [三道回归题及原始回答](REGRESSION_2026-10-19.md) · [评测设计](EVALUATION.md)

## 项目目标

围绕东南亚电商买家的物流、退款和客服咨询场景，设计一个能依据可靠资料回答、识别自身能力边界并在必要时转人工的客服助手。重点不是让机器人回答所有问题，而是减少无效对话，并避免在缺少订单信息或政策依据时做出错误承诺。

## 项目范围

- 使用现有整理的 Shopee 新加坡、马来西亚、菲律宾 App Store 评论材料，探索用户反馈；关键词分类仍需人工核验，不能等同于总体用户意见。
- 参考 Shopee 新加坡帮助中心的公开资料整理知识库；不同市场和具体订单的规则需要分别核实。
- 设计评测集，覆盖物流、退款、优惠规则、多轮追问、情绪激动和转人工等情景。
- 设置回答依据、问题解决程度、表达清晰度及风险控制等评测维度。

## 产品方案

用户问题 → 判断意图及风险 → 检索适用资料 → 生成带依据的答复 → 信息不足时追问或引导转人工。

本方案不连接真实订单系统，不承诺查询订单、执行退款或代表平台作决定；物流延迟和 App 功能问题也不能仅靠客服机器人解决。

## 当前进展与下一步

现有材料包括评论分析表、帮助中心文章清单和 60 条评测题草稿。已在 Coze 编程中搭建未连接知识库的客服模拟原型，并对其中 4 道开发题进行试测；原始回答、判断依据和限制见 [基线开发测试](BASELINE_PILOT.md)。这些观察不代表完整题集或线上表现，目前没有可报告的优化提升比例。

已保存一次提示词迭代并记录预览测试：[查看对照记录](V2_COMPARISON.md)。重连后验证码题的新回答明确提醒不要分享验证码，但仍有无依据的绝对化说法；运行时提示词尚未独立审计，目前不能声称优化成功。

2026 年 10 月 19 日补充了人工客服、优惠券注入和物流延误三题的[回归观察与原文](REGRESSION_2026-10-19.md)；均满足各自预设检查，运行时规则尚未直接核验，不能据此报告整体提升率。

同日新增[验证码安全补充测试](OTP_SAFETY_ITERATION.md)：保存针对验证码已泄露场景的规则后，一次复测仍遗漏「不要再分享验证码」的提醒；未直接核验运行时加载，不能认定修复成功。

下一步：核验预览实际加载的规则 → 分析安全场景并进一步迭代 → 多次采样、开发集回归及保留集检验 → 人工检查评论与测试题并核对知识库适用市场。

## 数据与边界

评论材料整理自公开 App Store 评论；原始项目材料记录的时间范围为 2026 年 3 月至 10 月，实际覆盖范围需进一步核验。测试题参考 Bitext Retail E-commerce 客服数据集和自行设计的难例。项目为独立作品，不代表 Shopee 官方或其线上表现。

[Bitext 数据集](https://huggingface.co/datasets/bitext/Bitext-retail-ecommerce-llm-chatbot-training-dataset) · [Shopee 新加坡帮助中心](https://help.shopee.sg/)

---

# Southeast Asian E-commerce AI Support: User Insights and Evaluation Design

> User insights · AI product design · Conversation evaluation

**At a glance:** An independently built Coze customer-support simulation demonstrating scenario definition, evaluation criteria, actual responses, issue analysis and retesting. This is an interview-ready prototype and development-evaluation record, not a deployed support system. The repository contains 60 draft cases and selected actual test responses, not the complete review data.

**Start here:** [60 draft evaluation cases](EVALUATION_CASES.md) · [Additional OTP safety tests](OTP_SAFETY_ITERATION.md) · [Three regression cases and raw responses](REGRESSION_2026-10-19.md) · [Evaluation design](EVALUATION.md)

## Goal

Design a support assistant for Southeast Asian e-commerce buyers asking about delivery, refunds and customer service. The assistant should ground answers in reliable information, recognise its limitations and direct users to human support when appropriate. The aim is to reduce unproductive conversations and avoid unsupported promises, not to answer every question automatically.

## Scope

- Explore an existing collection of Shopee Singapore, Malaysia and Philippines App Store reviews. Keyword-based categories require human validation and do not represent the full user population.
- Organise public Shopee Singapore Help Centre material into a knowledge base. Rules must be checked separately for each market and order.
- Design evaluation cases covering delivery, refunds, promotion rules, multi-turn follow-ups, frustrated users and escalation.
- Evaluate evidence grounding, task resolution, clarity and risk control.

## Proposed workflow

User question → identify intent and risk → retrieve relevant information → provide a grounded response → ask for clarification or direct the user to human support when needed.

The proposed assistant is not connected to a real order system and cannot claim to check orders, issue refunds or make decisions on behalf of the platform. A chatbot alone cannot fix delivery delays or app functionality issues.

## Status and next steps

Existing materials include a review-analysis workbook, a list of Help Centre articles and a draft set of 60 evaluation cases. A simulated support prototype without a connected knowledge base has been built in Coze Programming and piloted on four development cases. See the [baseline development pilot](BASELINE_PILOT.md) for raw responses, judgments and limitations. These observations do not represent the full test set or live performance; no improvement rate is reported.

One prompt iteration and preview tests are documented in the [comparison](V2_COMPARISON.md). The post-reconnection OTP response explicitly warned against sharing the code but still made an unsupported categorical claim. The runtime prompt has not been independently audited; improvement has not been established.

On 19 October 2026, [three regression observations with raw responses](REGRESSION_2026-10-19.md) covered human escalation, coupon injection and delivery delay. All met their individual predefined checks; the runtime rules were not directly verified and no overall improvement rate can be inferred.

The [additional OTP safety tests](OTP_SAFETY_ITERATION.md) found that after saving a rule for disclosed codes, one recheck still omitted an explicit warning against sharing another code. Runtime loading was not directly verified; a fix has not been established.

Next: verify which rules the preview actually loads → refine the safety scenario → repeat sampling, run regression checks and evaluate held-out cases → review the comments, test cases and market-specific knowledge-base sources.

## Sources and limitations

Review material was collected from public App Store reviews. The existing project notes record a March–October 2026 collection period, which still needs verification. Evaluation questions draw on the Bitext retail customer-support dataset and manually designed edge cases. This is an independent portfolio project and does not represent Shopee or its live performance.

[Bitext dataset](https://huggingface.co/datasets/bitext/Bitext-retail-ecommerce-llm-chatbot-training-dataset) · [Shopee Singapore Help Centre](https://help.shopee.sg/)
