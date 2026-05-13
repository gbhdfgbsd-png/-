# Personal Principle OS — 产品设计文档 (PRD)

> 版本: v0.1 | 日期: 2026-05-13 | 状态: Layer 0-3 已设计，Layer 4-6 待设计

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
│  [待设计]           │ │  [待设计]               │
└─────────────────────┘ └────────────────────────┘
                  │          │
                  └────┬─────┘
                       ▼
          ┌──────────────────────────────┐
          │  Layer 6                      │
          │  演化追踪层                    │
          │  (Evolution Tracker)          │
          │  [待设计]                     │
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
  decision_dimensions: ["income_vs_growth", "time_allocation"]
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

#### 输入处理流水线

```
用户原始输入
  → Step 1: 分类（决策记录 / 信息源触发 / 闪念）
  → Step 2: 结构化提取（场景/选项/选择/理由）
  → Step 3: 维度推断（维度/情绪/确信度/量级/可逆度/速度）
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

  # 元数据
  importance_to_you: "high|medium|low"
  revisit_count: 0
```

#### 输入处理流水线

```
用户输入（"刚看了某某的文章，他说……"）
  → Step 1: 确认是"信息源触发"类型
  → Step 2: 提取原始观点/来源/用户反应
  → Step 3: 假说化（去修辞 → 转为"如果X则Y"可操作结构）
  → Step 4: 适用边界初步划定（known + uncertain）
  → Step 5: 冲突检测（扫描现有库，标记supports/conflicts）
  → Step 6: 即时反馈呈现 → 用户确认
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

#### 特殊类型：价值取向声明

"人生的意义在于体验"等不可单次验证的观点 → 标记为value_orientation → 不走验证流程 → 通过"长期一致性认同"升级（你在多个决策中实际行为体现了这条价值取向）

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
      dimensions_involved: ["income_vs_growth"]
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
Phase 1: 维度聚类（找积累≥5条决策的维度）
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

#### 定期复查

| 层级 | 复查周期 | 深度 |
|------|---------|------|
| Meta (Tier 1) | 6个月 | 深度（重新审视是否认同） |
| Tier 2 | 3个月 | 中等（验证数据+边界检查） |
| Tier 3-4 | 3个月 | 轻量（是否还在被使用？） |
| validation负向增多 | 立即 | 紧急复查 |
| 6个月未触发 | - | 建议降级或退役 |

#### 退役流程

触发条件：复查时选择退役 / 连续3次负向验证 / 6个月未触发 / 被新原则替代

流程：确认意图→记录退役原因→type变为retired→完整保留历史数据→不删除

退役原则价值：演化追踪展示认知变化；决策辅助在特殊场景可能提醒"你曾有相关原则但退役了"。

---


### Layer 4: 张力检测器（Tension Detector）— [待设计]

**定位：** 持续对比描述性原则和规范性原则，检测"你说的"和"你做的"之间的差距，输出张力报告。

### Layer 5: 决策辅助层（Decision Aid）— [待设计]

**定位：** 用户描述决策场景后，调用原则+假说+历史类比，生成正面论证+对手盘+盲区提醒+收敛问题。不做结论，用户裁决。

### Layer 6: 演化追踪层（Evolution Tracker）— [待设计]

**定位：** 记录原则生命周期、认知变化轨迹。月度/季度报告"你变了什么"。预测你可能即将修正哪些原则。

---

## 五、交互设计

### 5.1 七种交互场景

| # | 场景 | 触发方 | 频率 |
|---|------|--------|------|
| 1 | 捕获(Capture) | 用户 | 每天多次 |
| 2 | 咨询(Consult) | 用户 | 重大决策时 |
| 3 | 系统推送(Proactive) | 系统 | 日报/周报/事件驱动 |
| 4 | 复盘回填(Review) | 系统提醒+用户 | 按预设节点 |
| 5 | 深度探索(Explore) | 用户 | 按需 |
| 6 | 信任圈·日常沉淀 | 用户事后 | 线下交流后 |
| 7 | 信任圈·Lifeline | 用户(极稀有) | 每人每年1-2次 |

### 5.2 场景一：捕获（Capture）

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

### 5.3 场景二：咨询（Consult）

**触发：** 主动切换到咨询模式（不同于捕获入口）
**输入：** 描述决策场景，不限长度
**系统处理三阶段：** 场景解析→原则调用→双面论证生成
**输出结构：**

```
🎯 决策咨询 #C-XXX
📋 场景解析：[核心选择/维度/时间压力/可逆程度]
⚖️ 正面论证：[调用的原则+连接点+综合指向]
🥊 对手盘：[反面论据+盲区提醒]（同样来自你的原则体系）
🔲 收敛问题：[帮你思考的问题，系统不做结论]
📎 历史类比：[过去类似情况你怎么选，结果如何]
→ 你的决定是？
```

**决定后：** 记录为决策日志 + 设置回填提醒 + 设置触发标记

### 5.4 场景三：系统主动推送（Proactive）

| 类型 | 触发 | 内容 |
|------|------|------|
| 每日简报 | 每天固定时间 | 昨日记录/待确认/待回填/今日可验证假说 |
| 模式警报 | 事件驱动 | 短时间多个同向决策/描述性vs规范性张力 |
| 演化报告 | 周/月 | 数据统计/最重要变化/最大张力/趋势预测 |

### 5.5 场景四：复盘回填（Review）

**触发：** 系统提醒（预设时间点）+ 用户主动
**输入：** 描述结果
**输出：** 结构化记录 + 标记验证/挑战了哪些假说和原则 + 设置下次追踪

**回填选项：** 正向 / 负向 / 说不清 / 已忘了 / 还没结果

### 5.6 场景五：深度探索（Explore）

多轮开放对话。系统主动追问、挑战、拓展。用于梳理领域脉络、探讨未成型想法、挑战假设、发现漏洞。

### 5.7 交互设计底层哲学

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

## 六、信任圈机制

### 6.1 核心设计原则

**对方不需要碰你的系统，不需要知道系统存在。** 你和对方正常线下交流 → 你事后把关键信息录入 → 系统结构化外部视角。

### 6.2 两种机制

| 机制 | 触发 | 对方感受 | 频率 |
|------|------|---------|------|
| 日常沉淀 | 任何线下交流后你事后录入 | 无感知 | 随时 |
| Lifeline | 重大决策+系统门槛通过 | 受宠若惊(被信任) | 极稀有,每人≤1-2次/年 |

### 6.3 日常沉淀

场景：聊完回家，按快捷键录入对方观点。
系统处理：结构化→关联决策→标记来源。
对方负担：零。

伴侣特殊：不走Lifeline（日常共同决策关系），面对面讨论后录入，可标记"联合决策"，系统记录未解决的情绪信号。

### 6.4 Lifeline机制

**核心洞察：** 一个足够重要足够稀有的问题，"你来问我"本身是给予——给了对方"被信任"的价值感。

**稀缺性保护门槛（系统评估）：**
- 决策影响时间跨度≥1年？
- 不可逆程度：高？
- 上次向此人发起Lifeline：多久前？
- 已独立思考超过7天？

全部通过→允许。不通过→建议不使用+原因+强制使用选项。

**系统帮你做的：** 生成精炼提问结构（背景/选项/你的思考/真正想问的），目标让对方5分钟理解+知道你认真想过+有锚点回答。

**回复处理：** 录入系统→结构化→关联原则/假说→记录Lifeline价值评估（决策后回填）。

### 6.5 数据结构口子预留

在数据层预留未来协作升级空间（现在交互100%你一人操作）：
- 决策记录:`external_perspectives`字段
- 联合决策:`participants`字段
- 原则库:`challenged_by`字段

### 6.6 远期设想

如果伴侣也有类似系统 → 联合决策可进化为两套原则系统的结构化比较 → 冲突从情绪层拉到逻辑层。

---

## 七、冷启动计划（30天）

### Phase 1: 纯记录期（第1-10天）

- 每天至少2个决策记录（大小不限）
- 格式极简：场景/选项/选择/理由/情绪
- 同时试金石库开始运行（正常看信息源，有感觉的扔进去）
- 系统不输出任何分析

### Phase 2: 模式识别期（第11-20天）

- 系统对前10天记录跑第一轮分析
- 检测：倾向性？情绪-决策关联？理由中的重复逻辑？
- 试金石库假说开始与决策做关联匹配
- 可能产生第一个emerging模式

### Phase 3: 初步涌现期（第21-30天）

- 系统输出第一批描述性原则（3-5条）
- 呈现："你实际在遵循的原则似乎包括……你认可吗？"
- 认可→确认为描述性原则
- 不认可→产生张力→系统开始帮你成长

---

## 八、待深化问题清单

以下设计问题已识别但尚未解决，将在后续迭代中逐一攻克：

| # | 问题 | 涉及层 | 优先级 |
|---|------|--------|--------|
| 1 | Layer 4张力检测器完整设计 | L4 | 高 |
| 2 | Layer 5决策辅助层推理逻辑设计（多原则如何整合输出） | L5 | 高 |
| 3 | Layer 6演化追踪层完整设计 | L6 | 高 |
| 4 | 维度体系设计（预设vs涌现？层级？去重？语义匹配？） | L0/L2 | 高 |
| 5 | 假说化的质量标准（什么叫"可操作"？好假说vs烂假说？） | L1 | 中 |
| 6 | 原则operational_guide的精细化（决策树vs线性？多原则整合？） | L3/L5 | 中 |
| 7 | 冲突裁决的时间维度（短期/中期/长期优先级可能不同） | L3 | 中 |
| 8 | 系统可读性设计（原则库增长后如何保持用户操控感） | 全局 | 中 |
| 9 | 原则置信度的情境衰减（人生阶段变化后旧原则是否需要re-validation） | L3 | 低 |
| 10 | 技术实现路径选择（存储/前端/检索/向量化） | 工程 | 待定 |

---

## 设计决策记录（Design Decision Log）

记录设计过程中的关键决策点和已否决方案，供未来回溯：

| 决策点 | 最终选择 | 否决方案 | 原因 |
|--------|---------|---------|------|
| 冷启动策略 | 先记录30天再涌现原则 | 从信息源直接提炼原则 | 别人的原则未经你验证不是你的原则 |
| 信息源定位 | 待验证假说(Touchstone) | 直接作为原则来源 | 防止确认偏误引擎 |
| 决策辅助输出 | 对手盘(正反两面) | 给出确定结论 | 确认偏误风险/决策质量>速度 |
| 信任圈交互 | 你事后录入,对方无感知 | 对方在系统中操作 | 对方无动机/像社交软件回消息/浪费他人时间 |
| Lifeline设计 | 极稀有+系统门槛保护 | 随时可问 | 稀缺性=社交价值/"受宠若惊"效应 |
| 原则类型 | 描述性+规范性+张力 | 单一类型 | 张力才是成长引擎 |
| 模式引擎输出 | 需用户确认才生效 | 系统自动生成原则 | 防止误检/保持用户操控感 |

---

*文档结束。Layer 4-6待后续设计会话补充。*
