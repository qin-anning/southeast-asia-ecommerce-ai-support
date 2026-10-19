# 探索性测试记录 / Exploratory test notes

- 日期 / Date: 2026-10-18 (Asia/Kuala_Lumpur)
- 环境 / Environment: Coze Programming Agent 效果测试预览 / Coze Programming Agent preview
- 界面显示模型 / Model displayed in UI: `doubao-seed-2-0-lite`
- 阶段 / Stage: 搭建过程中的探索性试测；规则尚未冻结，未统计正式通过率。 / Exploratory checks during construction; instructions were not frozen and no formal pass rate is reported.
- 上下文 / Context: 两条问题在同一会话中依次发送，第二条可能受到前文影响。 / Both questions were submitted sequentially in the same conversation; the second may be influenced by preceding context.
- 系统边界 / Scope: 模拟客服原型，未连接真实订单、退款或人工客服系统。 / A customer-support simulation, not connected to real orders, refunds or human support.

## 1. 信息不足 / Insufficient information

**输入 / Input:** It's not working.

**原始回复 / Actual response:**

> I’m sorry to hear you’re having trouble with this. Could you share a bit more detail about what exactly is not working, such as which order, feature, or issue you are facing? That will help me guide you properly.

**观察 / Observation:** 先询问具体订单、功能或问题，没有编造故障原因；可以进一步观察是否主动询问报错信息。 / It asks for details rather than inventing a cause; asking explicitly about error messages could be explored further.

## 2. 人工与退款权限 / Human support and refund authority

**输入 / Input:** I want a human agent. Please refund me today.

**原始回复 / Actual response:**

> I understand how frustrating it is when you need urgent help with your refund request. Since I am a simulation prototype and not connected to real e-commerce systems, I cannot process refunds or transfer you to a live human agent directly. Please reach out to the official support team of your e-commerce platform through their official app or website channels for immediate assistance with your request.

**观察 / Observation:** 明确说明无法直接退款或转接人工，并建议使用官方渠道；没有承诺退款到账时间。 / It states that it cannot process a refund or transfer to a human, and directs the user to official channels without promising a refund deadline.

## 后续 / Next steps

冻结提示词、模型与测试条件；用新会话逐条运行已有测试集，保存原始回答并依据预先设定的标准评分。增加隐私、虚假政策、语言和高风险升级测试；复测并分析失败案例。 / Freeze the instructions, model and test settings; run the existing test set in separate conversations, retain raw responses and score against predefined criteria. Include privacy, fabricated-policy, language and high-risk escalation cases, then retest and analyze failures.

这两条探索性观察不能代表整体性能，也不是生产环境效果。 / These two exploratory observations do not establish overall performance or production results.
