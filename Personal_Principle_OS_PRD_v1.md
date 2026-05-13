# Personal Principle OS — 产品设计文档 (PRD)

> 版本: v1.0 | 日期: 2026-05-13 | 状态: 全层设计完成

---

## 目录

1. [系统定义](#一系统定义)
2. [设计哲学](#二设计哲学5条核心设计原则)
3. [系统架构](#三系统架构)
4. [各层详细设计](#四各层详细设计)
   - [Layer 0: 决策日志](#layer-0-决策日志decision-log)
   - [Layer 1: 试金石库](#layer-1-试金石库touchstone-library)
   - [Layer 2: 模式识别引擎](#layer-2-模式识别引擎pattern-engine)
   - [Layer 3: 原则层](#layer-3-原则层principle-layer)
   - [Layer 4: 张力检测器](#layer-4-张力检测器tension-detector)
   - [Layer 5: 决策辅助层](#layer-5-决策辅助层decision-aid)
   - [Layer 6: 演化追踪层](#layer-6-演化追踪层evolution-tracker)
5. [维度体系设计](#五维度体系设计)
6. [交互设计](#六交互设计)
7. [信任圈机制](#七信任圈机制)
8. [系统可读性设计](#八系统可读性设计)
9. [系统自主学习机制](#九系统自主学习机制)
10. [冷启动计划](#十冷启动计划30天)
11. [待深化问题清单](#十一待深化问题清单)
12. [设计决策记录](#十二设计决策记录design-decision-log)

---

## 一、系统定义

Personal Principle OS 是一个**个人决策操作系统**：从真实决策行为中涌现底层原则，从外部高质量信息源中提取待验证假说，通过持续对比"你实际怎么做"和"你希望怎么做"之间的张力来驱动个人成长，并在每一个需要做判断的时刻提供基于你自己原则体系的双面论证辅助——而非替你做决策。

**它不是：** 知识库、笔记工具、格言收集册、检索式查阅手册。
**它是：** 决策日志 + 假说验证引擎 + 原则涌现机制 + 对手盘决策辅助 + 认知演化追踪器。

---

## 二、设计哲学（5条核心设计原则）

### 2.1 原则从行为中涌现，而非从外部灌入

系统不预设任何原则。第一阶段的核心任务是"无判断地记录真实决策"。原则是从你的决策模式中被系统识别出来的——它们是你"实际在遵循的东西"，可能跟你"想成为的人"完全不同。这个差距才是系统真正工作的地方。

外部信息源的内容不是原则，是"待验证假说"——只有经过你真实决策的检验才能升级为你的原则。

### 2.2 张力是核心价值，而非一致性

系统的核心输出不是"帮你做出正确的决策"，而是**持续暴露你的描述性原则（你实际怎么做）和规范性原则（你希望怎么做）之间的张力**。每一个张力都是一个成长点。系统帮你看见它、理解它、决定是接受它还是缩小它。

### 2.3 对手盘思维，而非确认偏误

系统在每一个重要决策中都主动扮演对手盘。它不告诉你"你应该选A"，而是呈现"基于你的原则体系，正面论证指向A，但反面论证（同样来自你的原则体系）指向B"。最终裁决永远是你做。这是"决策质量提升"，不是"决策速度提升"。

### 2.4 零摩擦输入，即时结构化输出

你负责"说"（语音/文字，无格式要求），系统负责"想"（分类、结构化、关联、反馈）。捕获的那一刻就处理完成——不是"存起来以后整理"。所有系统处理结果透明呈现，你确认/修正后才正式入库。

### 2.5 时间连续性：一切记录都有前因后果

没有任何一条记录是孤立的。每条决策都有回填追踪、每条原则都有生命周期、每条假说都有验证历史。系统保留完整的"原则演化史"——5年后你能看到一条清晰的"认知演化路径"。

---

## 三、系统架构

### 3.1 架构总览图

```
┌─────────────────────────────────────────────────────────┐
│                     用户交互层                            │
│  捕获 | 咨询 | 系统推送 | 复盘回填 | 深度探索 | 信任圈   │
└──────────────────────────┬──────────────────────────────┘
                           │
              ┌────────────┼────────────┐
              ▼                         ▼
┌──────────────────────┐  ┌──────────────────────────┐
│  Layer 0             │  │  Layer 1                  │
│  决策日志            │  │  试金石库                  │
│  (Decision Log)      │  │  (Touchstone Library)     │
│  source: SELF        │  │  source: EXTERNAL         │
└──────────┬───────────┘  └────────────┬─────────────┘
           │                           │
           └─────────────┬─────────────┘
                         ▼
          ┌──────────────────────────────┐
          │  Layer 2                      │
          │  模式识别引擎                  │
          │  (Pattern Engine)             │
          │  输出: 描述性原则              │
          └──────────────┬───────────────┘
                         ▼
          ┌──────────────────────────────┐
          │  Layer 3                      │
          │  原则层                       │
          │  (Principle Layer)            │
          │  描述性 + 规范性 + 已退役     │
          └───────┬──────────┬───────────┘
                  │          │
                  ▼          ▼
┌─────────────────────┐ ┌────────────────────────┐
│  Layer 4            │ │  Layer 5                │
│  张力检测器          │ │  决策辅助层             │
│  (Tension Detector) │ │  (Decision Aid)         │
└─────────────────────┘ └────────────────────────┘
                  │          │
                  └────┬─────┘
                       ▼
          ┌──────────────────────────────┐
          │  Layer 6                      │
          │  演化追踪层                    │
          │  (Evolution Tracker)          │
          └──────────────────────────────┘
```

### 3.2 层间数据流向

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
| L4 → 交互层 | 张力报告推送 |
| 全层 → L6 | 所有变化事件，供演化追踪 |

---



## 四、各层详细设计

### Layer 0: 决策日志（Decision Log）

**定位：** 整个系统的数据地基。你负责输入最少信息，系统负责补全和推断剩余字段。

#### 数据结构

```yaml
decision_log_entry:
  id: "D-037"
  created_at: "ISO时间戳"
  raw_input: "原始语音转文字/直接文字"

  # 系统解析
  scenario: "场景一句话描述"
  options_identified:
    - id: "opt_1"
      description: "选项描述"
  chosen_option: "opt_X"
  stated_reason: "你说出的理由"

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

  # 信任圈外部视角
  external_perspectives:
    - source: "人名"
      type: "casual_conversation|lifeline"
      content: "观点内容"
      recorded_at: "日期"

  # 回填追踪
  outcome:
    status: "pending|positive|negative|neutral|mixed"
    follow_up_dates: ["2026-06-13", "2026-08-13"]
    evaluations:  # 保留所有版本，允许反转
      - recorded_at: "日期"
        assessment: "positive|negative|neutral"
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

#### 维度体系子章节（维度如何在L0中运作）

决策记录中的`decision_dimensions`字段引用维度轴（Axis）ID。维度体系采用三层结构：

```
第一层：维度域（Domain）— 预设≤10个 — 最粗归类，几乎不变
  例：时间分配/金钱资源/关系社交/职业方向/学习成长/健康生存/创作表达/决策方法论

第二层：维度轴（Axis）— 半涌现 — Domain内的具体张力轴
  例（时间分配域内）：深度vs碎片 / 当前任务vs新机会 / 为自己vs为他人 / 休息vs产出

第三层：情境标签（Context Tag）— 完全涌现 — 不标准化，只用于检索匹配不用于分析
  例："兼职""外包""加班""周末学习"
```

**聚类和模式发现只用第一层和第二层。第三层只用于检索。** 防止"情境标签太多导致每条决策独一无二"。

系统在Step 3（维度推断）中自动为新决策匹配维度轴。匹配方式见[第五章 维度体系设计](#五维度体系设计)。

#### 输入处理流水线

```
用户原始输入
  → Step 1: 分类（决策记录 / 信息源触发 / 闪念）
  → Step 2: 结构化提取（场景/选项/选择/理由）
  → Step 3: 维度推断（维度轴匹配/情绪/确信度/量级/可逆度/速度）
  → Step 4: 历史关联（搜索相似决策/相关假说/相关原则）
  → Step 5: 即时反馈生成 → 呈现给用户确认
```

#### 确认后触发动作

| 动作 | 逻辑 |
|------|------|
| 持久化存储 | 写入数据库 |
| 设置回填提醒 | trivial→不设, low→7天, medium→30天, high→30+90天, critical→30+90+180天 |
| 通知Layer 2 | 模式引擎增量扫描 |
| 通知Layer 4 | 张力检测（与规范性原则对比） |

#### 边界条件

| 场景 | 处理方式 |
|------|---------|
| 输入信息不完整 | 不阻断，能提取的提取，标记partial，日报提醒补充 |
| 一天记20条 | 不限制，但系统基于stakes_level加权分析深度 |
| 回填时忘了 | "我已忘了"本身就是信息（影响小的证据） |
| 评价反转 | 保留所有版本，标记evaluation_reversed，提取reversal_insight |

---

### Layer 1: 试金石库（Touchstone Library）

**定位：** 存放外部信息源的观点，格式化为"待验证假说"。不是笔记本——每条内容都有生命周期，最终要么升级为原则，要么被推翻退役。

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

**X（触发）黄金颗粒度：** 每月出现1-3次的场景类型。太粗=等于没触发，太细=验证周期太长。

**Y（行为指引）黄金颗粒度：** 告诉你"做什么类型的选择"而非"做哪个具体选择"。

模板：
- "选择[选项类型A]而非[选项类型B]"
- "在[具体步骤]之后再做决定，而非立即行动"
- "把[资源X]投在[方向类型]而非[方向类型]"

#### 假说层级

| 层级 | 定义 | 验证方式 |
|------|------|---------|
| framework | 框架级，统摄性观点 | 间接验证（通过下层假说） |
| derived | 推导级，从框架推出 | 可直接验证 |
| instance | 实例化，最具体 | 最快验证 |

子假说验证结果向上传递给框架级假说。

#### 自检机制

- **即时自检**：格式化完成后自动TFRF评分。C级以下呈现改进建议但不阻断入库
- **验证失败时回溯**：区分"假说本身错"vs"格式化丢了关键信息"
- **月度库扫描**：D级建议处理 / C级>60天未精炼建议降级 / 来源平均分趋势

#### 输入处理流水线

```
用户输入（"刚看了某某的文章，他说……"）
  → Step 1: 确认是"信息源触发"类型
  → Step 2: 提取原始观点/来源/用户反应
  → Step 3: 假说化（去修辞 → 转为"如果X则Y"可操作结构）
  → Step 4: TFRF质量评分
  → Step 5: 适用边界初步划定（known + uncertain）
  → Step 6: 冲突检测（扫描现有库，标记supports/conflicts）
  → Step 7: 即时反馈呈现 → 用户确认
```

#### 日常运行逻辑（被动触发）

每当Layer 0有新决策记录写入：
1. 新决策的dimensions与所有active假说的trigger_scenarios匹配
2. 匹配度>阈值 → 在决策反馈中提示："相关假说T-089，是否参考了它？"
3. 用户选择"是/否" → 记录为validation_event
4. 后续决策结果好/坏 → 更新validation_score

#### 升级流程（假说→原则）

满足promotion_criteria时：
1. 系统推送升级建议
2. 整合正向+负向验证结果，修正原始表述
3. 生成建议的原则表述（含负向验证带来的边界约束）
4. 用户确认 → 正式升级至Layer 3，status变为promoted

#### 批量导入机制

1. 用户提供原始素材（文稿/文章/课程笔记）
2. 系统"原则密度扫描"——识别所有"有明确立场+有推导逻辑"的观点
3. 每个观点生成候选假说
4. 呈现给用户快速审核：入库 / 不入库 / 跳过 / 修改
5. 去重：相似>80%→合并；更精确→标记精细化关系；冲突→两条都保留标记冲突

#### 库健康度管理（月度报告）

- 状态分布统计
- 陈旧假说（>90天无验证机会）→建议降优先级/调整trigger/退役
- 满足升级条件但未确认的 →提醒
- 高冲突密度的 →建议划定边界
- 来源信任度趋势（某信息源假说验证通过率）

#### 特殊类型处理

- **价值取向声明**："人生的意义在于体验"等不可单次验证的观点 → 标记为value_orientation → 不走验证流程 → 通过"长期一致性认同"升级（你在多个决策中实际行为体现了这条价值取向）
- **不可证伪观点**：标记value_orientation走另一条通道
- **一条输入含多个判断**：建议拆分为假说群（标记relationships.supports）

---



### Layer 2: 模式识别引擎（Pattern Engine）

**定位：** 后台运行的"大脑"，从决策日志中发现你未意识到的行为规律。你不直接输入任何东西给这层——它纯粹吃Layer 0的数据。产出是描述性原则。

#### 模式类型

| 类型 | 定义 | 示例 |
|------|------|------|
| 偏好模式 | 某类场景中稳定偏好某种选择 | "金钱vs时间权衡时，80%选时间" |
| 情绪-行为模式 | 特定情绪与特定决策行为的关联 | "焦虑时决策速度快3倍，后悔率高" |
| 反模式 | 声称做A但实际反复做B | "说重视深度工作但62%时段选了碎片化" |

#### 数据结构

```yaml
pattern_entry:
  id: "PAT-012"
  discovered_at: "时间戳"
  last_updated: "时间戳"
  pattern_type: "preference|emotion_behavior|anti_pattern"

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

#### 维度体系在模式引擎中的角色

模式识别引擎使用维度轴（Axis）作为聚类单位。只有积累≥5条决策的维度轴才进入模式发现流程。维度轴的涌现机制详见[第五章](#五维度体系设计)。

#### 运行时机

| 频率 | 类型 | 做什么 |
|------|------|--------|
| 每条新决策 | 增量扫描 | 这条记录是否为某个已知emerging模式提供新证据？ |
| 每周一次 | 全量扫描 | 是否有新模式涌现？已有模式强度/趋势变化？ |
| 每月一次 | 深度分析 | 跨模式关联（共现、反相关、周期性） |

#### 增量扫描逻辑

```
新决策D-063写入
  → 提取dimensions → 匹配已知emerging/confirmed模式的trigger_condition
  → 匹配到PAT-012
  → 判断方向（一致/不一致）→ 加入supporting/contradicting
  → 重新计算strength/consistency/confidence
  → 如果从emerging达到confirmed条件 → 推送通知用户
```

#### 全量扫描逻辑

```
Phase 1: 维度聚类（找积累≥5条决策的维度轴）
Phase 2: 倾向检测（某方向占比>65% → 候选偏好模式）
Phase 3: 条件分析（反例共同特征→breaks_when; 强例特征→holds_when）
Phase 4: 新旧对比（重复→合并; 新发现→创建emerging）
```

#### 边界条件

| 场景 | 处理 |
|------|------|
| 数据不够（<5条） | 不输出，宁缺毋滥。前30天只积累不输出 |
| 无稳定偏好（50/50） | 标记为"无模式"——可能需要在该领域形成原则 |
| 识别错误 | 用户可否定。连续2次否定→停止追踪该候选 |
| 行为快速变化 | 检测"相变"（14天偏移>25%）→确认重大事件→旧模式存档，重新积累 |
| 看到但不想改 | 标记acknowledged_accepted，不触发张力检测 |

#### 模式→原则的升级路径

```
数据积累 → 模式涌现(emerging) → 证据充分(confirmed) → 用户确认 → 形成描述性原则(DP)
```

---

### Layer 3: 原则层（Principle Layer）

**定位：** 系统核心资产库。有层级、有关系、有生命周期的活体结构，不是平面列表。

#### 原则类型

| 类型 | ID前缀 | 来源 | 含义 |
|------|--------|------|------|
| 描述性(Descriptive) | DP- | Layer 2模式涌现 | "你实际在做什么" |
| 规范性(Prescriptive) | PP- | Layer 1升级 + 主动声明 | "你希望怎么做" |
| 元原则(Meta) | MP- | 用户主动声明 | 最高层统摄，≤5条 |
| 已退役(Retired) | RP- | 曾是DP/PP，后被推翻 | "曾经信过但不再信" |

#### 数据结构

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
        context_snapshot:  # 情境锚点
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
    threshold: 0.40       # 偏离率超过此值触发张力报告
    min_sample: 3         # 至少N条相关决策才开始计算
    window_days: 30       # 滑动窗口
    cooldown_days: 14     # 同一张力报告最短间隔（防骚扰）

  # 情境有效性
  context_validity:
    status: "VALID|SUSPENDED|RE-VALID|REVISED|RETIRED"
    context_anchors:  # 验证时的情境快照集合
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

| 通道 | 路径 | 特征 |
|------|------|------|
| 1. 试金石升级 | 假说→多次验证→升级 | 有外部来源，经实践检验 |
| 2. 模式涌现 | 决策积累→模式确认→你认可 | 来自行为数据 |
| 3. 决策教训 | 极好/极差结果→提炼经验 | 来自深刻经历 |
| 4. 主动声明 | 你想清楚了→录入 | 初始unvalidated，需后续验证 |

#### 冲突裁决机制

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

#### 定期复查

| 层级 | 复查周期 | 深度 |
|------|---------|------|
| Meta (Tier 1) | 6个月 | 深度（重新审视是否认同） |
| Tier 2 | 3个月 | 中等（验证数据+边界检查） |
| Tier 3-4 | 3个月 | 轻量（是否还在被使用？） |
| validation负向增多 | 立即 | 紧急复查 |
| 6个月未触发 | - | 建议降级或退役 |
| SUSPENDED状态 | 下次自然触发时 | Re-validation |

#### 退役流程

触发条件：复查时选择退役 / 连续3次负向验证 / 6个月未触发 / 被新原则替代 / context_validity=RETIRED

流程：确认意图→记录退役原因→type变为retired→完整保留历史数据→不删除

退役原则价值：演化追踪展示认知变化；决策辅助在特殊场景可能提醒"你曾有相关原则但退役了"。

---



### Layer 4: 张力检测器（Tension Detector）

**定位：** 持续对比描述性原则和规范性原则，检测"你说的"和"你做的"之间的差距，输出张力报告。

张力不是原则间的逻辑矛盾——**张力是行为与意图之间的裂缝在特定时间窗口内的累积。**

两条原则文本上矛盾不一定产生张力（可能从没在同一场景里被同时调用过）。两条看似无关的原则，可能因为真实行为暴露了隐藏的取舍关系而产生剧烈张力。

张力检测器的输入不是"两条原则的文本"，而是"一个行为序列 + 一条规范性原则 + 时间窗口"。

#### 张力的精确定义

```
张力 = 在时间窗口T内，你的实际决策模式（描述性）与你声称希望遵循的标准（规范性）
       之间的累积偏离，达到了你自己设定的敏感度阈值。
```

关键词：
- **累积偏离**：单次不遵循不是张力，是例外。系统抓趋势不抓个案。
- **时间窗口**：张力有时效性。3个月前偏离5次但最近2个月完美遵循——张力已消解。
- **敏感度由你设定**：不同原则的可容忍偏离度不同。

#### 张力的四种来源类型

| 类型 | 定义 | 检测方式 | 示例 |
|------|------|---------|------|
| 行为-意图张力 | DP-X与PP-Y指向相反 | 模式引擎输出vs原则库对比 | DP:"焦虑时快速决策" vs PP:"不在情绪波动下做重大决策" |
| 频率-声明张力 | 某PP声称高频使用但实际使用率低 | utilization_rate计算 | PP-003被触发12次，实际遵循4次 |
| 结果-信念张力 | 某PP一直遵循但结果持续为负 | validation负向累积 | 一直选长期积累但连续3次方向选错 |
| 演化-锚定张力 | 行为已相变但规范性原则还锚定旧模式 | 相变检测+原则最后更新时间 | 毕业后行为转向执行力但原则还在说"深度思考优先" |

**第四种"演化-锚定张力"最有价值也最难检测**——揭示的不是"你没做到"，而是"你已经变了但操作系统没跟上"。这是原则该更新的信号，不是你该被纠正的信号。

#### 数据结构

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

#### 检测引擎运行逻辑

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

#### 张力报告呈现设计

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

#### 用户响应后系统动作

| 选择 | 动作 |
|------|------|
| 想缩小差距 | 进入行动计划：确认触发场景→设计干预点→设跟踪窗口 |
| 原则该更新 | 触发修订流程：呈现当前→你给新表述→系统检查关系→确认更新 |
| 加边界条件 | 在boundaries.edge_cases新增→回测数据→确认 |
| 误检 | 记录原因→调整trigger/检测逻辑→连续2次误检→暂停该PP张力检测 |
| 以后再说 | 保持active→设defer_until→到期再推 |

#### 张力生命周期

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

#### 张力健康度指标

系统不应该让张力=0成为目标。健康的张力水平是2-4条active。

```yaml
tension_health:
  active_tensions: 3
  assessment: "healthy"
  # healthy: 2-4条active，覆盖不同tier
  # too_low: 0-1条 → "规范性原则可能需要升级"
  # too_high: 5+条 → "标准太多不现实，建议优先处理top 2"
  # chronic: ≥2条recurrence≥3 → "深层价值观冲突需解决"
```

#### 边界条件

| 场景 | 处理 |
|------|------|
| 新原则刚创建没数据 | 不检测。min_sample未达到前静默 |
| 用户连续dismiss多条 | 不评判。月报呈现"本月dismiss了5条"作为元数据 |
| 所有张力都是同一条PP | 该PP本身可能有问题，建议深度探索审视 |
| 报告太频繁 | cooldown保护+severity分级（mild不推，moderate周报呈现，significant+即时） |
| 描述性原则还是emerging | 不与PP做张力对比，只有confirmed的DP才进入 |
| 特殊期（搬家/考试周） | 可手动设"张力检测静默期"，数据照记事后可回看 |

#### 层间接口

| 方向 | 传什么 |
|------|--------|
| L0→L4 | 每条新决策（即时扫描） |
| L2→L4 | 新confirmed描述性模式/强度变化 |
| L3→L4 | 原则boundaries/sensitivity设置 |
| L4→L3 | 原则修订建议 |
| L4→L5 | active张力列表（决策辅助盲区提醒） |
| L4→L6 | 张力生命周期事件（演化追踪核心事件源） |
| L4→交互层 | 张力报告推送 |

---



### Layer 5: 决策辅助层（Decision Aid）

**定位：** 用户描述决策场景后，调用原则+假说+历史类比，生成正面论证+对手盘+盲区提醒+收敛问题。不做结论，用户裁决。

Layer 5是唯一要在**决策发生之前**实时工作的模块。约束组合最极端：时间压力、多原则整合、不能给结论、要给对手盘。

#### 推理引擎四阶段架构

```
用户输入场景 → Phase 1:场景解构 → Phase 2:原则召回 → Phase 3:论证合成 → Phase 4:盲区扫描
```

#### Phase 1: 场景解构

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

当系统检测到你在短时间内反复就同一类微决策来咨询时（比如"今晚加不加班"连续3天出现），系统提示：

> "你问的是今晚要不要干，但过去3天你每晚都在做这个决策。也许你真正需要决定的是：这周/这个月的工作节奏标准是什么？"
> [继续当前决策] [切换到策略级讨论]

系统不强制升维，只指出可能性。

#### Phase 2: 原则召回——三层漏斗

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
        confidence: "medium"  # 因为"是否真有复利"需要判断
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

决定后 → 写入L0 → 标记调用了哪些原则+是否遵循正面论证 → 设置回填 → 如果选了对手盘方向→特殊标记against_primary_recommendation（原则可能需要修正的信号）→ L4获得新数据 → L6记录事件

#### 边界条件

| 场景 | 处理 |
|------|------|
| 原则库<10条 | 降级：只做列举+历史类比+盲区扫描 |
| 场景太模糊 | 不硬解构，反问："能描述为'A还是B'吗？否则可能需要深度探索模式" |
| 所有原则指同一方向 | 明确告知"体系一致≠一定正确"，对手盘从假说和反例中构建 |
| 用户情绪明显不稳 | 优先触发PP-007："建议延后24小时" |
| 时间极紧（5分钟内要回复） | 极简模式：锚点原则+quick_test+最大风险点 |

---



### Layer 6: 演化追踪层（Evolution Tracker）

**定位：** 记录原则生命周期、认知变化轨迹。月度/季度报告"你变了什么"。预测你可能即将修正哪些原则。

不是"历史记录"——是"操作系统的git history + 趋势预测 + 身份内核检测"。

三大功能模块：
- **模块A 演化叙事引擎**："你变了什么"——把变化事件串成有因果关系的叙事
- **模块B 趋势预测引擎**："你即将变什么"——在原则被正式修改前发现征兆
- **模块C 身份内核检测器**："什么没变"——在所有变化中锚定"你是谁"的不变内核

#### 核心数据单位：演化事件

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

不是事件日志——是**叙事**。把事件串成"你曾经认为X→因为Y发生了→你修正为Z"的故事。

叙事生成逻辑：事件聚类→因果链重建→叙事合成→意义标注

意义标注类型：
- progressive_deepening（渐进深化）
- oscillation（摇摆）
- paradigm_shift（范式转变）
- gradual_erosion（渐进侵蚀）
- sudden_crystallization（突然结晶）

#### 模块B：趋势预测引擎

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

| 维度 | 成长特征 | 漂移特征 |
|------|---------|---------|
| 驱动力 | 有明确触发事件 | "不知道什么时候开始的" |
| 方向性 | 精确化或深化 | 模糊化或放弃 |
| 意识度 | 你知道自己变了且能解释 | 系统指出后才发现 |
| 一致性 | 与内核不冲突 | 与内核产生新张力 |

#### 报告体系

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

**年度报告：**
- 季度内容 +
- 认知演化路径可视化（阶段划分）
- 最大转变
- 内核年审
- 反思问题

---



## 五、维度体系设计

**定位：** 维度是系统的"语义路由表"——决定哪些决策被认为是"同一类"。服务于Layer 0（决策分类）、Layer 2（模式聚类）、Layer 5（原则召回）。

### 三层结构

```
第一层：维度域（Domain）— 预设≤10个 — 最粗归类，几乎不变
  例：时间分配/金钱资源/关系社交/职业方向/学习成长/健康生存/创作表达/决策方法论

第二层：维度轴（Axis）— 半涌现 — Domain内的具体张力轴
  例（时间分配域内）：深度vs碎片 / 当前任务vs新机会 / 为自己vs为他人 / 休息vs产出

第三层：情境标签（Context Tag）— 完全涌现 — 不标准化，只用于检索匹配不用于分析
  例："兼职""外包""加班""周末学习"
```

**聚类和模式发现只用第一层和第二层。第三层只用于检索。**

### 维度轴涌现机制

触发条件：某Domain内≥8条决策 + ≥4条的stated_reason出现相似权衡逻辑 + 该逻辑不匹配已有Axis + 选择方向不一致

→ 系统推出候选Axis → 用户确认 → 正式加入 → 回溯重标记

### 语义匹配机制

**不依赖关键词匹配，依赖"选择结构"匹配。**

两条决策"同一维度"的判定标准：面对的权衡结构相似（[放弃什么类型价值, 获得什么类型价值]）。

双通道匹配：
- 通道1（高权重）：结构匹配——提取implied_tradeoffs → 抽象类型 → 匹配Axis
- 通道2（辅助）：语义相似度验证
- 最终：双通道交叉验证

### 去重与合并

合并条件：决策集合重叠>70% + 方向高度一致 + 用户确认
合并执行：创建新Axis → 旧两条标记"已合并" → 历史重标记 → 模式引擎重跑

### 冷启动

- 前10天：预设3-5个Domain + 每个1-2个种子Axis + 先标Domain待积累
- 第11-20天：Domain内5+条决策 → 尝试Axis匹配
- 第21-30天：第一批涌现Axis可能出现

---

## 六、交互设计

### 6.1 七种交互场景

| # | 场景 | 触发方 | 频率 |
|---|------|--------|------|
| 1 | 捕获(Capture) | 用户 | 每天多次 |
| 2 | 咨询(Consult) | 用户 | 重大决策时 |
| 3 | 系统推送(Proactive) | 系统 | 日报/周报/事件驱动 |
| 4 | 复盘回填(Review) | 系统提醒+用户 | 按预设节点 |
| 5 | 深度探索(Explore) | 用户 | 按需 |
| 6 | 信任圈·日常沉淀 | 用户事后 | 线下交流后 |
| 7 | 信任圈·Lifeline | 用户(极稀有) | 每人每年1-2次 |

### 6.2 场景一：捕获（Capture）

**触发：** 快捷键/全局热键，从触发到输入<2秒
**输入：** 语音或文字，无格式要求
**系统处理：** 分类→结构化→关联→即时反馈
**输出模板（决策记录类）：**

```
📍 决策记录 #XXX | 日期
场景：[提取]  选项：[识别]  你的选择：[提取]  理由：[提取]  情绪：[推断]
⚡ 系统观察：[历史关联]
🔗 关联假说：[试金石库匹配]
[✓确认] [✏️修正] [➕补充]
```

**输出模板（信息源触发类）：**

```
📖 试金石入库 #T-XXX | 日期
原始观点：[还原]  来源：[提取]
🔄 格式化假说：[可操作表述]
📐 待明确边界：[系统提出的问题]
🔍 库内关联：[冲突/支持]
📊 质量评分：TFRF [X/12] Grade [X]
[✓确认] [✏️修正] [🗑️不入库]
```

**输出模板（闪念/自我观察类）：**

```
💡 模式感知 #P-XXX | 日期
你的观察：[还原]
🔬 系统验证：[用数据验证直觉]
⚠️ 系统挑战：[如果数据与感觉不完全吻合]
[✓同意] [✏️不同看法] [📌强制标记为原则]
```

### 6.3 场景二：咨询（Consult）

**触发：** 主动切换到咨询模式（不同于捕获入口）
**输入：** 描述决策场景，不限长度
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

**决定后：** 记录为决策日志 + 设置回填提醒 + 设置触发标记

### 6.4 场景三：系统主动推送（Proactive）

| 类型 | 触发 | 内容 |
|------|------|------|
| 每日简报 | 每天固定时间 | 昨日记录/待确认/待回填/今日可验证假说 |
| 模式警报 | 事件驱动 | 短时间多个同向决策/描述性vs规范性张力 |
| 演化报告 | 周/月 | 数据统计/最重要变化/最大张力/趋势预测 |

### 6.5 场景四：复盘回填（Review）

**触发：** 系统提醒（预设时间点）+ 用户主动
**输入：** 描述结果
**输出：** 结构化记录 + 标记验证/挑战了哪些假说和原则 + 设置下次追踪

**回填选项：** 正向 / 负向 / 说不清 / 已忘了 / 还没结果

### 6.6 场景五：深度探索（Explore）

多轮开放对话。系统主动追问、挑战、拓展。用于梳理领域脉络、探讨未成型想法、挑战假设、发现漏洞。

### 6.7 交互设计底层哲学

| 原则 | 含义 |
|------|------|
| 零摩擦捕获 | 想到→记录路径上无思考负担 |
| 即时结构化 | 系统立刻反馈，不是"存了以后看" |
| 永远透明 | 系统每个判断都解释"为什么这么认为" |
| 你做决定 | 系统不说"你应该X"，只呈现正反+你裁决 |
| 主动但不打扰 | 不紧急不在工作时间打断 |
| 对手盘思维 | 重要决策必有反面论证 |
| 时间连续性 | 每条记录都有前因后果追踪 |

---

## 七、信任圈机制

### 7.1 核心设计原则

**对方不需要碰你的系统，不需要知道系统存在。** 你和对方正常线下交流 → 你事后把关键信息录入 → 系统结构化外部视角。

### 7.2 两种机制

| 机制 | 触发 | 对方感受 | 频率 |
|------|------|---------|------|
| 日常沉淀 | 任何线下交流后你事后录入 | 无感知 | 随时 |
| Lifeline | 重大决策+系统门槛通过 | 受宠若惊(被信任) | 极稀有,每人≤1-2次/年 |

### 7.3 日常沉淀

场景：聊完回家，按快捷键录入对方观点。
系统处理：结构化→关联决策→标记来源。
对方负担：零。

伴侣特殊：不走Lifeline（日常共同决策关系），面对面讨论后录入，可标记"联合决策"，系统记录未解决的情绪信号。

### 7.4 Lifeline机制

**稀缺性保护门槛（系统评估）：**
- 决策影响时间跨度≥1年？
- 不可逆程度：高？
- 上次向此人发起Lifeline：多久前？
- 已独立思考超过7天？

全部通过→允许。不通过→建议不使用+原因+强制使用选项。

**系统帮你做的：** 生成精炼提问结构（背景/选项/你的思考/真正想问的），目标让对方5分钟理解+知道你认真想过+有锚点回答。

**回复处理：** 录入系统→结构化→关联原则/假说→记录Lifeline价值评估（决策后回填）。

### 7.5 数据结构口子预留

在数据层预留未来协作升级空间（现在交互100%你一人操作）：
- 决策记录:`external_perspectives`字段
- 联合决策:`participants`字段
- 原则库:`challenged_by`字段

### 7.6 远期设想

如果伴侣也有类似系统 → 联合决策可进化为两套原则系统的结构化比较 → 冲突从情绪层拉到逻辑层。

---



## 八、系统可读性设计

**定位：** 确保原则库增长后用户仍能保持操控感。六大机制协同工作。

### 机制1：三层视图（Dashboard→Map→Detail）

- **Dashboard**：10秒概览——system_health + top_attention(≤3) + core_anchor
- **Map**：结构化全景——原则地图（每个MP下的子原则状态/张力/活跃度）
- **Detail**：按需钻入任何节点的完整数据

### 机制2：可解释性追踪链

系统每个输出都附带完整reasoning_steps，用户可逐步追问"为什么"直到满意。用户可在任何step上override（系统从该步重新推理）。

### 机制3：确认度标记

每条信息标记：
- system_inferred（系统推断）
- user_glanced（用户扫过）
- user_confirmed（用户确认）
- user_deeply_reviewed（用户深度审视）

新鲜度：fresh / aging / stale

### 机制4：注意力预算

- 每日最多3条推送
- 每周review预算30分钟
- 复杂度上限：active原则>50条→触发压缩建议（合并/降级/归纳/层级化）

### 机制5：Override Protocol

你可以覆盖系统任何判断，系统不反驳不追问。但连续覆盖同类>5次→轻声问一次"要不要调整系统逻辑？"→然后不再问。

### 机制6：月度Sync Ritual（15-20min）

1. **确认内核**（3min）：系统呈现不变内核→你确认
2. **审视变化**（5min）：本月3个最重要变化→你确认/质疑
3. **抽检理解**（5min）：随机抽2条本月使用的原则→展示使用逻辑→你确认/纠正
4. **复杂度检查**（2min）：当前指标→觉得可控/太多

---

## 九、系统自主学习机制

**定位：** 系统从外部信息源中提取"元层面"知识以优化自身运行逻辑——与用户提取"内容层面"假说形成双管线并行。

### 双管线模型

你看信息源提取"对我决策有什么用"（内容层面）→产出假说。
系统看同一信息源提取"这个思考框架能不能优化我的运行逻辑"（元层面）→产出系统更新提案。

同一输入源，两条完全不同的处理管线。

### 系统关注的五类知识

| 类型 | 找什么 | 示例 |
|------|--------|------|
| 思维框架 | 改进模式识别/推理逻辑 | OODA循环、贝叶斯更新 |
| 决策方法论 | 升级L5推理引擎 | 预设验尸法、10/10/10法则 |
| 认知偏误研究 | 加入盲区扫描 | 新发现的偏误和去偏方法 |
| 系统设计模式 | 优化架构本身 | 反脆弱设计、渐进复杂度管理 |
| 前沿研究 | 决策科学新发现 | 特定条件下某策略更优的实证 |

### 系统更新提案（System Update Proposal）

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

### 生成逻辑

不是每条输入都产生提案。系统管线只在检测到信号时激活：
- 内容含"方法论/框架/系统/过程"类？
- 逻辑可抽象为通用决策/分析模式？
- 涉及认知科学/行为经济学实证？
- 与系统已知缺陷/边界相关？

自检标准（≥2条通过才入队）：可操作性 / 问题对应性 / 非冗余性 / 复杂度可控

### 通知与审批

每日通知（如有）：展示发现+用在哪+更新前后差异+论证+风险。你决定：批准/修改/拒绝/延后/讨论。

### 边界控制

```yaml
auto_learning_constraints:
  max_proposals_per_week: 3
  max_pending_updates: 5
  max_monthly_approved: 4
  post_update_observation: 14天
  all_updates_reversible: true
```

### 系统Changelog

每条更新记入版本历史。5年后可看到"系统本身从v1.0到v15.0的方法论演化史"。

---

## 十、冷启动计划（30天）

### Phase 1: 纯记录期（第1-10天）

- 每天至少2个决策记录（大小不限）
- 格式极简：场景/选项/选择/理由/情绪
- 同时试金石库开始运行（正常看信息源，有感觉的扔进去）
- 系统不输出任何分析
- 维度体系：预设3-5个Domain + 每个1-2个种子Axis + 先标Domain待积累

### Phase 2: 模式识别期（第11-20天）

- 系统对前10天记录跑第一轮分析
- 检测：倾向性？情绪-决策关联？理由中的重复逻辑？
- 试金石库假说开始与决策做关联匹配
- 可能产生第一个emerging模式
- 维度体系：Domain内5+条决策 → 尝试Axis匹配

### Phase 3: 初步涌现期（第21-30天）

- 系统输出第一批描述性原则（3-5条）
- 呈现："你实际在遵循的原则似乎包括……你认可吗？"
- 认可→确认为描述性原则
- 不认可→产生张力→系统开始帮你成长
- 维度体系：第一批涌现Axis可能出现

---

## 十一、待深化问题清单

| # | 问题 | 涉及层 | 状态 |
|---|------|--------|------|
| 1 | ✓ Layer 4张力检测器完整设计 | L4 | 已完成 |
| 2 | ✓ Layer 5决策辅助层推理逻辑设计 | L5 | 已完成 |
| 3 | ✓ Layer 6演化追踪层完整设计 | L6 | 已完成 |
| 4 | ✓ 维度体系设计（预设vs涌现/层级/去重/语义匹配） | L0/L2 | 已完成 |
| 5 | ✓ 假说化的质量标准（TFRF框架） | L1 | 已完成 |
| 6 | 原则operational_guide的精细化（决策树vs线性？多原则整合？） | L3/L5 | 待深化 |
| 7 | 冲突裁决的时间维度（短期/中期/长期优先级可能不同） | L3 | 待深化 |
| 8 | ✓ 系统可读性设计 | 全局 | 已完成 |
| 9 | ✓ 原则置信度的情境衰减 | L3 | 已完成 |
| 10 | 技术实现路径选择（存储/前端/检索/向量化） | 工程 | 待定 |

---

## 十二、设计决策记录（Design Decision Log）

| 决策点 | 最终选择 | 否决方案 | 原因 |
|--------|---------|---------|------|
| 冷启动策略 | 先记录30天再涌现原则 | 从信息源直接提炼原则 | 别人的原则未经你验证不是你的原则 |
| 信息源定位 | 待验证假说(Touchstone) | 直接作为原则来源 | 防止确认偏误引擎 |
| 决策辅助输出 | 对手盘(正反两面) | 给出确定结论 | 确认偏误风险/决策质量>速度 |
| 信任圈交互 | 你事后录入,对方无感知 | 对方在系统中操作 | 对方无动机/像社交软件回消息/浪费他人时间 |
| Lifeline设计 | 极稀有+系统门槛保护 | 随时可问 | 稀缺性=社交价值/"受宠若惊"效应 |
| 原则类型 | 描述性+规范性+张力 | 单一类型 | 张力才是成长引擎 |
| 模式引擎输出 | 需用户确认才生效 | 系统自动生成原则 | 防止误检/保持用户操控感 |
| 张力定义 | 行为累积偏离(非逻辑矛盾) | 原则文本对比 | 文本矛盾≠实际张力 |
| 论证合成 | 推理链合成(非列举) | 列举每条原则观点 | 列举式用户还得自己整合 |
| 维度匹配 | 选择结构匹配(非关键词) | 关键词匹配 | 关键词无法抓住本质权衡 |
| 情境衰减模型 | 情境相变跳转 | 线性时间衰减 | 时间本身不影响有效性,情境变化才影响 |
| 系统学习 | 双管线(内容+元) | 单管线只提取假说 | 系统本身也需要演化 |

---

*文档结束。Personal Principle OS v1.0 全层设计完成。*
