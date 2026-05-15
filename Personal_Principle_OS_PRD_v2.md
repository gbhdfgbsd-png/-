# Personal Principle OS — 产品设计文档 (PRD)

> 版本: v2.0 | 日期: 2026-05-15 | 状态: 全层设计完成

---

## 目录

1. [系统定义](#一系统定义)
2. [设计哲学](#二设计哲学)
3. [系统运行模型](#三系统运行模型)
4. [系统架构](#四系统架构)
5. [各层详细设计](#五各层详细设计)
6. [维度体系设计](#六维度体系设计)
7. [交互设计](#七交互设计)
8. [信任圈机制](#八信任圈机制)
9. [系统健康与可读性](#九系统健康与可读性)
10. [系统自主学习机制](#十系统自主学习机制)
11. [系统可证伪性设计](#十一系统可证伪性设计)
12. [冷启动计划](#十二冷启动计划)
13. [设计决策记录](#十三设计决策记录)

---

## 一、系统定义

`[v1保留]`

Personal Principle OS 是一个**个人决策操作系统**：从真实决策行为中涌现底层原则，从外部高质量信息源中提取待验证假说，通过持续对比"你实际怎么做"和"你希望怎么做"之间的张力来驱动个人成长，并在每一个需要做判断的时刻提供基于你自己原则体系的双面论证辅助——而非替你做决策。

**它不是：** 知识库、笔记工具、格言收集册、检索式查阅手册、需要你打理的公司。
**它是：** 决策日志 + 假说验证引擎 + 原则涌现机制 + 对手盘决策辅助 + 认知演化追踪器。
**它像：** 定投纳斯达克——设定好规则后自动运行，你只在极少数结构性时刻介入。

### 系统核心价值锚定

`[v2迭代]`

系统存在的唯一理由：**帮你做出更好的决策。**

系统的不可替代价值集中在四件你用其他方式做不到的事：
1. **跨时间关联**——把你人脑无法同时hold住的、跨月跨年的决策数据关联起来
2. **强制对手盘**——在你所有朋友都可能顺着你说的情况下，结构性地给你反面论证
3. **无意识模式发现**——发现你完全没感觉的行为微趋势
4. **长期认知轨迹**——3年前怎么想、现在怎么想、变化的脉络

其他功能（记录、模式呈现、自我理解）系统都在做，但不是系统存在的理由——你用日记和自然反思也能部分做到。

### 系统终极目标

`[v2迭代]`

**系统的成功不是"被你永远使用"——而是"有一天你内化了足够的决策智慧，不再需要系统辅助也能高质量决策"。**

---

## 二、设计哲学（7条核心设计原则）

### 2.1 原则从行为中涌现，而非从外部灌入

`[v1保留]`

系统不预设任何原则。第一阶段的核心任务是"无判断地记录真实决策"。原则是从你的决策模式中被系统识别出来的——它们是你"实际在遵循的东西"，可能跟你"想成为的人"完全不同。这个差距才是系统真正工作的地方。

外部信息源的内容不是原则，是"待验证假说"——只有经过你真实决策的检验才能升级为你的原则。

### 2.2 张力是核心价值，而非一致性

`[v1保留]`

系统的核心输出不是"帮你做出正确的决策"，而是**持续暴露你的描述性原则（你实际怎么做）和规范性原则（你希望怎么做）之间的张力**。每一个张力都是一个成长点。系统帮你看见它、理解它、决定是接受它还是缩小它。

### 2.3 对手盘思维，而非确认偏误

`[v1保留]`

系统在每一个重要决策中都主动扮演对手盘。它不告诉你"你应该选A"，而是呈现"基于你的原则体系，正面论证指向A，但反面论证（同样来自你的原则体系）指向B"。最终裁决永远是你做。这是"决策质量提升"，不是"决策速度提升"。

### 2.4 零摩擦输入，系统自治运行

`[v2迭代]`

你负责"说"（语音/文字，无格式要求），系统负责"想"（分类、结构化、关联、反馈）。

系统输出**默认生效**，你只在不同意时介入。不是"确认才生效"，是"生效了你要改随时改"。系统从"需要你管理的公司"变为"自己运行的指数基金"。

### 2.5 时间连续性：一切记录都有前因后果

`[v1保留]`

没有任何一条记录是孤立的。每条决策都有回填追踪、每条原则都有生命周期、每条假说都有验证历史。系统保留完整的"原则演化史"——5年后你能看到一条清晰的"认知演化路径"。

### 2.6 遗忘与增长同等重要

`[v2迭代]`

系统不是只有吸气没有呼气的肺。增长机制（记录、入库、生成）必须有同等强度的压缩/遗忘机制与之配对。复杂度有硬上限，周期性压缩是结构性的、强制性的、自动执行的。

### 2.7 系统对自身价值诚实

`[v2迭代]`

系统必须能被证明没用。如果运行数据表明系统没有改善决策质量，系统有义务告诉你。可证伪性不是系统的弱点，是系统对你诚实的证明。

---

## 三、系统运行模型

`[v2迭代]`

### 3.1 系统成熟度曲线

```
用户认知投入
  ↑
  │  ████████████████████
  │  ██████████████████████████
  │  ████████████████████████████████████████████ ← 校准期结束
  │                                         ░░░░░░░░░░░░░░░░░░ ← 巡航态
  └──────────────────────────────────────────────────────────→ 时间
     校准期(30-60天)                          巡航期(永续)
```

### 3.2 三态运行模式

```yaml
system_states:
  calibration_mode:
    description: "用户教系统阶段"
    duration: "30-60天（直到所有确认行为毕业）"
    user_effort: "每天5-10分钟"
    behavior: "系统输出需确认，但每类确认有独立毕业条件"
    exit_condition: "所有确认行为的纠正率降到阈值以下"
    
  cruise_mode:
    description: "校准完成后的常态"
    user_daily:
      - "随时输入（想到就说，0摩擦，不需要确认）"
      - "需要时提问（决策咨询，主动发起）"
      - "固定时间看Briefing（<2分钟，≤5条）"
    user_monthly: "Sync Ritual（15分钟）"
    system_auto: "解析/分类/关联/检测张力/更新模式/压缩/遗忘"
    
  survival_mode:
    description: "用户状态差或高压期"
    trigger: "7天无输入 或 用户手动设置"
    behavior: 
      - "只存储输入，不做任何处理"
      - "不推送任何东西"
      - "不请求任何确认"
    recovery: "恢复输入后自动回升到cruise_mode，积压批量处理"
```

### 3.3 脉冲式运行节奏

系统活跃度随你的决策密度自动脉动，不是匀速运行。

```yaml
rhythm_detection:
  low_power_trigger: "连续14天输入<2条"
  full_power_trigger: "7天内输入≥5条 或 发起L5咨询 或 stakes=high"
  
  low_power_mode:
    - "不推送Briefing（除非你主动打开）"
    - "模式引擎暂停"
    - "只做：存储 + 长周期回填提醒"
    - "品质：完全安静，你感觉不到系统存在"
    
  full_power_mode:
    - "全层激活"
    - "Briefing恢复"
    - "主动关联推送"
    - "L5决策辅助全开"
    
  transition: "自动，不需要用户手动切换"
```

### 3.4 重激活校验协议

系统从低功耗切换到全功率时的第一个动作——校验而非直接调用旧数据。

```yaml
reactivation_protocol:
  trigger: "低功耗→全功率切换"
  first_action:
    - "取top 5最可能被调用的原则"
    - "检查每条原则的key_assumptions"
    - "对用户提一个问题"
  question: |
    距离上次活跃已经过了X个月。
    这些是你当时最核心的3条原则：
    ① [原则1] —— 前提是[情境A]
    ② [原则2] —— 前提是[情境B]
    ③ [原则3] —— 前提是[情境C]
    这些前提现在还成立吗？
  response_options:
    "是": "正常激活，全部原则可用"
    "部分变了": "标记变化原则降权使用，密集期后重新审视"
    "完全不同了": "所有原则标记待重新验证，进入重校准模式"
```

### 3.5 确认机制毕业条件

校准期内，每类确认行为有独立的退出跑道：

| 确认行为 | 毕业条件 | 毕业后行为 |
|---------|----------|-----------|
| 决策记录结构化 | 连续20条未修正 | 默认生效，不再呈现确认 |
| 维度分类 | 某Domain内连续10条未改 | 该Domain自动分类 |
| 试金石格式化 | 连续15条未调格式 | 默认入库 |
| 模式识别 | 前3个confirmed模式均认可 | 后续emerging直接标记 |
| TFRF评分 | 手动调分<2次/月 | 系统评分即终稿 |

**毕业不需要你手动操作——系统根据纠正率自动判断"我学够了"。**



---

## 四、系统架构

### 4.1 架构总览图

`[v1保留，层级标注为v2迭代]`

```
┌─────────────────────────────────────────────────────────┐
│                     用户交互层                            │
│  捕获 | 咨询 | 每日Briefing | 复盘回填 | 深度探索 | 信任圈│
└──────────────────────────┬──────────────────────────────┘
                           │
              ┌────────────┼────────────┐
              ▼                         ▼
┌──────────────────────┐  ┌──────────────────────────┐
│  Layer 0             │  │  Layer 1                  │
│  决策日志            │  │  试金石库                  │
│  (Decision Log)      │  │  (Touchstone Library)     │
│  source: SELF        │  │  source: EXTERNAL         │
│  支撑层              │  │  支撑层                    │
└──────────┬───────────┘  └────────────┬─────────────┘
           │                           │
           └─────────────┬─────────────┘
                         ▼
          ┌──────────────────────────────┐
          │  Layer 2                      │
          │  模式识别引擎                  │
          │  (Pattern Engine)             │
          │  ★ 核心价值层                  │
          └──────────────┬───────────────┘
                         ▼
          ┌──────────────────────────────┐
          │  Layer 3                      │
          │  原则层                       │
          │  (Principle Layer)            │
          │  描述性 + 规范性 + 已退役     │
          │  支撑层                       │
          └───────┬──────────┬───────────┘
                  │          │
                  ▼          ▼
┌─────────────────────┐ ┌────────────────────────┐
│  Layer 4            │ │  Layer 5                │
│  张力检测器          │ │  决策辅助层             │
│  (Tension Detector) │ │  (Decision Aid)         │
│  ★ 核心价值层        │ │  ★ 核心价值层           │
└─────────────────────┘ └────────────────────────┘
                  │          │
                  └────┬─────┘
                       ▼
          ┌──────────────────────────────┐
          │  Layer 6                      │
          │  演化追踪层                    │
          │  (Evolution Tracker)          │
          │  ★ 核心价值层                  │
          └──────────────────────────────┘
```

`[v2迭代]` **核心价值层（L2/L4/L5/L6）：** 提供你用其他方式做不到的独特价值——跨时间统计模式发现、无意识偏离检测、结构化对手盘、长期认知轨迹。
**支撑层（L0/L1/L3）：** 必须存在但不是系统的价值来源——它们是数据地基和结构资产。

### 4.2 层间数据流向

`[v1保留]`

| 从 → 到 | 传递什么 |
|----------|---------|
| 交互层 → L0 | 用户原始输入（决策记录） |
| 交互层 → L1 | 用户原始输入（信息源观点） |
| L0 → L2 | 全量决策记录，供模式扫描 |
| L1 → L0 | 相关假说推送（决策时关联） |
| L0 → L1 | 决策结果（反向验证假说） |
| L2 → L3 | 涌现的描述性原则 |
| L1 → L3 | 验证通过的假说升级为规范性原则 |
| L3 → L4 | 描述性vs规范性原则对比数据 |
| L3+L1+L0 → L5 | 原则+假说+历史类比，供决策辅助 |
| L0 → L4 | 每条新决策（即时扫描） |
| L2 → L4 | 新confirmed描述性模式/强度变化 |
| L4 → L3 | 原则修订建议 |
| L4 → L5 | active张力列表（决策辅助盲区提醒） |
| L4 → L6 | 张力生命周期事件（演化追踪核心事件源） |
| L4 → 交互层 | 张力报告（汇入每日Briefing） |
| 全层 → L6 | 所有变化事件，供演化追踪 |

---

## 五、各层详细设计

### Layer 0: 决策日志（Decision Log）

**定位：** 整个系统的数据地基。你负责输入最少信息，系统负责补全和推断剩余字段。**默认生效，不需要逐条确认。**

#### 数据结构

`[v1保留 + v2迭代字段]`

```yaml
decision_log_entry:
  id: "D-037"
  created_at: "ISO时间戳"
  raw_input: "原始语音转文字/直接文字"

  # 系统解析（默认生效，confidence<0.5时标记待确认）
  scenario: "场景一句话描述"
  options_identified:
    - id: "opt_1"
      description: "选项描述"
  chosen_option: "opt_X"
  stated_reason: "你说出的理由"
  parsing_confidence: 0.85  # [v2迭代] 解析置信度

  # 系统推断（你可修正）
  decision_dimensions: ["AX-001", "AX-005"]  # 引用维度轴ID
  emotional_signals:
    - type: "conflict|anxiety|excitement|calm|frustration"
      indicator: "触发判断的原文片段"
  confidence_level: "high|medium|low|conflicted"
  reversibility: "high|medium|low"
  time_pressure: "high|medium|low"
  stakes_level: "trivial|low|medium|high|critical"
  decision_speed: "immediate|same_day|days|weeks|months"

  # 自动关联
  related_decisions: ["D-012", "D-028"]
  related_hypotheses: ["T-023"]
  related_principles: ["PP-003"]

  # [v2迭代] 行为结构特征（用于双通道模式检测）
  behavior_structure:
    effort_level: "high|medium|low"
    novelty: "routine|familiar|novel"
    choice_pattern: "status_quo|change|escalation|de-escalation"

  # 信任圈外部视角
  external_perspectives:
    - source: "人名"
      type: "casual_conversation|lifeline"
      content: "观点内容"
      recorded_at: "日期"

  # 回填追踪 [v2迭代：按stakes分级]
  outcome:
    status: "pending|positive|negative|neutral|mixed"
    backfill_schedule: []  # 按stakes自动设定，见下方回填分级设计
    evaluations:
      - recorded_at: "日期"
        type: "feeling_only|preliminary|assessment|final"  # [v2迭代]
        assessment: "positive|negative|neutral"
        negative_nuance: ""  # [v2迭代] 即使正向，有没有小的负面后果
        notes: "描述"
    validates_hypotheses: []
    challenges_hypotheses: []
    validates_principles: []
    challenges_principles: []

  # 元数据
  input_method: "voice|text"
  completeness: "full|partial"
  tags: []
```

#### 前置质量门控

`[v2迭代]`

系统不是"做了你再检查"，而是"确定度不够就老实说不确定"：

```yaml
quality_gates:
  decision_record:
    minimum_fields: [scenario, choice, reason]  # 少于3项→系统追问而非自己瞎猜
    ambiguity_threshold: 0.5  # 解析confidence<0.5→标记"待确认"而非默认生效
    emotion_inference: "only_when_obvious"  # 不确定就标"未知"，不硬猜
```

#### 输入处理流水线

`[v2迭代]`

```
用户原始输入
  → Step 1: 分类（决策记录 / 信息源触发 / 闪念）
  → Step 2: 结构化提取（场景/选项/选择/理由）
  → Step 3: 维度推断 + 行为结构特征提取
  → Step 4: 历史关联（搜索相似决策/相关假说/相关原则）
  → Step 5: 默认生效写入（confidence≥0.5时）
  → Step 6: confidence<0.5的字段标记待确认，汇入每日Briefing
```

#### 确认后触发动作

`[v1保留]`

| 动作 | 逻辑 |
|------|------|
| 持久化存储 | 写入数据库 |
| 设置回填提醒 | 按stakes分级自动设定 |
| 通知Layer 2 | 模式引擎增量扫描 |
| 通知Layer 4 | 张力检测（与规范性原则对比） |

#### 回填时间分级设计

`[v2迭代]`

```yaml
backfill_timing:
  stakes_trivial: no_backfill  # 不浪费系统资源
  stakes_low: [7_days]
  stakes_medium: [30_days]
  stakes_high: [30_days_feeling_only, 90_days_real_assessment]
  stakes_critical: [30_days_feeling, 90_days_preliminary, 180_days_assessment, 365_days_final]

backfill_rules:
  high_and_critical_first_backfill:
    allowed_responses: ["记录当前感受", "记录客观变化"]
    NOT_allowed: ["正向/负向判断"]  # 太早判断会被短期情绪污染
  every_positive_backfill:
    forced_question: "这个决策有没有任何小的负面后果，即使总体正向？"
    purpose: "强制收集负向信号碎片，防止正向回填过多"
```

#### 决策日志压缩周期

`[v2迭代]`

```yaml
log_compression:
  cycle: "每90天执行"
  process:
    1: "识别已被模式引擎消化且产出confirmed原则的决策"
    2: "这些决策→压缩为一行摘要（日期+选择+结果）"
    3: "原始详细记录→删除（不是归档，是删除）"
    4: "保留：未消化的 + 有回填标记的 + stakes≥high的"
  purpose: "防止只增不减的膨胀。一旦信息价值被提取到原则和模式里，原始记录不需要永久保留"
```

#### 边界条件

`[v1保留]`

| 场景 | 处理方式 |
|------|---------|
| 输入信息不完整 | 不阻断，能提取的提取，标记partial，Briefing提醒补充 |
| 一天记20条 | 不限制，但系统基于stakes_level加权分析深度 |
| 回填时忘了 | "我已忘了"本身就是信息（影响小的证据） |
| 评价反转 | 保留所有版本，标记evaluation_reversed，提取reversal_insight |

---

### Layer 1: 试金石库（Touchstone Library）

**定位：** 存放外部信息源的观点，格式化为"待验证假说"。不是笔记本——每条内容都有生命周期，最终要么升级为原则，要么被推翻退役。

`[v1保留]`

#### 数据结构

```yaml
touchstone_entry:
  id: "T-089"
  created_at: "ISO时间戳"

  # 原始输入
  raw_input: "用户原始语音/文字"
  original_quote: "信息源原始表述"
  source:
    person: "万维钢"
    platform: "得到·精英日课"
    specific_content: "第5季第234期"
    date_consumed: "2026-05-13"
  your_reaction: "你为什么觉得有道理"

  # 系统格式化
  hypothesis:
    statement: "可操作的假说表述（去修辞、去金句化）"
    actionable_implication: "如果成立，在决策中意味着什么"
    trigger_scenarios:
      - "场景描述1"
      - "场景描述2"
    boundary_conditions:
      known: ["已知适用边界"]
      uncertain: ["待明确的边界问题"]
    quality_score:  # TFRF评分
      trigger: 0-3
      falsifiability: 0-3
      resolution: 0-3
      fidelity: 0-3
      total: 0-12
      grade: "A|B|C|D"

  # 验证生命周期
  lifecycle:
    status: "active_hypothesis|under_testing|partially_validated|validated|challenged|refined|retired|promoted"
    validation_events:
      - date: "日期"
        decision_id: "D-045"
        result: "positive|negative|neutral"
        notes: "描述"
    validation_score:
      positive_count: 0
      negative_count: 0
      total_opportunities: 0
      utilization_rate: 0.0
    promotion_criteria:
      min_positive_validations: 3
      max_negative_ratio: 0.25
      min_time_span_days: 30

  # 关联
  relationships:
    supports: ["T-xxx"]
    conflicts_with:
      - id: "T-034"
        conflict_description: "冲突描述"
        resolution_status: "unresolved|resolved"
    refines: []
  related_decisions: []

  # 分类
  domains: ["decision_quality", "time_allocation"]
  entry_type: "actionable_hypothesis|value_orientation"
  hypothesis_level: "framework|derived|instance"

  # 元数据
  importance_to_you: "high|medium|low"
  revisit_count: 0
```

#### 假说化质量标准（TFRF四维框架）

`[v1保留]`

| 维度 | 检验问题 | 3分 | 0分 |
|------|---------|-----|-----|
| T-Trigger | 什么场景想起它？ | 有场景+进入条件+排除条件 | 无触发("永远适用"=永远想不起) |
| F-Falsifiability | 什么结果能证明它错？ | 有明确失败条件 | 不可证伪→转value_orientation |
| R-Resolution | 能在几次决策中验证？ | ≤5次, ≤90天 | 不可在有限决策中验证 |
| F-Fidelity | 格式化后是否忠实原始逻辑？ | 保留核心推导+关键条件 | 歪曲原意 |

总分12分分级：
- A(10-12)：直接入主动匹配池
- B(7-9)：可用，标记改进空间
- C(4-6)：入库但不主动匹配
- D(0-3)：建议转通道或重写

#### X和Y的颗粒度控制

`[v1保留]`

**X（触发）黄金颗粒度：** 每月出现1-3次的场景类型。太粗=等于没触发，太细=验证周期太长。

**Y（行为指引）黄金颗粒度：** 告诉你"做什么类型的选择"而非"做哪个具体选择"。

模板：
- "选择[选项类型A]而非[选项类型B]"
- "在[具体步骤]之后再做决定，而非立即行动"
- "把[资源X]投在[方向类型]而非[方向类型]"

#### 假说层级

`[v1保留]`

| 层级 | 定义 | 验证方式 |
|------|------|---------|
| framework | 框架级，统摄性观点 | 间接验证（通过下层假说） |
| derived | 推导级，从框架推出 | 可直接验证 |
| instance | 实例化，最具体 | 最快验证 |

子假说验证结果向上传递给框架级假说。

#### 输入处理流水线

`[v1保留]`

```
用户输入（"刚看了某某的文章，他说……"）
  → Step 1: 确认是"信息源触发"类型
  → Step 2: 提取原始观点/来源/用户反应
  → Step 3: 假说化（去修辞 → 转为"如果X则Y"可操作结构）
  → Step 4: TFRF质量评分
  → Step 5: 适用边界初步划定（known + uncertain）
  → Step 6: 冲突检测（扫描现有库，标记supports/conflicts）
  → Step 7: 默认生效写入（校准期毕业后不再需要确认）
```

#### 日常运行逻辑（被动触发）

`[v1保留]`

每当Layer 0有新决策记录写入：
1. 新决策的dimensions与所有active假说的trigger_scenarios匹配
2. 匹配度>阈值 → 在决策反馈中提示："相关假说T-089，是否参考了它？"
3. 用户选择"是/否" → 记录为validation_event
4. 后续决策结果好/坏 → 更新validation_score

#### 升级流程（假说→原则）

`[v1保留]`

满足promotion_criteria时：
1. 系统推送升级建议
2. 整合正向+负向验证结果，修正原始表述
3. 生成建议的原则表述（含负向验证带来的边界约束）
4. 用户确认 → 正式升级至Layer 3，status变为promoted

#### 批量导入机制

`[v1保留]`

1. 用户提供原始素材（文稿/文章/课程笔记）
2. 系统"原则密度扫描"——识别所有"有明确立场+有推导逻辑"的观点
3. 每个观点生成候选假说
4. 呈现给用户快速审核：入库 / 不入库 / 跳过 / 修改
5. 去重：相似>80%→合并；更精确→标记精细化关系；冲突→两条都保留标记冲突

#### 复杂度硬上限

`[v2迭代]`

```yaml
touchstone_budget:
  active_hypotheses_hard_cap: 100
  at_cap_behavior: "TFRF评分最低的10条自动降级为archived"
  monthly_scan: "D级建议处理 / C级>60天未精炼建议降级 / 来源平均分趋势"
```

#### 特殊类型处理

`[v1保留]`

- **价值取向声明**："人生的意义在于体验"等不可单次验证的观点 → 标记为value_orientation → 不走验证流程 → 通过"长期一致性认同"升级
- **不可证伪观点**：标记value_orientation走另一条通道
- **一条输入含多个判断**：建议拆分为假说群（标记relationships.supports）



---

### Layer 2: 模式识别引擎（Pattern Engine）

**定位：** 后台运行的"大脑"，从决策日志中发现你未意识到的行为规律。你不直接输入任何东西给这层——它纯粹吃Layer 0的数据。产出是描述性原则。★核心价值层——提供你自然反思做不到的跨时间统计发现。

#### 双通道模式检测

`[v2迭代]`

```yaml
pattern_detection_dual_channel:
  channel_1_reason_based:
    source: "stated_reason字段"
    method: "语义聚类，找重复逻辑"
    risk: "可能被事后合理化污染"
    
  channel_2_behavior_based:
    source: "选择本身的结构特征（behavior_structure字段）"
    method: "不看理由，只看选项客观属性"
    features: [reversibility, stakes, time_horizon, effort_level, novelty, choice_pattern]
    
  cross_validation:
    both_channels_agree: "高置信度模式"
    only_channel_1: "⚠️ 可能是合理化产物，降权处理"
    only_channel_2: "🔥 用户无意识的真实倾向——最高价值发现"
```

#### 模式类型

`[v1保留 + v2迭代新增隐性模式]`

| 类型 | 定义 | 示例 |
|------|------|------|
| 偏好模式 | 某类场景中稳定偏好某种选择 | "金钱vs时间权衡时，80%选时间" |
| 情绪-行为模式 | 特定情绪与特定决策行为的关联 | "焦虑时决策速度快3倍，后悔率高" |
| 反模式 | 声称做A但实际反复做B | "说重视深度工作但62%时段选了碎片化" |
| 隐性模式 `[v2迭代]` | 行为通道发现但理由通道没有的 | "你总说选长期，但行为结构显示你80%选低effort" |

#### 数据结构

`[v1保留]`

```yaml
pattern_entry:
  id: "PAT-012"
  discovered_at: "时间戳"
  last_updated: "时间戳"
  pattern_type: "preference|emotion_behavior|anti_pattern|implicit"

  description: "自然语言描述"

  structured_definition:
    trigger_condition:
      dimensions_involved: ["AX-001"]  # 引用维度轴
      scenario_keywords: ["兼职", "外包", "短期收入"]
    observed_tendency:
      direction: "long_term_investment"
      strength: 0.78  # 0-1
      consistency: "high|medium|low|volatile"
    conditions:
      holds_when: ["经济压力中等或较低", "有明确项目方向"]
      breaks_when: ["经济压力极高+时间紧迫"]

  # [v2迭代] 双通道检测来源
  detection_channel:
    source: "reason_based|behavior_based|both"
    cross_validation_status: "confirmed|reason_only|behavior_only"

  evidence:
    supporting_decisions: ["D-012", "D-028", "D-037"]
    contradicting_decisions: ["D-008", "D-019"]
    total_relevant_decisions: 9
    confidence_level: "emerging|moderate|high|very_high"
    temporal_distribution:
      earliest: "日期"
      latest: "日期"
      concentration: "concentrated|distributed"

  emotional_correlation:  # 仅emotion_behavior类型
    trigger_emotion: "anxiety"
    behavioral_change: "decision_speed_increase"
    outcome_correlation: "negative"

  lifecycle:
    status: "emerging|confirmed|evolving|weakening|dissolved"
    status_history: []
    trend_prediction:
      direction: "strengthening|stable|weakening"
      confidence: "high|medium|low"

  principle_connection:
    derived_principle_id: "DP-007"
    alignment_with_prescriptive:
      aligned_with: ["PP-003"]
      conflicts_with: ["PP-011"]  # 产生张力

  user_acknowledged: true|false
  user_reaction: "agree|disagree|partially_agree|surprised"
```

#### 模式呈现方式

`[v2迭代]`

不再呈现"发现模式→让你确认"。而是呈现完整分布（含反例）→你自判断：

```
"在'短期vs长期'维度上，你过去30天的15条决策分布：
 · 12次选了长期方向（场景特征：经济压力低、时间充裕）
 · 3次选了短期方向（场景特征：deadline紧、情绪焦虑）
 
 你怎么理解这个分布？
 [这就是我的模式] [比这复杂] [我没意识到那3次]"
```

**前者（v1）引导确认，后者（v2）引导思考。**

#### 维度体系在模式引擎中的角色

`[v1保留]`

模式识别引擎使用维度轴（Axis）作为聚类单位。只有积累≥5条决策的维度轴才进入模式发现流程。

#### 运行时机

`[v1保留]`

| 频率 | 类型 | 做什么 |
|------|------|--------|
| 每条新决策 | 增量扫描 | 这条记录是否为某个已知emerging模式提供新证据？ |
| 每周一次 | 全量扫描 | 是否有新模式涌现？已有模式强度/趋势变化？ |
| 每月一次 | 深度分析 | 跨模式关联（共现、反相关、周期性）+ 双通道交叉验证 |

#### 增量扫描逻辑

`[v1保留]`

```
新决策D-063写入
  → 提取dimensions → 匹配已知emerging/confirmed模式的trigger_condition
  → 匹配到PAT-012
  → 判断方向（一致/不一致）→ 加入supporting/contradicting
  → 重新计算strength/consistency/confidence
  → 如果从emerging达到confirmed条件 → 推送通知用户
```

#### 全量扫描逻辑

`[v1保留]`

```
Phase 1: 维度聚类（找积累≥5条决策的维度轴）
Phase 2: 倾向检测（某方向占比>65% → 候选偏好模式）
Phase 3: 条件分析（反例共同特征→breaks_when; 强例特征→holds_when）
Phase 4: 新旧对比（重复→合并; 新发现→创建emerging）
Phase 5: [v2迭代] 双通道交叉验证（理由通道和行为通道是否一致）
```

#### 边界条件

`[v1保留]`

| 场景 | 处理 |
|------|------|
| 数据不够（<5条） | 不输出，宁缺毋滥。前30天只积累不输出 |
| 无稳定偏好（50/50） | 标记为"无模式"——可能需要在该领域形成原则 |
| 识别错误 | 用户可否定。连续2次否定→停止追踪该候选 |
| 行为快速变化 | 检测"相变"（14天偏移>25%）→确认重大事件→旧模式存档，重新积累 |
| 看到但不想改 | 标记acknowledged_accepted，不触发张力检测 |

#### 模式→原则的升级路径

`[v1保留]`

```
数据积累 → 模式涌现(emerging) → 证据充分(confirmed) → 用户确认 → 形成描述性原则(DP)
```

---

### Layer 3: 原则层（Principle Layer）

**定位：** 系统核心资产库。有层级、有关系、有生命周期的活体结构，不是平面列表。

#### 原则类型

`[v1保留]`

| 类型 | ID前缀 | 来源 | 含义 |
|------|--------|------|------|
| 描述性(Descriptive) | DP- | Layer 2模式涌现 | "你实际在做什么" |
| 规范性(Prescriptive) | PP- | Layer 1升级 + 主动声明 | "你希望怎么做" |
| 元原则(Meta) | MP- | 用户主动声明 | 最高层统摄，≤5条 |
| 已退役(Retired) | RP- | 曾是DP/PP，后被推翻 | "曾经信过但不再信" |

#### 数据结构

`[v1保留]`

```yaml
principle_entry:
  id: "PP-003"
  created_at: "时间戳"
  type: "prescriptive|descriptive|meta|retired"

  # 来源溯源
  origin:
    path: "hypothesis_promotion|pattern_emergence|user_declaration|decision_lesson|principle_refinement"
    source_id: "T-023"
    original_source:
      person: "李笑来"
      content: "把时间投在复利最高的地方"
      platform: "富足人生社群"

  # 原则内容（三层表述）
  statement: "面对'短期收入vs长期积累'时，默认选长期积累，除非短期生存受威胁。"

  reasoning:
    logic: "长期积累有复利效应，短期收入是线性的。但前提是你活着才能享受复利。"
    key_assumptions:
      - "有基本生存保障（短期不会饿死）"
      - "选择的方向确实有复利效应"
      - "有足够自制力持续投入"
    assumption_sensitivity:
      - assumption: "有基本生存保障"
        if_violated: "原则失效，切换生存模式"
        violation_threshold: "月收入<基本开销70%持续超过2个月"

  operational_guide:
    decision_rule: |
      1. 检查生存条件：当前现金流>70%基本开销？
      2. 满足 → 默认选长期积累
      3. 不满足 → 选短期收入，设退出条件（恢复安全线后立即回到长期）
    quick_test: "如果选了短期收入，一年后回看会不会觉得浪费了时间？会→选长期。"

  # 适用边界
  boundaries:
    applies_to:
      domains: ["career_direction", "time_allocation", "financial_decisions"]
      scenario_triggers: ["出现兼职/外包机会", "需要在赚钱和做项目间分配时间"]
    does_not_apply_to: ["纯消费决策", "学习方向AB选择", "紧急情况"]
    edge_cases:
      - scenario: "短期收入很高（>正常3倍）"
        guidance: "额外评估：这个'短期高收入'是否本身有长期价值（人脉/经验/背书）"

  # 验证记录
  validation:
    total_applications: 7
    positive_outcomes: 5
    negative_outcomes: 1
    pending_outcomes: 1
    application_log:
      - decision_id: "D-012"
        date: "日期"
        applied: true
        outcome: "positive"
        notes: "拒绝兼职，项目有进展"
        context_snapshot:
          life_stage: "early_career"
          financial_state: "stable"
          time_freedom: "high"
          responsibility_level: "low"
          primary_role: "independent_creator"
    validation_strength:
      score: 0.83
      reliability: "high"
      time_span_days: 97

  # 层级关系
  hierarchy:
    level: "meta_principle|principle|sub_principle"
    parent_id: "MP-002"
    children_ids: []
    sibling_ids: ["PP-004", "PP-005"]

  # 原则间关系
  relationships:
    supports: ["PP-007"]
    tensions_with:
      - id: "DP-012"
        tension_id: "TEN-003"
    supersedes: []
    superseded_by: null

  # 权重与优先级
  weight:
    importance: "critical|high|medium|low"
    frequency: "daily|weekly|monthly|rare"
    priority_tier: 2  # 1=绝对(生存), 2=核心(人生方向), 3=一般, 4=偏好
    override_conditions: ["Tier 1原则冲突时让步"]

  # 张力敏感度设置
  tension_sensitivity:
    threshold: 0.40
    min_sample: 3
    window_days: 30
    cooldown_days: 14

  # 情境有效性
  context_validity:
    status: "VALID|SUSPENDED|RE-VALID|REVISED|RETIRED"
    context_anchors:
      - life_stage: "early_career"
        financial_state: "stable"
        time_freedom: "high"
        responsibility_level: "low"
        primary_role: "independent_creator"
    context_distance_to_current: 0.0  # 0-1, >0.5触发SUSPENDED

  # 生命周期
  lifecycle:
    status: "active|under_review|suspended|retired|evolved"
    version: 2
    version_history:
      - version: 1
        date: "日期"
        statement: "旧版表述"
        change_reason: null
      - version: 2
        date: "日期"
        statement: "新版表述"
        change_reason: "D-008和D-019经验表明需加入生存条件例外"
    next_review_date: "2026-09-20"
    review_interval_days: 90
```

#### 层级体系

`[v1保留]`

```
Meta-Principles（≤5条，最高优先级，极少变动）
│
├── MP-001: "生存和健康是一切的底层基础设施"
│   ├── PP-009: "睡眠不足6小时不做重要决策"
│   ├── PP-010: "身体警告时工作让位休息"
│   └── PP-011: "永远保持≥3个月开销现金储备"
│
├── MP-002: "时间是不可再生资源，每个时间决策都是投资决策"
│   ├── PP-003: "短期收入vs长期积累：默认选长期"
│   ├── PP-004: "学习选择：优先选有复利效应的技能"
│   └── PP-005: "社交时间：优先投在长期互利的关系"
│
├── MP-003: "决策质量 > 决策速度（除非试错成本极低）"
│   ├── PP-006: "重大决策前主动研究反面案例"
│   ├── PP-007: "不在焦虑/情绪波动下做重大决策"
│   └── PP-008: "可逆决策快执行，不可逆决策谨慎推导"
│
└── [待涌现]
```

#### 原则形成的4条通道

`[v1保留]`

| 通道 | 路径 | 特征 |
|------|------|------|
| 1. 试金石升级 | 假说→多次验证→升级 | 有外部来源，经实践检验 |
| 2. 模式涌现 | 决策积累→模式确认→你认可 | 来自行为数据 |
| 3. 决策教训 | 极好/极差结果→提炼经验 | 来自深刻经历 |
| 4. 主动声明 | 你想清楚了→录入 | 初始unvalidated，需后续验证 |

#### 冲突裁决机制

`[v1保留]`

**优先级体系：**
- Tier 1: 生存和安全（绝对优先）
- Tier 2: 核心人生方向
- Tier 3: 日常决策标准
- Tier 4: 偏好（锦上添花）

**同级冲突裁决流程：**
1. 明确冲突点
2. 检查适用边界（有一条在当前场景不适用？→消解）
3. 检查前提假设（某条前提不成立？→该条暂失效）
4. 上面都没消解 → 呈现给用户做最终裁决
5. 同类冲突反复出现且裁决一致 → 建议增加"仲裁原则"

裁决记录完整保留：两条冲突ID、场景、裁决方法、胜出方、新认知。

#### 情境依赖与有效性状态模型

`[v1保留]`

原则有效性受三个独立变量影响：时间距离 / 情境距离 / 你自身的距离。

**有效性状态流转：**
```
情境不变 → VALID(高置信)
→ 情境重大变化 → SUSPENDED(存疑,需re-validation)
→ 新情境验证仍成立 → RE-VALID(跨情境稳定)
→ 需要修订 → REVISED
→ 不再适用 → RETIRED
```

**情境锚点：** 每条validation记录附带context_snapshot（life_stage/financial_state/time_freedom/responsibility_level/primary_role）

**context_distance计算：** 当前情境 vs 验证时情境的加权差异。distance>0.5的原则→SUSPENDED。

**情境相变检测：**
- **显式**：用户声明"我毕业了/工作了/搬城市了" → 扫描所有原则 → 标记distance>0.5为SUSPENDED → 呈现哪些需re-validation
- **隐式**：系统从数据中推断（time_pressure分布突变/新维度出现/financial维度频率×3）→ 轻量询问

**Re-validation机制：** 不是单独任务——嵌入正常使用。原则下次自然触发时附带情境提醒："这条在不同条件下验证过。请确认当前前提是否满足。"

#### 复杂度硬上限

`[v2迭代]`

```yaml
principle_budget:
  active_principles_hard_cap: 40
  at_cap_behavior: "新原则入库→系统必须同时提案一条旧原则退役/合并/降级"
  auto_merge_trigger:
    condition: "两条原则在同Domain + 验证历史70%重叠 + 核心逻辑可抽象涵盖"
    action: "系统提案合并为一条更高层原则"
    grace_period: "合并后6个月运行正常→旧两条真正删除"
```

#### 定期复查

`[v1保留]`

| 层级 | 复查周期 | 深度 |
|------|---------|------|
| Meta (Tier 1) | 6个月 | 深度（重新审视是否认同） |
| Tier 2 | 3个月 | 中等（验证数据+边界检查） |
| Tier 3-4 | 3个月 | 轻量（是否还在被使用？） |
| validation负向增多 | 立即 | 紧急复查 |
| 6个月未触发 | - | 建议降级或退役 |
| SUSPENDED状态 | 下次自然触发时 | Re-validation |

#### 退役流程

`[v1保留]`

触发条件：复查时选择退役 / 连续3次负向验证 / 6个月未触发 / 被新原则替代 / context_validity=RETIRED

流程：确认意图→记录退役原因→type变为retired→完整保留历史数据→不删除

退役原则价值：演化追踪展示认知变化；决策辅助在特殊场景可能提醒"你曾有相关原则但退役了"。



---

### Layer 4: 张力检测器（Tension Detector）

**定位：** ★核心价值层。持续对比描述性原则和规范性原则，检测"你说的"和"你做的"之间的差距，输出张力报告。提供你自然反思无法感知的偏离率数据。

张力不是原则间的逻辑矛盾——**张力是行为与意图之间的裂缝在特定时间窗口内的累积。**

`[v1保留]`

两条原则文本上矛盾不一定产生张力（可能从没在同一场景里被同时调用过）。两条看似无关的原则，可能因为真实行为暴露了隐藏的取舍关系而产生剧烈张力。

张力检测器的输入不是"两条原则的文本"，而是"一个行为序列 + 一条规范性原则 + 时间窗口"。

#### 张力的精确定义

`[v1保留]`

```
张力 = 在时间窗口T内，你的实际决策模式（描述性）与你声称希望遵循的标准（规范性）
       之间的累积偏离，达到了你自己设定的敏感度阈值。
```

关键词：
- **累积偏离**：单次不遵循不是张力，是例外。系统抓趋势不抓个案。
- **时间窗口**：张力有时效性。3个月前偏离5次但最近2个月完美遵循——张力已消解。
- **敏感度由你设定**：不同原则的可容忍偏离度不同。

#### 张力的四种来源类型

`[v1保留]`

| 类型 | 定义 | 检测方式 | 示例 |
|------|------|---------|------|
| 行为-意图张力 | DP-X与PP-Y指向相反 | 模式引擎输出vs原则库对比 | DP:"焦虑时快速决策" vs PP:"不在情绪波动下做重大决策" |
| 频率-声明张力 | 某PP声称高频使用但实际使用率低 | utilization_rate计算 | PP-003被触发12次，实际遵循4次 |
| 结果-信念张力 | 某PP一直遵循但结果持续为负 | validation负向累积 | 一直选长期积累但连续3次方向选错 |
| 演化-锚定张力 | 行为已相变但规范性原则还锚定旧模式 | 相变检测+原则最后更新时间 | 毕业后行为转向执行力但原则还在说"深度思考优先" |

**第四种"演化-锚定张力"最有价值也最难检测**——揭示的不是"你没做到"，而是"你已经变了但操作系统没跟上"。

#### 数据结构

`[v1保留]`

```yaml
tension_entry:
  id: "TEN-017"
  detected_at: "时间戳"
  last_updated: "时间戳"
  type: "behavior_intent|frequency_claim|outcome_belief|evolution_anchor"

  descriptive_side:
    principle_id: "DP-008"
    statement: "描述性侧表述"
    evidence_window:
      start: "日期"
      end: "日期"
      relevant_decisions: ["D-045", "D-051", "D-053"]
      direction_summary: "在5次相关决策中，4次选择了快速执行"

  prescriptive_side:
    principle_id: "PP-007"
    statement: "规范性侧表述"
    expected_behavior: "重大决策前至少等待24小时冷静期"

  measurement:
    deviation_rate: 0.80
    time_window_days: 30
    sample_size: 5
    trend: "widening|stable|narrowing"
    severity: "mild|moderate|significant|critical"
    # mild: 偏离率<40%或样本<3
    # moderate: 40-60%
    # significant: 60-80%
    # critical: >80%且样本≥5且原则tier≤2

  context_analysis:
    common_triggers: ["时间压力高", "stakes判断为medium以下"]
    emotional_correlation: "anxiety → 偏离概率+40%"
    outcome_when_deviated:
      positive: 2
      negative: 1
      neutral: 1
    outcome_when_followed:
      positive: 1
      negative: 0
      neutral: 0

  diagnosis:
    hypothesis: "execution_gap|principle_outdated|boundary_missing|context_dependent"
    confidence: "high|medium|low"
    reasoning: "诊断推理过程"

  user_response:
    acknowledged: false
    response_type: null
    # accept_tension → 想缩小差距
    # accept_behavior → 原则该更新
    # add_boundary → 加例外条件
    # dismiss → 误检
    # defer → 以后处理
    action_taken: null

  lifecycle:
    status: "active|acknowledged|resolving|resolved|recurring|dismissed"
    resolution_history: []
    recurrence_count: 0
```

#### 张力呈现框架轮换

`[v2迭代]`

**不再固定用"偏离率"框架——随机轮换三种解读，防止用户内化"偏离=问题"的固定心智模型：**

```yaml
tension_framing:
  rotate_randomly_each_time:
    frame_A: "PP-003偏离率40%。你的行为在偏离你的原则。"
    frame_B: "你的行为在过去6周呈现新模式。PP-003可能不再描述真实的你。"
    frame_C: "数据显示PP-003和近期行为不一致。可解读为'偏离'或'原则过时'。你怎么看？"
```

#### 张力报告呈现设计

`[v1保留]`

**核心原则：不是批评，是镜子。绝对禁止暗含"你做错了"的表述。**

```
⚡ 张力报告 TEN-017 | 日期

📐 你声称的标准：
PP-007 "不在焦虑/情绪波动下做重大决策"

▪ 你最近30天的实际行为：
5次相关决策中，4次在情绪高波动状态下做出
偏离率：80% | 趋势：扩大

🔬 模式分析：
· 4次偏离中3次time_pressure=high
· 偏离后结果：2正向, 1负向, 1待定
· 1次遵循（D-049）特征：stakes=critical, 主动延迟24小时

🤔 系统假设（不是结论）：
你可能隐含地区分了"真正重大"和"自以为重大但可快速判断的"。
PP-007可能需要边界条件："stakes≥high时适用，medium以下允许快速判断"。

你怎么看？
[🎯 想缩小差距] [🔄 原则该更新] [📐 加边界条件] [✗ 误检] [⏰ 以后再说]
```

#### 检测引擎运行逻辑

`[v1保留]`

| 触发 | 做什么 | 延迟 |
|------|--------|------|
| 每条新决策写入 | 即时：是否偏离某PP？写入violation_buffer | 不立即报告单次偏离 |
| 偏离累积达阈值 | 生成张力报告 | 检测到立即生成，推送受不打扰规则约束 |
| 每周全量扫描 | 遍历所有active PP计算遵循率 | 周报呈现 |
| 模式引擎输出新confirmed模式 | 与所有PP对比检查新张力 | 随模式通知一起 |
| 原则形成/修改 | 新PP生效时回扫最近30天 | 原则确认后立即 |

即时扫描逻辑：
```
新决策D-063写入
  → 提取dimensions + chosen_option + emotional_signals
  → 匹配所有PP的scenario_triggers
  → 命中PP-007 → 检查：情绪高波动？stakes≥medium？
  → 判定偏离 → 写入violation_buffer
  → 检查buffer：30天窗口内偏离率 = 4/5 = 0.80 > threshold(0.40)
  → 触发张力报告生成
```

#### 用户响应后系统动作

`[v1保留]`

| 选择 | 动作 |
|------|------|
| 想缩小差距 | 进入行动计划：确认触发场景→设计干预点→设跟踪窗口 |
| 原则该更新 | 触发修订流程：呈现当前→你给新表述→系统检查关系→确认更新 |
| 加边界条件 | 在boundaries.edge_cases新增→回测数据→确认 |
| 误检 | 记录原因→调整trigger/检测逻辑→连续2次误检→暂停该PP张力检测 |
| 以后再说 | 保持active→设defer_until→到期再推 |

#### 张力生命周期

`[v1保留]`

```
检测到偏离累积 → active → 推送用户 → 用户响应：
  ├── accept_tension → resolving → 跟踪 → 偏离率下降 → resolved
  ├── accept_behavior → 原则更新 → resolved(principle_updated)
  ├── add_boundary → 原则边界更新 → 重新计算 → 可能消失
  ├── dismiss → dismissed（不再检测，除非手动恢复）
  └── defer → deferred → 到期重推

resolved后再次出现 → recurrence_count+1
recurrence_count≥3 → chronic_tension
  → "这个张力反复出现，可能不是执行力问题，可能是更深层价值观冲突。
     是否进入深度探索模式？"
```

#### 复杂度硬上限

`[v2迭代]`

```yaml
tension_budget:
  active_tensions_hard_cap: 10
  at_cap_behavior: "最旧的未解决张力自动降级为observation"
  healthy_range: "2-4条active"
  # healthy: 2-4条active，覆盖不同tier
  # too_low: 0-1条 → "规范性原则可能需要升级"
  # too_high: 5+条 → "标准太多不现实，建议优先处理top 2"
  # chronic: ≥2条recurrence≥3 → "深层价值观冲突需解决"
```

#### 边界条件

`[v1保留]`

| 场景 | 处理 |
|------|------|
| 新原则刚创建没数据 | 不检测。min_sample未达到前静默 |
| 用户连续dismiss多条 | 不评判。月报呈现"本月dismiss了5条"作为元数据 |
| 所有张力都是同一条PP | 该PP本身可能有问题，建议深度探索审视 |
| 报告太频繁 | cooldown保护+severity分级（mild不推，moderate周报呈现，significant+即时） |
| 描述性原则还是emerging | 不与PP做张力对比，只有confirmed的DP才进入 |
| 特殊期（搬家/考试周） | 系统自动检测低功耗态，不推送张力报告 |



---

### Layer 5: 决策辅助层（Decision Aid）

**定位：** ★核心价值层。系统存在的最核心理由——用户描述决策场景后，调用原则+假说+历史类比，生成正面论证+对手盘+盲区提醒+收敛问题。不做结论，用户裁决。

Layer 5是唯一要在**决策发生之前**实时工作的模块。约束组合最极端：时间压力、多原则整合、不能给结论、要给对手盘。

#### 决策前直觉捕获

`[v2迭代]`

```yaml
pre_analysis_capture:
  trigger: "用户发起L5决策咨询时，系统呈现分析之前"
  question: "在你看系统分析之前——你现在倾向哪个选项？信心多大(1-10)？"
  fields:
    pre_lean: "选项X"
    pre_confidence: 7
  purpose:
    - "建立反事实基准（没有系统你会怎么选）"
    - "捕获直觉vs理性的真实张力"
    - "为系统价值追踪提供数据（见第十一章可证伪性设计）"
```

#### 推理引擎四阶段架构

`[v1保留]`

```
用户输入场景 → Phase 1:场景解构 → Phase 2:原则召回 → Phase 3:论证合成 → Phase 4:盲区扫描
```

#### Phase 1: 场景解构

`[v1保留]`

```yaml
scene_decomposition:
  consultation_id: "C-012"
  raw_input: "用户原始描述"

  choice_structure:
    type: "binary|multi_option|spectrum|meta_decision"
    options:
      - id: "opt_A"
        description: "选项描述"
        implied_tradeoffs: ["放弃什么", "获得什么"]

  dimensions_involved:
    - dimension: "AX-001"
      relevance: "high"

  constraints:
    time_pressure: "high|medium|low|none"
    reversibility: "high|medium|low"
    stakes: "trivial|low|medium|high|critical"
    information_completeness: "sufficient|partial|severely_lacking"

  time_horizon:
    primary: "immediate|days|weeks|months|years"
    secondary_effects: []
    horizon_conflicts:
      - short_term_favors: "opt_A"
        long_term_favors: "opt_B"
        crossover_point: "描述"
```

**时间尺度升维机制：**

`[v1保留]`

当系统检测到你在短时间内反复就同一类微决策来咨询时，系统提示：

> "你问的是今晚要不要干，但过去3天你每晚都在做这个决策。也许你真正需要决定的是：这周/这个月的工作节奏标准是什么？"
> [继续当前决策] [切换到策略级讨论]

系统不强制升维，只指出可能性。

#### Phase 2: 原则召回——三层漏斗

`[v1保留]`

```
Layer 1 粗筛：维度匹配+trigger语义匹配 → 候选集（15-20条）
Layer 2 排序：relevance_score = 维度匹配×0.3 + trigger匹配×0.3 + tier×0.2 + validation×0.1 + recency×0.1
Layer 3 对抗性筛选：
  → top N中如果全指向同一选项 → 强制拉入反方向原则
  → 没有反方向原则 → 从试金石库未验证假说中搜索
  → 连假说都没有 → 标记"原则体系在该方向有盲区"
  → 输出：正方原则集 + 反方原则集
```

同时召回：相关假说（低权重参考）、历史类比（决策日志）、活跃张力（盲区提醒）、退役原则（幽灵提醒）。

#### Phase 3: 论证合成（论证链合成）

`[v1保留]`

把多条原则串成推理链，每一步标注依赖哪条原则+confidence。

```yaml
argument_synthesis:
  pro_argument:
    conclusion: "倾向选项A"
    reasoning_chain:
      - step: 1
        claim: "当前经济满足生存安全线"
        grounded_in: "PP-003.decision_rule.step_1"
        evidence: "现金储备=4.2个月"
        confidence: "high"
      - step: 2
        claim: "生存条件满足→默认选长期积累"
        grounded_in: "PP-003.statement"
        confidence: "high"
      - step: 3
        claim: "选项A的长期属性更强"
        grounded_in: "场景分析"
        confidence: "medium"
    overall_confidence: "medium-high"
    weakest_link: "Step 3——复利判断是判断而非事实"

  contra_argument:
    conclusion: "为什么可能应该选B"
    reasoning_chain:
      - step: 1
        claim: "PP-003前提'方向有复利效应'——你没有该领域先例数据"
        grounded_in: "PP-003.key_assumptions[1]"
        confidence: "medium"
      - step: 2
        claim: "PP-008说可逆决策快执行——B可逆性高"
        grounded_in: "PP-008"
        confidence: "high"
      - step: 3
        claim: "历史D-028：同样'选长期'但方向错误导致3月浪费"
        grounded_in: "D-028.outcome=negative"
        confidence: "medium"
    strongest_point: "方向不确定时可逆性权重应上升"
```

**论证链合成算法：**
1. 识别锚点（tier最高+validation最强）
2. 从锚点的decision_rule逐步检查前提满足
3. 满足的前提=支撑点，不满足/不确定的=攻击点（给反方）
4. 连接支撑原则扩展正面链
5. 反方锚点挑战正方weakest_link + 补充历史反例
6. 每步标注confidence+grounded_in

#### Phase 4: 盲区扫描

`[v1保留]`

```yaml
blind_spot_scan:
  missing_dimensions:
    - dimension: "relationship_impact"
      note: "未提到对伴侣影响"
  cognitive_bias_alerts:
    - bias: "sunk_cost"
      trigger: "你提到'已经投了2周'"
  information_gaps:
    - gap: "A的复利机制未具体描述"
  active_tension_reminder:
    - tension_id: "TEN-017"
      relevance: "你正在用PP-007但偏离率80%"
  retired_principle_ghost:
    - "你曾有'项目开始不轻易放弃'原则，因D-028退役"
  pre_mortem_analysis:
    - "假设选了A且3个月后失败，最可能的3个原因：①方向判断依据不足 ②执行力不够 ③市场环境变化"
    - trigger_condition: "stakes≥high时启动"
```

#### Quick_test设计标准

`[v1保留]`

好的quick_test满足三条件：
1. **一个问题**（不是三步判断）
2. **答案是binary的**（是/否）
3. **调用情绪直觉而非理性分析**（压力下理性带宽不够）

示例：
- ✓ "如果最尊敬的人站旁边看你做决定，你还选这个吗？"
- ✓ "选了短期收入，3个月后的你会骂现在的你吗？"
- ✗ "评估一下长期NPV" → 压力下算不了

**本质：把复杂推理压缩成5秒内回答的情绪探针。不需要"正确"，只需要把你从自动驾驶中拽出来一秒。**

#### 决策后闭环

`[v2迭代]`

```
决定后 → 写入L0 → 标记：
  - 调用了哪些原则
  - 是否遵循正面论证
  - pre_lean vs final_choice是否一致
  - 如果改变了选择→记录change_reason（反事实追踪数据）
→ 设置回填（按stakes分级）
→ 如果选了对手盘方向→特殊标记against_primary_recommendation（原则可能需要修正的信号）
→ L4获得新数据 → L6记录事件
```

#### L5架构预留升级

`[v2迭代]`

当前版本：单线程线性推理。

未来升级方向（不在v2.0实施，待实际验证后启用）：

```
并行推理+讨论综合架构：
  并行阶段：视角A(原则出发) / 视角B(历史类比) / 视角C(反方) / 视角D(假说)
  讨论阶段：综合ABCD → 找共识/分歧/盲区 → 合成最终论证
  启用条件：系统运行3个月后，如果L5论证质量不够好（尤其对手盘太弱）
```

#### 边界条件

`[v1保留]`

| 场景 | 处理 |
|------|------|
| 原则库<10条 | 降级：只做列举+历史类比+盲区扫描 |
| 场景太模糊 | 不硬解构，反问："能描述为'A还是B'吗？否则可能需要深度探索模式" |
| 所有原则指同一方向 | 明确告知"体系一致≠一定正确"，对手盘从假说和反例中构建 |
| 用户情绪明显不稳 | 优先触发PP-007："建议延后24小时" |
| 时间极紧（5分钟内要回复） | 极简模式：锚点原则+quick_test+最大风险点 |



---

### Layer 6: 演化追踪层（Evolution Tracker）

**定位：** ★核心价值层。记录原则生命周期、认知变化轨迹。月度/季度报告"你变了什么"。预测你可能即将修正哪些原则。你用其他方式完全做不到的长期认知轨迹追踪。

不是"历史记录"——是"操作系统的git history + 趋势预测 + 身份内核检测"。

`[v1保留]`

三大功能模块：
- **模块A 演化叙事引擎**："你变了什么"——把变化事件串成有因果关系的叙事
- **模块B 趋势预测引擎**："你即将变什么"——在原则被正式修改前发现征兆
- **模块C 身份内核检测器**："什么没变"——在所有变化中锚定"你是谁"的不变内核

#### 核心数据单位：演化事件

`[v1保留]`

```yaml
evolution_event:
  id: "EV-089"
  timestamp: "时间戳"
  event_type: "principle_created|principle_updated|principle_retired|
               principle_promoted|tension_detected|tension_resolved|
               pattern_emerged|pattern_dissolved|phase_shift|
               hypothesis_promoted|hypothesis_retired|
               meta_principle_modified|validation_reversal|system_upgrade"
  subject:
    type: "principle|pattern|hypothesis|tension|system"
    id: "PP-003"
    before_state: "变化前快照"
    after_state: "变化后快照"
    delta_summary: "一句话描述"
  cause:
    type: "evidence_accumulation|single_critical_event|user_reflection|
           external_life_change|gradual_drift|conflict_resolution"
    triggering_decisions: ["D-045"]
    description: "描述"
  significance:
    level: "minor|moderate|major|transformative"
    affects_tier: 3
    cascade_effects: []
  meta_cognition:
    change_direction: "growth|regression|lateral_shift|deepening|simplification"
    user_confirmed_direction: null
```

#### 模块A：演化叙事引擎

`[v1保留]`

不是事件日志——是**叙事**。把事件串成"你曾经认为X→因为Y发生了→你修正为Z"的故事。

叙事生成逻辑：事件聚类→因果链重建→叙事合成→意义标注

意义标注类型：
- progressive_deepening（渐进深化）
- oscillation（摇摆）
- paradigm_shift（范式转变）
- gradual_erosion（渐进侵蚀）
- sudden_crystallization（突然结晶）

#### 模块B：趋势预测引擎

`[v1保留]`

在原则被正式修改前发现征兆。6种预测信号：

| 信号 | 检测方式 | 预测含义 |
|------|---------|---------|
| 偏离加速 | 连续3周期deviation_rate上升 | PP可能即将修订/退役 |
| 反例聚集 | 30天负向比例突升 | PP前提可能正在失效 |
| 使用衰减 | 90天触发下降>50% | 可能已隐含放弃 |
| 替代行为涌现 | 新模式与某PP重叠但方向不同 | 新DP正在取代旧PP |
| 假说反超 | 某假说验证分数超过同域PP | 假说可能比现行原则更可靠 |
| 元原则松动 | 某MP下多条PP同时张力/偏离 | MP本身需重新审视 |

价值：把"原则开始过时→你终于修改"的认知滞后从3-6个月压缩到2-4周。

#### 模块C：身份内核检测器

`[v1保留]`

操作定义：身份内核 = 从未修改核心逻辑的原则 + 从未偏离的规范性原则 + 无论条件如何变化都一致的行为倾向。**不是你"声称"不变的，是数据证明确实没变的。**

```yaml
identity_core:
  stable_principles:
    - id: "MP-001"
      stable_since: "2026-05-20"
      stability_days: 480
      assessment: "deep_conviction"
  stable_patterns:
    - description: "偏向帮助他人"
      assessment: "identity_trait"
  stable_values:
    - statement: "体验多样性>物质积累"
      assessment: "core_value"
  core_health:
    total_stable_elements: 8
    assessment: "healthy"
    # healthy: 5-15条 | too_rigid: >20条 | too_fluid: <3条
```

**内核警报（最高优先级）：** 当稳定480天的元素突然出现偏离——不是普通张力，是地基松动。系统呈现两种可能："极端期例外（需设退出条件）" vs "被外部压力无意识侵蚀（需立即干预）"。

#### "成长vs漂移"区分

`[v1保留]`

| 维度 | 成长特征 | 漂移特征 |
|------|---------|---------|
| 驱动力 | 有明确触发事件 | "不知道什么时候开始的" |
| 方向性 | 精确化或深化 | 模糊化或放弃 |
| 意识度 | 你知道自己变了且能解释 | 系统指出后才发现 |
| 一致性 | 与内核不冲突 | 与内核产生新张力 |

#### 系统季度自我暴错

`[v2迭代]`

```yaml
quarterly_self_challenge:
  task: "找出系统分析倾向A但用户选B且结果正向的案例"
  presentation: |
    本季度你有X次违背了系统的主要论证方向，其中Y次结果更好。
    系统在以下场景下判断力不如你的直觉：[...]
    请记住：系统不比你聪明，它只是更有结构。
  purpose: "主动去权威化，防止用户过度依赖系统"
```

#### 系统权威监控器

`[v2迭代]`

```yaml
system_authority_monitor:
  metric: "过去30天中，用户选择了系统主要论证方向的比例"
  healthy_range: "60%-80%"
  alert_threshold: ">85%持续60天"
  alert_message: |
    过去两个月你有87%的决策选择了系统正面论证的方向。
    这可能意味着系统分析得很好。
    也可能意味着你在不自觉地依赖系统代替独立思考。
    建议：下一个重大决策时，先自己想清楚方向，然后再看系统分析。
```

#### 随机静默期

`[v2迭代]`

```yaml
silence_period:
  frequency: "每2-3个月一次"
  duration: "5-7天"
  behavior: "L5不可用，无Briefing推送，用户纯靠直觉"
  post_silence: "对比静默期决策质量与有系统时的质量"
  purpose: "防止系统从工具变为依赖"
```

#### 报告体系

`[v1保留]`

**月度报告：**
- 数据统计
- 最重要变化
- 趋势预测
- 内核确认

**季度报告：**
- 月度内容 +
- 跨领域模式
- 结构性变化
- 3月前对比
- 退役回顾
- 系统自我暴错报告 `[v2迭代]`

**年度报告：**
- 季度内容 +
- 认知演化路径可视化（阶段划分）
- 最大转变
- 内核年审
- 反思问题



---

## 六、维度体系设计

**定位：** 维度是系统的"语义路由表"——决定哪些决策被认为是"同一类"。服务于Layer 0（决策分类）、Layer 2（模式聚类）、Layer 5（原则召回）。

### 三层结构

`[v1保留]`

```
第一层：维度域（Domain）— 预设≤10个 — 最粗归类，几乎不变
  例：时间分配/金钱资源/关系社交/职业方向/学习成长/健康生存/创作表达/决策方法论

第二层：维度轴（Axis）— 半涌现 — Domain内的具体张力轴
  例（时间分配域内）：深度vs碎片 / 当前任务vs新机会 / 为自己vs为他人 / 休息vs产出

第三层：情境标签（Context Tag）— 完全涌现 — 不标准化，只用于检索匹配不用于分析
  例："兼职""外包""加班""周末学习"
```

**聚类和模式发现只用第一层和第二层。第三层只用于检索。** 防止"情境标签太多导致每条决策独一无二"。

### 维度轴涌现机制

`[v1保留]`

触发条件：某Domain内≥8条决策 + ≥4条的stated_reason出现相似权衡逻辑 + 该逻辑不匹配已有Axis + 选择方向不一致

→ 系统推出候选Axis → 用户确认 → 正式加入 → 回溯重标记

### 语义匹配机制

`[v1保留]`

**不依赖关键词匹配，依赖"选择结构"匹配。**

两条决策"同一维度"的判定标准：面对的权衡结构相似（[放弃什么类型价值, 获得什么类型价值]）。

双通道匹配：
- 通道1（高权重）：结构匹配——提取implied_tradeoffs → 抽象类型 → 匹配Axis
- 通道2（辅助）：语义相似度验证
- 最终：双通道交叉验证

### 去重与合并

`[v1保留]`

合并条件：决策集合重叠>70% + 方向高度一致 + 用户确认
合并执行：创建新Axis → 旧两条标记"已合并" → 历史重标记 → 模式引擎重跑

### 复杂度硬上限

`[v2迭代]`

```yaml
axis_budget:
  active_axes_hard_cap: 25
  at_cap_behavior: "触发合并扫描"
  merge_condition: "决策集合重叠>70% + 方向高度一致"
```

### 冷启动

`[v1保留]`

- 前10天：预设3-5个Domain + 每个1-2个种子Axis + 先标Domain待积累
- 第11-20天：Domain内5+条决策 → 尝试Axis匹配
- 第21-30天：第一批涌现Axis可能出现

---

## 七、交互设计

### 7.1 交互场景

`[v2迭代]`

| # | 场景 | 触发方 | 频率 |
|---|------|--------|------|
| 1 | 捕获(Capture) | 用户 | 随时（想到就说） |
| 2 | 咨询(Consult) | 用户 | 重大决策时 |
| 3 | 每日Briefing | 系统 | 固定时间，有内容才推 |
| 4 | 复盘回填(Review) | 系统提醒 | 按stakes分级的时间点 |
| 5 | 深度探索(Explore) | 用户 | 按需 |
| 6 | 信任圈·日常沉淀 | 用户事后 | 线下交流后 |
| 7 | 信任圈·Lifeline | 用户(极稀有) | 每人每年1-2次 |
| 8 | 月度Sync | 系统+用户 | 每月一次15分钟 |

### 7.2 场景一：捕获（Capture）

`[v2迭代]`

**触发：** 快捷键/全局热键，从触发到输入<2秒
**输入：** 语音或文字，无格式要求
**系统处理：** 分类→结构化→关联→**默认生效写入**
**校准期毕业后：** 不再呈现确认界面。低confidence的字段汇入Briefing等你有空时看。

### 7.3 场景二：咨询（Consult）

`[v1保留 + v2迭代]`

**触发：** 主动切换到咨询模式（不同于捕获入口）
**输入：** 描述决策场景，不限长度
**v2新增：** 系统呈现分析前先捕获直觉倾向（pre_analysis_capture）
**系统处理四阶段：** 场景解构→原则召回→论证合成→盲区扫描
**输出结构：**

```
🎯 决策咨询 #C-XXX
📋 场景解析：[核心选择/维度/时间压力/可逆程度/时间尺度]
⚖️ 正面论证：[推理链+每步依据+confidence+weakest_link]
🥊 对手盘：[反面推理链+strongest_point]（同样来自你的原则体系）
🔲 盲区扫描：[缺失维度/认知偏误/信息缺口/活跃张力/退役原则幽灵/预设验尸]
❓ 收敛问题：[帮你思考的问题，系统不做结论]
📎 历史类比：[过去类似情况你怎么选，结果如何]
⚡ Quick Test：[5秒情绪探针]
→ 你的决定是？
```

**决定后：** 记录为决策日志 + 标记pre_lean vs final_choice + 设置回填提醒

### 7.4 场景三：每日Briefing

`[v2迭代]`

**核心原则：没有重要信息的日子=不推送=最好的日子。**

| 优先级 | 内容类型 | 出现条件 |
|--------|---------|---------|
| 1 | 系统自我修改通知 | 系统改了自己的规则时 |
| 2 | 需要你输入的卡点 | 解析confidence<0.5的记录 |
| 3 | 发现/趋势摘要 | 有新emerging模式或显著趋势 |
| 4 | 即将到期的回填 | 回填点前1天 |
| 5 | 系统健康异常 | 指标超阈值 |

**约束：**
- 总条数≤5
- 每条一句话+可展开详情
- 总阅读时间<2分钟
- 无重要信息的日子=不推送

### 7.5 场景四：复盘回填（Review）

`[v1保留 + v2迭代]`

**触发：** 系统提醒（按stakes分级的预设时间点）+ 用户主动
**输入：** 描述结果
**输出：** 结构化记录 + 标记验证/挑战了哪些假说和原则 + 设置下次追踪

**v2迭代：** 高stakes决策的前两次回填只允许记录感受和客观变化，不开放正向/负向判断。每次正向回填强制追问"有没有任何小的负面后果"。

### 7.6 场景五：深度探索（Explore）

`[v1保留]`

多轮开放对话。系统主动追问、挑战、拓展。用于梳理领域脉络、探讨未成型想法、挑战假设、发现漏洞。

### 7.7 月度Sync Ritual

`[v2迭代]`

**15分钟，固定时间：**

1. **系统健康一览**（2min）：核心指标 + 系统本月自动做了什么
2. **3条随机抽检**（5min）：系统随机呈现3条它自动处理的记录，你10秒扫一眼确认质量
3. **本月重大变更汇总**（5min）：系统升级了什么 / 新模式 / 新张力
4. **内核确认**（3min）：不变的内核→你确认

### 7.8 交互设计底层哲学

`[v2迭代]`

| 原则 | 含义 |
|------|------|
| 零摩擦捕获 | 想到→记录，无思考负担 |
| 默认生效 | 系统输出不等确认，你改随时改 |
| 永远透明 | 系统每个判断都可追问"为什么" |
| 你做决定 | 系统只呈现正反+你裁决 |
| 安静优先 | 没重要事不推送，稳定期完全沉默 |
| 对手盘思维 | 重要决策必有反面论证 |
| 脉冲式 | 系统活跃度随你的决策密度同步 |

---

## 八、信任圈机制

### 8.1 核心设计原则

`[v1保留]`

**对方不需要碰你的系统，不需要知道系统存在。** 你和对方正常线下交流 → 你事后把关键信息录入 → 系统结构化外部视角。

### 8.2 两种机制

`[v1保留]`

| 机制 | 触发 | 对方感受 | 频率 |
|------|------|---------|------|
| 日常沉淀 | 任何线下交流后你事后录入 | 无感知 | 随时 |
| Lifeline | 重大决策+系统门槛通过 | 受宠若惊(被信任) | 极稀有,每人≤1-2次/年 |

### 8.3 日常沉淀

`[v1保留]`

场景：聊完回家，按快捷键录入对方观点。
系统处理：结构化→关联决策→标记来源。
对方负担：零。

伴侣特殊：不走Lifeline（日常共同决策关系），面对面讨论后录入，可标记"联合决策"，系统记录未解决的情绪信号。

### 8.4 Lifeline机制

`[v1保留]`

**稀缺性保护门槛（系统评估）：**
- 决策影响时间跨度≥1年？
- 不可逆程度：高？
- 上次向此人发起Lifeline：多久前？
- 已独立思考超过7天？

全部通过→允许。不通过→建议不使用+原因+强制使用选项。

**系统帮你做的：** 生成精炼提问结构（背景/选项/你的思考/真正想问的），目标让对方5分钟理解+知道你认真想过+有锚点回答。

**回复处理：** 录入系统→结构化→关联原则/假说→记录Lifeline价值评估（决策后回填）。

### 8.5 数据结构口子预留

`[v1保留]`

在数据层预留未来协作升级空间（现在交互100%你一人操作）：
- 决策记录:`external_perspectives`字段
- 联合决策:`participants`字段
- 原则库:`challenged_by`字段



---

## 九、系统健康与可读性

### 9.1 三层视图

`[v1保留]`

- **Dashboard**：10秒概览——system_health + top_attention(≤3) + core_anchor
- **Map**：结构化全景——原则地图（每个MP下的子原则状态/张力/活跃度）
- **Detail**：按需钻入任何节点的完整数据

### 9.2 可解释性追踪链

`[v1保留]`

系统每个输出都附带完整reasoning_steps，用户可逐步追问"为什么"直到满意。用户可在任何step上override（系统从该步重新推理）。

### 9.3 确认度标记

`[v1保留]`

每条信息标记：
- system_inferred（系统推断）
- user_glanced（用户扫过）
- user_confirmed（用户确认）
- user_deeply_reviewed（用户深度审视）

新鲜度：fresh / aging / stale

### 9.4 Override Protocol

`[v1保留]`

你可以覆盖系统任何判断，系统不反驳不追问。但连续覆盖同类>5次→轻声问一次"要不要调整系统逻辑？"→然后不再问。

### 9.5 过程指标（系统健康仪表盘）

`[v2迭代]`

系统持续自监控：

```yaml
system_health_metrics:
  parsing_accuracy:
    metric: "最近30条中用户修正比例"
    threshold: ">20% → 系统降级为需确认模式"
  pattern_false_positive:
    metric: "系统提出的模式用户拒绝比例"
    threshold: ">40% → 提高emerging门槛"
  tension_signal_noise:
    metric: "张力报告中用户标记'误检'的比例"
    threshold: ">30% → 调低敏感度"
  system_authority_follow_rate:
    metric: "用户选择系统主要论证方向的比例"
    healthy_range: "60%-80%"
    alert: ">85%持续60天 → 依赖度警报"
```

### 9.6 复杂度总预算

`[v2迭代]`

```yaml
complexity_budget_summary:
  active_principles: {hard_cap: 40}
  active_hypotheses: {hard_cap: 100}
  active_tensions: {hard_cap: 10}
  active_axes: {hard_cap: 25}
  daily_briefing: {max_items: 5}
  monthly_sync: {max_duration: "15min"}
  
  compression_cycles:
    decision_log: "每90天压缩"
    association_pruning: "每180天扫描"
    principle_merge_scan: "每季度"
```

### 9.7 关联剪枝

`[v2迭代]`

```yaml
association_pruning:
  scan_cycle: "每180天"
  dormant_condition: "该关联180天内未被任何层引用 + 两端节点无活跃张力"
  dormant_to_delete: "再过180天仍为dormant → 删除"
  purpose: "防止关联网络指数膨胀"
```

---

## 十、系统自主学习机制

**定位：** 系统从外部信息源中提取"元层面"知识以优化自身运行逻辑——与用户提取"内容层面"假说形成双管线并行。

### 10.1 双管线模型

`[v1保留]`

你看信息源提取"对我决策有什么用"（内容层面）→产出假说。
系统看同一信息源提取"这个思考框架能不能优化我的运行逻辑"（元层面）→产出系统更新提案。

同一输入源，两条完全不同的处理管线。

### 10.2 系统关注的五类知识

`[v1保留]`

| 类型 | 找什么 | 示例 |
|------|--------|------|
| 思维框架 | 改进模式识别/推理逻辑 | OODA循环、贝叶斯更新 |
| 决策方法论 | 升级L5推理引擎 | 预设验尸法、10/10/10法则 |
| 认知偏误研究 | 加入盲区扫描 | 新发现的偏误和去偏方法 |
| 系统设计模式 | 优化架构本身 | 反脆弱设计、渐进复杂度管理 |
| 前沿研究 | 决策科学新发现 | 特定条件下某策略更优的实证 |

### 10.3 系统更新提案

`[v1保留]`

```yaml
system_update_proposal:
  id: "SU-014"
  source: {input_id, person, platform, content}
  discovery:
    type: "decision_methodology|cognitive_bias|thinking_framework|system_design|frontier_research"
    summary: "一句话发现"
  proposal:
    target_layer: "L5"
    target_component: "blind_spot_scan"
    current_state: "当前状态"
    proposed_change: "变更方案"
    change_type: "addition|modification|replacement|removal"
  reasoning:
    why_this_matters: "为什么重要"
    expected_benefit: "预期收益"
    potential_risk: "潜在风险"
    risk_mitigation: "风险缓解"
  impact:
    scope: "minor|moderate|major|structural"
    backward_compatible: true/false
  approval:
    status: "pending|approved|rejected|deferred|partially_approved"
```

### 10.4 审批机制

`[v2迭代]`

按scope分级自动处理，不再逐条需要用户审批：

```yaml
approval_by_scope:
  minor: "默认试运行14天，月度Sync时汇报结果"
  moderate: "默认试运行14天，月度Sync时决定保留或回滚"
  major: "推送审批，用户明确批准才执行"
  structural: "推送审批 + 详细论证 + 必须批准"
```

### 10.5 边界控制

`[v1保留]`

```yaml
auto_learning_constraints:
  max_proposals_per_week: 3
  max_pending_updates: 5
  max_monthly_approved: 4
  post_update_observation: 14天
  all_updates_reversible: true
```

### 10.6 必须告知用户的底线

`[v2迭代]`

**无论scope大小，系统修改了自己的规则后，必须在下次Briefing中告知用户：**
- 改了什么
- 为什么改
- 对你使用方式有什么影响
- 怎么回滚

### 10.7 系统Changelog

`[v1保留]`

每条更新记入版本历史。5年后可看到"系统本身从v1.0到v15.0的方法论演化史"。

---

## 十一、系统可证伪性设计

`[v2迭代]`

### 11.1 反事实追踪

```yaml
counterfactual_tracking:
  trigger: "每次L5咨询"
  capture:
    pre_analysis_lean: "用户分析前的倾向"
    pre_analysis_confidence: "信心度1-10"
    post_analysis_choice: "最终选择"
    change_occurred: true/false
    change_reason: "如果改变了，什么说服了你"
  
  annual_summary:
    total_consultations: N
    unchanged_choice: X  # 系统价值=确认
    changed_choice: Y    # 系统有增量影响
    changed_positive: Z  # 改变且结果好
    changed_negative: W  # 改变且结果差
    net_value: "Z - W"   # 系统净正贡献
```

### 11.2 静默期对照

```yaml
silence_period_validation:
  frequency: "每2-3个月一次，5-7天"
  behavior: "L5不可用，无Briefing，用户纯靠直觉"
  post_silence_analysis: "回溯对比静默期决策质量与有系统时的质量"
  two_possible_results:
    quality_dropped: "系统确实在帮你 → 继续使用有信心"
    quality_unchanged: "系统可能只是安慰感 → 重要信号"
```

### 11.3 各层可证伪声明

| 系统层 | 核心声明 | 无用判定条件 |
|--------|---------|-------------|
| L2模式引擎 | 发现用户盲区 | 12个月内用户对模式反应全是"我知道" |
| L4张力检测 | 促使行为/原则修正 | 6个月内零次修正触发 |
| L5决策辅助 | 改善决策质量 | 反事实追踪净正贡献=0 |
| L6演化追踪 | 帮助理解变化方向 | 报告未导致任何认知或行动改变 |
| L1试金石库 | 假说被有效调用 | 年度被L5调用且影响决策的<5条 |

### 11.4 Kill Switch

```yaml
system_kill_switch:
  core_claim: "本系统帮助用户做出更好的决策"
  
  conditions_any_2_met:  # 任意2条满足→系统主动建议关闭
    - "连续12个月L5改变选择且结果正向=0"
    - "连续12个月张力报告导致修正=0"
    - "静默期对照显示无质量差异，连续2次"
    - "用户月度输入连续6个月<3条"
  
  action: |
    根据过去12个月数据，本系统没有为你的决策带来可测量的改善。
    建议：
    ① 关闭系统，把时间用在别处
    ② 大幅简化，只保留确认有用的层
    ③ 继续运行但降低投入到接近零
    你的选择？
```

---

## 十二、冷启动计划

### Phase 1: 纯记录期（第1-10天）——校准期开始

`[v1保留 + v2迭代]`

- 每天记录决策（大小不限，有就记没有不强求）
- 格式极简：场景/选项/选择/理由
- 同时试金石库开始运行（正常看信息源，有感觉的扔进去）
- 系统不输出任何分析
- 维度体系：预设3-5个Domain + 每个1-2个种子Axis + 先标Domain待积累
- **每条记录需要确认**（校准系统理解力）

### Phase 2: 模式识别期（第11-20天）

`[v1保留 + v2迭代]`

- 系统对前10天记录跑第一轮分析
- 检测：倾向性？情绪-决策关联？理由中的重复逻辑？
- 双通道交叉验证开始 `[v2迭代]`
- 试金石库假说开始与决策做关联匹配
- 可能产生第一个emerging模式
- 维度体系：Domain内5+条决策 → 尝试Axis匹配
- **确认行为开始逐项毕业** `[v2迭代]`

### Phase 3: 初步涌现期（第21-30天）

`[v1保留 + v2迭代]`

- 系统输出第一批描述性原则（3-5条）
- 呈现完整分布（含反例）让你判断 `[v2迭代]`
- 认可→确认为描述性原则
- 不认可→产生张力→系统开始帮你成长
- 维度体系：第一批涌现Axis可能出现
- **大部分确认行为应已毕业→进入巡航态** `[v2迭代]`

### Phase 4: 巡航态确认（第31-60天）

`[v2迭代]`

- 验证系统默认处理的质量
- 月度Sync第一次执行
- 过程指标建立基线
- **所有确认行为毕业→正式进入cruise_mode**

---

## 十三、设计决策记录（Design Decision Log）

| 决策点 | 最终选择 | 否决方案 | 原因 |
|--------|---------|---------|------|
| 冷启动策略 `[v1保留]` | 先记录30天再涌现原则 | 从信息源直接提炼原则 | 别人的原则未经你验证不是你的原则 |
| 信息源定位 `[v1保留]` | 待验证假说(Touchstone) | 直接作为原则来源 | 防止确认偏误引擎 |
| 决策辅助输出 `[v1保留]` | 对手盘(正反两面) | 给出确定结论 | 确认偏误风险/决策质量>速度 |
| 信任圈交互 `[v1保留]` | 你事后录入,对方无感知 | 对方在系统中操作 | 对方无动机/浪费他人时间 |
| Lifeline设计 `[v1保留]` | 极稀有+系统门槛保护 | 随时可问 | 稀缺性=社交价值/"受宠若惊"效应 |
| 原则类型 `[v1保留]` | 描述性+规范性+张力 | 单一类型 | 张力才是成长引擎 |
| 模式引擎输出 `[v1保留]` | 需用户确认才生效 | 系统自动生成原则 | 防止误检/保持用户操控感 |
| 张力定义 `[v1保留]` | 行为累积偏离(非逻辑矛盾) | 原则文本对比 | 文本矛盾≠实际张力 |
| 论证合成 `[v1保留]` | 推理链合成(非列举) | 列举每条原则观点 | 列举式用户还得自己整合 |
| 维度匹配 `[v1保留]` | 选择结构匹配(非关键词) | 关键词匹配 | 关键词无法抓住本质权衡 |
| 情境衰减模型 `[v1保留]` | 情境相变跳转 | 线性时间衰减 | 时间本身不影响有效性,情境变化才影响 |
| 系统学习 `[v1保留]` | 双管线(内容+元) | 单管线只提取假说 | 系统本身也需要演化 |
| 确认机制 `[v2迭代]` | 默认生效+毕业条件 | 每条确认才生效 | 认知负荷诚实性——系统不应是需要你打理的公司 |
| 复杂度管理 `[v2迭代]` | 硬上限+强制遗忘+周期性压缩 | 软建议 | 防止复杂度自催化膨胀，遗忘是学习的另一半 |
| 运行节奏 `[v2迭代]` | 脉冲式自动切换 | 固定频率 | 匹配人生决策密度，稳定期完全安静 |
| 系统价值验证 `[v2迭代]` | Kill Switch+反事实追踪 | 无验证机制 | 可证伪性=对用户诚实 |
| 权力关系 `[v2迭代]` | 主动去权威化(季度暴错+静默期+框架轮换) | 仅被动Override | 防止了解变束缚，系统不应成为你的法官 |
| 模式检测 `[v2迭代]` | 双通道（理由+行为结构） | 单通道（仅理由） | 防事后合理化污染，行为通道发现无意识真实倾向 |
| 系统终极目标 `[v2迭代]` | 让你不再需要系统 | 永续使用 | 工具不是信仰，系统的成功是让你内化决策智慧 |

---

*文档结束。Personal Principle OS v2.0 全层设计完成。*
