# AI Research Intelligence Platform Demo PRD


> 文档版本：v1.0  
> 产品阶段：可开发 Demo / MVP 规格  
> 默认种子用例：Generative AI × Industrial Design  
> 建议数据规模：500–1000 篇 WoS / Scopus 真实或脱敏样例文献  
> 核心定位：All-in-one AI Research Intelligence Platform  

## 0. 文档摘要

本 Demo 用于验证一条完整、可解释、可复现的科研文献工作流：

```text
上传 WoS/Scopus 文件
→ Research Setup
→ 低成本语义排序与分层 AI 筛选
→ 用户 Include / Exclude 反馈
→ Adaptive Research Context 更新
→ Final Corpus
→ Bibliometric Explorer
→ 真实算法生成统计与网络图谱
→ Bibliometric Semantic Layer
→ Evidence-grounded Research Insights
→ Methodology Export
```

Adaptive Research Context 是贯穿筛选、分析与洞察生成的底层能力，不是独立的 Research Memory 产品。Demo 不训练或微调模型，不让 LLM 替代文献计量计算，也不将自动生成的“研究空白”表述为事实。

---

## 1. 产品背景与问题

科研人员在进行主题探索、综述准备或研究选题时，通常需要在多个割裂工具之间完成文献导出、清洗、初筛、计量分析、网络可视化和结果解释。当前流程存在以下问题：

1. 大量标题与摘要需要逐篇人工筛选，重复劳动高。
2. 研究问题、纳入排除规则与实际判断经常脱节，筛选标准会演化但缺少结构化记录。
3. 文献计量工具能够生成图表，但图表与研究问题之间缺少可追溯的解释层。
4. 通用 LLM 可以生成流畅结论，却容易混淆统计事实、模型推断与研究者判断。
5. AI 辅助过程缺少版本、参数、决策日志与证据引用，难以复现。

本产品用一个 Workspace 内的连续工作流解决以上割裂：以 Adaptive Research Context 维护研究意图，以分层 AI 降低筛选成本，以真实算法完成计量计算，再以结构化语义层约束 LLM 的解释范围。

## 2. 产品目标与非目标

### 2.1 Demo 目标

- 跑通 500–1000 篇文献从上传到洞察导出的完整闭环。
- 支持 WoS / Scopus CSV 或 TXT 的字段识别、预览、映射、清洗和去重。
- 通过 Embedding、规则与人工反馈降低人工排序和初筛负担。
- 让用户可查看、编辑并确认 Include / Exclude / Boundary 三类 Context。
- 用真实算法生成年度发文趋势、关键词共现、作者合作网络、主题聚类。
- 让每条 AI 洞察能够回溯到统计结果、聚类、图谱节点或代表文献。
- 记录足以复现 Demo 结果的输入摘要、规则、模型、参数、版本和操作日志。
- 建立指标基线，验证“减少 60%–80% 人工初筛工作量”等目标；该数字仅为待验证目标，不是实测结果。

### 2.2 非目标

- 不建设覆盖所有数据库格式的通用导入平台。
- 不进行模型 Fine-tune、自训练基础模型或自动 Active Learning 模型训练。
- 不做多人实时协作、复杂权限、机构级知识库或商业计费。
- 不自动抓取付费全文，不绕过出版商权限。
- 不用 LLM 计算共现、中心性、聚类或趋势指标。
- 不自动声称发现“Research Gap”。相关输出只能称为 **Potential Research Opportunity** 或 **Underexplored Connection**，并显著标注“需人工验证”。
- PRISMA 不作为全平台默认规范；仅当用户选择对应的 systematic/scoping review protocol 时，才启用相关字段、流程图或导出支持。

## 3. 种子用例

### 3.1 主题

**Generative AI × Industrial Design**：研究生成式 AI 在工业设计、产品设计、概念生成、共创、人机协作与创意支持中的应用。

### 3.2 数据集

- 500–1000 篇 WoS / Scopus 导出的真实或脱敏样例记录。
- 最低字段：Title、Abstract、Authors、Year、Keywords、Source、DOI。
- 应包含明显相关、明显无关与边界样本，便于验证三层筛选。
- 预先由研究者抽取 100–200 篇建立人工 gold set，用于 Demo 指标评估；gold set 不进入 prompt。

### 3.3 示例筛选语义

- Include：生成式 AI 直接用于工业/产品设计过程、设计创意、概念生成、设计师协作或设计评价。
- Exclude：仅讨论制造优化、纯图像生成技术、建筑设计、药物设计，且与工业/产品设计研究问题无直接联系。
- Boundary：研究对象或设计语境不明确；只在全文中可能出现工业设计应用；“design”一词语义含混。

## 4. 目标用户

### 4.1 核心用户

- 需要快速建立主题语料库的研究生、博士生和青年研究者。
- 进行文献计量、领域综述前期探索的科研人员。
- 需要可解释 AI 辅助筛选的跨学科研究团队成员。

### 4.2 Demo 假设

- 用户理解标题/摘要筛选，但不要求具备编程能力。
- 用户能判断 AI 建议是否符合其研究边界。
- 用户接受 AI 提供优先级与理由，但最终语料库选择权归用户。

## 5. 核心用户流程

1. 用户创建 Project，输入研究主题，选择研究目的与可选 review protocol。
2. 上传 WoS / Scopus 文件，系统解析、映射、校验和去重。
3. 系统基于研究问题生成 Include / Exclude / Boundary 初稿，用户编辑确认 Context v1。
4. 系统生成 Embedding，按规则匹配与语义相关度进行候选排序。
5. 用户逐篇或批量确认 Include / Exclude；不确定条目进入 Boundary Queue。
6. LLM 仅处理边界样本或用户显式请求解释的记录，返回结构化判断、理由与证据字段。
7. 系统根据反馈提出 Context 规则建议；用户接受、编辑或拒绝后产生新版本。
8. 用户冻结筛选结果，生成 Final Corpus 快照。
9. 系统用确定性/可记录算法计算四类文献计量结果并渲染图表与网络。
10. 系统把统计结果序列化为 Bibliometric Semantic Layer，再交给 LLM 生成带证据引用的洞察。
11. 用户查看、修订、验证洞察，并导出语料库、分析结果和 Methodology Report。

---

## 6. Workspace 总体架构

左侧固定导航：

1. Research Setup
2. Literature Screening
3. Bibliometric Explorer
4. Research Intelligence

顶部全局栏：Project 名称、Corpus 状态、Context 版本、保存状态、任务状态、Methodology Export。

全局状态：

- `DRAFT`：研究设置未确认。
- `INGESTING`：文件解析/清洗中。
- `READY_TO_SCREEN`：可开始筛选。
- `SCREENING`：筛选进行中。
- `CORPUS_FROZEN`：已生成 Final Corpus 快照。
- `ANALYZING`：文献计量计算中。
- `INSIGHTS_READY`：洞察可用。
- `FAILED`：任务失败，可查看错误并重试。

## 7. 页面详细规格

### 7.1 Workspace 1：Research Setup

#### 信息架构与组件

- Project Header：名称、描述、创建时间、数据状态。
- Research Question：自由文本输入；AI 可帮助改写，但必须由用户确认。
- Research Purpose：探索性分析 / 文献计量 / narrative review / systematic review / scoping review / other。
- Protocol：默认 `None`；仅相关 review 类型可选 PRISMA 支持。
- File Uploader：支持 `.csv`、`.txt`，显示文件大小、来源类型和上传进度。
- Field Mapping：源字段到标准字段的映射表，含自动识别置信度。
- Data Preview：前 20 条记录、缺失率、编码异常、重复候选。
- Deduplication Summary：DOI 精确去重、标准化标题近似去重，允许人工保留。
- Adaptive Research Context Editor：三个可编辑区块：Include、Exclude、Boundary。
- Confirm Setup 按钮：确认后创建 Context v1 并启动 Embedding Job。

#### 关键交互

- 上传后自动探测 WoS/Scopus；无法识别时进入手动映射。
- 保存映射前必须映射 Title；Abstract 缺失允许继续但显示风险。
- AI 生成规则只是草稿；用户确认前不影响筛选。
- 用户更改规则后显示未保存状态；确认产生不可变版本，后续可新建版本。

#### 页面状态

- Empty：引导输入问题和上传文件。
- Uploading / Parsing：进度、当前步骤、取消按钮。
- Mapping Required：突出未映射必填字段。
- Validation Warning：缺失、乱码、重复、异常年份。
- Ready：可预览清洗后记录并确认。
- Failed：给出可操作错误、错误码与重试入口。

#### 验收标准

- 能成功导入至少一份 500–1000 篇样例文件。
- Title 映射率 100%；每条记录生成稳定内部 ID。
- DOI 精确重复能够识别；无 DOI 时可基于规范化标题提示疑似重复。
- 用户可手动修正字段映射和重复判断。
- Context v1 包含三个区块、研究问题、创建者、时间与来源。
- 确认后异步生成 Embedding，不阻塞页面操作。

### 7.2 Workspace 2：Literature Screening

#### 信息架构与组件

- Screening Progress：总数、已决策、Include、Exclude、Boundary、未处理。
- Efficiency Panel：人工审阅数量、AI 建议数、批量接受数、耗时估计；均标注测量口径。
- Filter Bar：状态、年份、关键词、来源、置信度、AI 层级。
- Screening Queue：按优先级排序的文献卡片或表格。
- Paper Detail Drawer：Title、Abstract、Keywords、Authors、Year、Source、DOI、AI 建议、理由、匹配规则与证据片段。
- Decision Controls：Include / Exclude / Boundary / Undo；支持键盘快捷键。
- Batch Actions：仅对高置信且同一规则命中的记录开放；确认弹窗显示影响数量。
- Context Side Panel：当前版本、规则、最近反馈、待确认规则建议。
- Context Suggestion Review：Accept / Edit & Accept / Reject。
- Audit Timeline：决策人、时间、旧值、新值、来源（manual/rule/LLM/batch）。

#### 关键交互

- 默认先展示高信息价值样本：边界、不确定和能区分规则的样本；支持切换为相关度排序。
- 每次人工决策即时保存，并保留上一个决策可撤销。
- AI 建议不自动写入最终决策，除非用户执行明确的批量确认。
- 当累计一定数量的新反馈（默认 10 条）或发现重复模式时，系统可生成规则建议。
- 接受规则建议后生成 Context 新版本，并对未决策记录重新评分；已人工决策不被覆盖。
- Finalize Corpus 前展示未决策和 Boundary 数量；用户必须选择继续处理或明确接受当前快照。

#### 页面状态

- Embedding Pending：可浏览，不能开始全队列排序。
- Ready / Screening。
- No Results：筛选条件无匹配。
- Context Re-scoring：显示后台进度，旧排序仍可读。
- Conflict：AI 建议与已确认规则或人工标签冲突。
- Finalizing：锁定当前筛选快照。
- Failed：单条 LLM 失败不阻塞人工筛选；可重试。

#### 验收标准

- 用户可在不调用 LLM 的情况下完成纯人工筛选。
- 每条决策都有可追溯事件；Undo 不删除历史，而是追加反向事件。
- Context 更新须经用户确认，且已决策记录不被自动改写。
- LLM 返回无效 JSON 时自动重试一次，仍失败则标记并允许人工处理。
- Final Corpus 是带版本号的不可变快照，至少记录纳入记录 ID、Context 版本和筛选截止事件。
- 重新打开项目后筛选进度与滚动位置可恢复。

### 7.3 Workspace 3：Bibliometric Explorer

#### 信息架构与组件

- Corpus Summary：文献数、年份范围、来源数、作者数、关键词数、缺失率。
- Analysis Controls：分析类型、参数、最小频次、Top N、聚类设置、是否合并同义词。
- Annual Publication Trend：折线/柱状图和数据表。
- Keyword Co-occurrence：网络图、节点表、边表、聚类筛选。
- Author Collaboration Network：网络图、作者表、合作边表、组件/中心性摘要。
- Topic Clusters：二维可视化或聚类列表、关键词、代表文献、规模、平均年份。
- Chart Inspector：点击节点/簇后查看支撑记录。
- Export：PNG/SVG（P1）、CSV/JSON（P0）、参数清单。

#### 真实算法约束

- 年度发文趋势：按规范化 publication year 分组计数。
- 关键词共现：对标准化 Author Keywords/Index Keywords 建立文献内无向共现边；边权为共现文献数。
- 作者合作网络：对每篇文献作者集合建立无向合作边；边权为合著文献数。
- 主题聚类：Demo 推荐使用文献 Embedding + KMeans；簇数可由用户设定或在候选范围内用 silhouette score 建议。二维投影仅用于展示，不作为聚类依据。可选 TF-IDF 关键词描述簇。
- NetworkX 计算网络与基础指标；所有参数写入 analysis run。
- LLM 不得参与计数、连边、中心性和聚类归属计算。

#### 页面状态

- Corpus Not Frozen：提示先完成筛选。
- Ready to Analyze。
- Computing：分步骤进度。
- Partial Success：某一分析失败时其余结果仍可用。
- Empty Result：数据不足或阈值过高，给出调参建议。
- Stale：Final Corpus 产生新版本后，旧分析明显标记为过期。

#### 验收标准

- 同一 Corpus、代码版本和参数下结果可重复。
- 图表数值与导出表格一致，抽查 20 条记录可追溯到源文献。
- 每种分析显示算法名、关键参数、运行时间和输入 Corpus 版本。
- 用户点击节点、边或簇可查看支撑文献。
- 不允许把可视化布局坐标解释为统计关系。

### 7.4 Workspace 4：Research Intelligence

#### 信息架构与组件

- Insight Scope：选择使用的分析 run、研究问题、Context 版本。
- Generate Insights：生成概览、趋势、主题结构、合作结构、Potential Research Opportunity。
- Insight Cards：标题、结论、类型、置信/支持等级、证据引用、限制、人工验证状态。
- Evidence Drawer：统计指标、图谱节点/边、簇、代表文献及 DOI。
- Claim Editor：用户编辑、接受、标记需复核或删除。
- Contradiction/Insufficient Evidence Banner。
- Export Report：Markdown/JSON（P0），PDF/DOCX（P2）。

#### Evidence-grounded Insight 约束

- LLM 只接收 Bibliometric Semantic Layer，不接收未经裁剪的数据库全量文本。
- 每个事实性 claim 必须带 `evidence_ids`；没有证据的 claim 不得展示为结论。
- 输出区分：`descriptive_finding`、`interpretation`、`potential_opportunity`、`limitation`。
- `potential_opportunity` 必须使用“可能”“值得进一步验证”等措辞，并显示“需要人工验证”。
- 禁止使用“已证明”“必然”“研究空白”等超出证据的措辞。
- 引用的文献 ID、统计 ID、cluster ID 必须经服务端校验存在且属于当前 run。
- 服务端对数字做一致性校验；无法验证的数字删除或降级为错误状态。

#### 页面状态

- No Analysis：引导完成 Bibliometric Explorer。
- Generating。
- Ready。
- Evidence Validation Failed：隐藏问题 claim，允许重试。
- Stale：分析或 Corpus 已更新。
- User Verified / Needs Review。

#### 验收标准

- 每张 Insight Card 至少有一个有效 evidence ID；纯限制说明除外。
- 点击证据可定位到对应图表、数据行或代表文献。
- 所有“Potential Research Opportunity / Underexplored Connection”都有人工验证提示。
- 篡改或不存在的 evidence ID 不能通过服务端保存。
- 用户修改内容、验证状态与原始 AI 输出均保留审计记录。

---

## 8. 数据字段与最小数据库模型

建议 PostgreSQL + pgvector；所有主键使用 UUID，时间使用 UTC。

### 8.1 标准文献字段

| 字段 | 类型 | 必需 | 说明 |
|---|---|---:|---|
| id | uuid | 是 | 内部 ID |
| project_id | uuid | 是 | 所属项目 |
| source_record_id | text | 否 | WoS UT、Scopus EID 等 |
| title | text | 是 | 原始标题 |
| normalized_title | text | 是 | 去重用 |
| abstract | text | 否 | 摘要 |
| authors | jsonb | 否 | 标准化作者数组 |
| year | int | 否 | 发表年份 |
| author_keywords | jsonb | 否 | 作者关键词 |
| index_keywords | jsonb | 否 | 数据库关键词 |
| source_title | text | 否 | 期刊/会议 |
| doi | text | 否 | 规范化 DOI |
| citations | int | 否 | 导入时引用数及来源 |
| document_type | text | 否 | 文献类型 |
| language | text | 否 | 语言 |
| raw_record | jsonb | 是 | 原始字段 |
| embedding | vector | 否 | title + abstract 表示 |
| content_hash | text | 是 | 去重与复现 |

### 8.2 最小表

- `projects`：项目设置、研究问题、purpose、protocol、当前状态。
- `source_files`：文件元数据、hash、来源、字段映射、解析状态；不在日志记录原始内容。
- `papers`：标准化文献。
- `duplicate_groups`：重复组、匹配方法、相似度、保留记录。
- `context_versions`：版本号、研究问题、include/exclude/boundary、变更摘要、确认人。
- `context_suggestions`：建议、支持反馈 ID、状态、用户编辑结果。
- `screening_scores`：规则分、语义分、LLM 结果、模型和 Context 版本。
- `screening_decisions`：当前有效决策，便于查询。
- `decision_events`：追加式审计事件，禁止物理覆盖。
- `corpus_snapshots`：不可变语料快照及 paper IDs/hash。
- `analysis_runs`：语料版本、算法、参数、代码版本、状态。
- `analysis_artifacts`：结果类型、结构化 JSON、文件地址、hash。
- `insight_runs`：模型、prompt 版本、输入 semantic layer hash、状态。
- `insights`：claim、类型、evidence IDs、验证状态、原始输出。
- `jobs`：异步任务、进度、错误、重试次数。

### 8.3 关键约束

- `context_versions(project_id, version)` 唯一。
- 一个 Project 可有多个 Corpus Snapshot；Analysis Run 必须绑定一个 Snapshot。
- 人工决策优先级高于 AI 建议；重评分不得覆盖人工决策。
- 删除 Project 采用软删除；Demo 提供二次确认和恢复窗口。

## 9. AI 接入方案

### 9.1 Embedding

- 输入：规范化 `title + abstract + keywords`，字段间加明确分隔符。
- 用途：主题相关度排序、相似记录、聚类输入、边界候选识别。
- 按 `content_hash + embedding_model` 缓存，避免重复调用。
- Abstract 缺失时允许仅标题和关键词生成，并标注低信息量。

### 9.2 LLM Structured Output

用途仅限：

1. Research Question 与初始 Context 草稿。
2. 边界文献筛选建议与理由。
3. 从人工反馈提出 Context 更新建议。
4. 基于 Semantic Layer 生成证据约束洞察。

所有调用使用 JSON Schema；服务端校验，失败自动重试一次。保存模型名称、参数、prompt 版本、输入 hash、输出和 token usage。Demo 温度建议 0–0.2。

### 9.3 Few-shot 与 Context 更新

- 选取已确认的代表性 Include、Exclude、Boundary 示例，每类默认最多 5 条。
- 示例优先选择近期、规则覆盖多样、靠近决策边界的记录。
- 严禁把 gold set 标签泄露到 prompt。
- Context 建议由 LLM 提出，必须给出触发样本和规则变更；用户确认后才生成新版本。
- Demo 不 Fine-tune。Context 版本 + few-shot 即构成适应机制。

## 10. 成本感知的分层筛选逻辑

### 10.1 漏斗

```text
Layer 0：确定性清洗、去重、语言/年份等用户规则
Layer 1：Embedding 相关度 + 关键词/规则匹配
Layer 2：高置信排序或候选批次，人工快速确认
Layer 3：仅对 Boundary / 冲突 / 用户请求项调用 LLM
Layer 4：人工最终决策
```

### 10.2 初始阈值建议（配置项，不是固定真值）

- 明显相关：语义分位 Top 20% 且命中 Include 规则，优先展示，不自动纳入。
- 明显低相关：Bottom 30% 且命中 Exclude 规则，进入低优先队列，不自动排除。
- LLM 候选：中间区间、规则冲突、信息不足或用户指定记录。
- LLM 调用预算：默认不超过总记录 20%；达到预算时提示用户调整或继续纯人工。

阈值须通过种子数据验证后调整。记录每层通过量、人工覆盖率、误判率和成本。

## 11. 文献计量真实计算规格

| 分析 | 输入 | 核心计算 | 输出 |
|---|---|---|---|
| 年度趋势 | year | group-by count；可选同比，仅在分母有效时计算 | year/count/growth |
| 关键词共现 | 标准化关键词 | 文献内组合计数、加权无向图、频次阈值 | nodes/edges/clusters |
| 作者合作 | 标准化作者 | 合著组合计数、组件、degree 等 | nodes/edges/metrics |
| 主题聚类 | paper embeddings | KMeans；silhouette 建议 k；TF-IDF 描述簇 | cluster assignment/labels/representatives |

同义词合并表必须可查看并导出。作者消歧在 Demo 只做规范化姓名与完全匹配，不声称解决同名异人问题，并在限制中说明。

## 12. Bibliometric Semantic Layer

Semantic Layer 是真实统计结果与 LLM 之间的只读、版本化中间层。它必须：

- 由后端从 `analysis_artifacts` 确定性生成。
- 只包含经过验证的数值、实体 ID、关系、代表文献和限制。
- 每个对象有稳定 `evidence_id`。
- 包含 Corpus、Context、Analysis Run 和生成器版本。
- 进行大小控制：Top N + 摘要统计；不因 token 限制改变原始分析结果。

示例见 19.3。

## 13. Evidence-grounded Insight 与防幻觉

### 13.1 生成约束

- LLM 只能引用输入中存在的 `evidence_id` 和 `paper_id`。
- 每个 claim 明确区分 observation 与 interpretation。
- 所有数字由服务端与 Semantic Layer 二次核对。
- 文献题名、作者、DOI 只可从数据库引用，不允许模型补全。
- Semantic Layer 未覆盖的信息应返回 `insufficient_evidence`。
- 机会类判断不得表述为确定事实。

### 13.2 服务端验证

1. JSON Schema 校验。
2. Evidence ID 存在性与归属校验。
3. 数值字符串与证据值匹配校验。
4. 禁用措辞扫描，如“证明了”“明确的研究空白”；根据 claim 类型做替换或拒绝。
5. 失败 claim 单独隔离，不让整个 insight run 失败。

## 14. Methodology Export / 可复现记录 MVP

P0 导出一个 ZIP，包含：

- `methodology.md`：研究问题、purpose、protocol、筛选流程、人工/AI 决策统计、限制。
- `corpus.csv`：Final Corpus 标准字段。
- `screening_decisions.csv`：paper ID、最终决策、时间、来源、Context 版本。
- `context_versions.json`：完整版本与确认记录。
- `analysis_parameters.json`：算法、阈值、随机种子、依赖/代码版本。
- `analysis_results/`：四类结果的 CSV/JSON。
- `insights.json`：claim、证据、用户验证状态。
- `manifest.json`：输入文件 hash、导出时间、各文件 hash、模型/prompt 版本。

不默认声称符合 PRISMA。仅在用户选择相应 protocol 且必需数据完整时，P1 支持生成 PRISMA 相关计数或流程材料。

## 15. Adaptive Research Context 规格

### 15.1 结构

- Research Question
- Include Rules：规则 ID、文本、理由、示例、状态。
- Exclude Rules：同上。
- Boundary Rules：不确定条件、需要补充的信息、处理策略。
- Confirmed Examples：每类代表性 paper IDs。
- Version Metadata：版本、来源、确认人、时间、变更摘要。

### 15.2 更新规则

- AI 可建议新增、合并、拆分或澄清规则。
- 建议必须引用至少一个触发反馈，显示预估影响的未决策记录数。
- 用户可接受、编辑后接受或拒绝。
- 接受后创建新版本，不覆盖旧版；支持切回旧版并重新评分。
- 回滚 Context 只改变当前活动版本，不删除后来版本或历史事件。

## 16. 异常与回滚最低实现

- 上传失败：保留已上传文件元数据，允许重试解析或重新映射。
- Job 失败：保存阶段和错误码；幂等重试，不重复创建结果。
- LLM 超时/限流：指数退避，最多自动重试 2 次；之后允许人工继续。
- 无效 LLM 输出：结构化重试一次，然后标记失败。
- 用户误操作：最后一次单条/批量筛选可 Undo，所有变更保留事件。
- Context 回滚：切换活动版本并创建新的重评分 Job。
- Corpus 更新：创建新 Snapshot，旧分析保留但标记 Stale。
- 分析失败：按 artifact 类型独立重试，不清除成功结果。
- 导出失败：不影响项目数据，展示错误与重新生成入口。

## 17. 技术栈建议

- 前端：Next.js + React + TypeScript；TanStack Query；ECharts 优先，复杂网络交互可选 D3。
- 后端：FastAPI + Pydantic + SQLAlchemy/Alembic。
- 数据：PostgreSQL + pgvector。
- 异步任务：Demo 可用 FastAPI BackgroundTasks；若部署需要可靠重试，P1 使用 Redis + Celery/RQ。
- AI：OpenAI API，Embedding + 支持 Structured Outputs 的 LLM。
- 分析：pandas、NetworkX、scikit-learn；可选 UMAP 仅用于二维展示。
- 文件：本地对象目录用于开发；部署时使用 S3 兼容存储。
- 测试：pytest、Playwright、前端组件测试。

建议采用单仓库：`apps/web`、`apps/api`、`packages/schemas`、`fixtures/seed`。

## 18. API 接口草案

### Project / Setup

- `POST /api/projects`
- `GET /api/projects/{project_id}`
- `PATCH /api/projects/{project_id}`
- `POST /api/projects/{project_id}/files`
- `POST /api/files/{file_id}/parse`
- `PATCH /api/files/{file_id}/mapping`
- `GET /api/files/{file_id}/preview`
- `POST /api/projects/{project_id}/deduplicate`

### Context

- `GET /api/projects/{project_id}/contexts`
- `POST /api/projects/{project_id}/contexts/draft`
- `POST /api/projects/{project_id}/contexts/{version}/activate`
- `GET /api/projects/{project_id}/context-suggestions`
- `POST /api/context-suggestions/{id}/resolve`

### Screening

- `POST /api/projects/{project_id}/embeddings`
- `GET /api/projects/{project_id}/screening/queue`
- `GET /api/papers/{paper_id}`
- `POST /api/papers/{paper_id}/screening-suggestion`
- `POST /api/projects/{project_id}/decisions`
- `POST /api/projects/{project_id}/decisions/batch`
- `POST /api/projects/{project_id}/decisions/{event_id}/undo`
- `POST /api/projects/{project_id}/corpora`

### Analysis / Insight / Export

- `POST /api/corpora/{corpus_id}/analysis-runs`
- `GET /api/analysis-runs/{run_id}`
- `GET /api/analysis-runs/{run_id}/artifacts/{type}`
- `GET /api/analysis-runs/{run_id}/semantic-layer`
- `POST /api/analysis-runs/{run_id}/insight-runs`
- `GET /api/insight-runs/{run_id}`
- `PATCH /api/insights/{insight_id}`
- `POST /api/projects/{project_id}/exports`
- `GET /api/jobs/{job_id}`

### 接口规则

- 异步操作返回 `202 + job_id`。
- 写接口支持 `Idempotency-Key`。
- 列表使用 cursor pagination。
- 错误结构统一为 `{code, message, details, request_id, retryable}`。

## 19. 核心数据结构 / JSON Schema

### 19.1 Screening Suggestion

```json
{
  "$schema": "https://json-schema.org/draft/2020-12/schema",
  "type": "object",
  "additionalProperties": false,
  "required": ["decision", "confidence", "reason", "matched_rule_ids", "evidence"],
  "properties": {
    "decision": {"enum": ["include", "exclude", "boundary"]},
    "confidence": {"type": "number", "minimum": 0, "maximum": 1},
    "reason": {"type": "string", "maxLength": 600},
    "matched_rule_ids": {"type": "array", "items": {"type": "string"}},
    "evidence": {
      "type": "array",
      "maxItems": 5,
      "items": {
        "type": "object",
        "additionalProperties": false,
        "required": ["field", "text"],
        "properties": {
          "field": {"enum": ["title", "abstract", "keywords"]},
          "text": {"type": "string", "maxLength": 300}
        }
      }
    },
    "uncertainty": {"type": ["string", "null"], "maxLength": 300}
  }
}
```

### 19.2 Context Suggestion

```json
{
  "operation": "add",
  "section": "boundary",
  "proposed_rule": "当 design 指算法设计且无产品或工业设计语境时，标记为 Boundary。",
  "rationale": "近期反馈显示 design 存在语义歧义。",
  "supporting_decision_event_ids": ["uuid-1", "uuid-2"],
  "estimated_affected_unscreened_count": 37
}
```

### 19.3 Semantic Layer

```json
{
  "schema_version": "1.0",
  "project_id": "uuid",
  "corpus_snapshot_id": "uuid",
  "analysis_run_id": "uuid",
  "context_version": 3,
  "corpus_summary": {
    "paper_count": 684,
    "year_min": 2018,
    "year_max": 2026,
    "limitations": ["部分文献缺少作者关键词"]
  },
  "evidence": [
    {
      "evidence_id": "trend:2024",
      "type": "annual_count",
      "value": {"year": 2024, "count": 126},
      "supporting_paper_ids": ["uuid-a", "uuid-b"]
    },
    {
      "evidence_id": "cluster:2",
      "type": "topic_cluster",
      "value": {
        "paper_count": 91,
        "top_terms": ["co-creation", "concept generation", "designer"]
      },
      "representative_paper_ids": ["uuid-c", "uuid-d"]
    }
  ]
}
```

### 19.4 Insight Output

```json
{
  "insights": [
    {
      "type": "potential_opportunity",
      "title": "可进一步验证的人机共创与评价方法连接",
      "claim": "当前语料中，共创主题与设计评价主题的直接共现较少，可能构成值得进一步验证的 Underexplored Connection。",
      "evidence_ids": ["cluster:2", "edge:cluster2-cluster5"],
      "limitations": ["共现较少不等同于不存在相关研究", "需要全文与领域专家验证"],
      "requires_human_validation": true
    }
  ]
}
```

## 20. 性能、隐私、安全与错误处理

### 20.1 性能目标

- 1000 篇 CSV/TXT 解析与预览：开发环境目标 30 秒内。
- 常规列表首屏：P95 小于 2 秒，不含首次 AI/分析任务。
- 单条决策保存：P95 小于 500ms。
- Embedding、聚类和 LLM 使用异步 Job，页面显示阶段性进度。
- 图谱默认只渲染 Top N 节点，避免浏览器卡顿；完整数据可下载。

以上为 Demo 验收目标，需在指定硬件与网络环境实测。

### 20.2 隐私与安全

- 只上传用户有权处理的数据；界面提示不要上传受限全文或敏感个人信息。
- API Key 仅保存在服务端环境变量，绝不进入浏览器或日志。
- 对上传扩展名、MIME、大小、编码进行校验；文件名随机化，阻止路径穿越。
- LLM 最小化传输：默认仅标题、摘要、关键词和 Context；不发送原始文件。
- 日志脱敏，不记录完整摘要、API Key 或原始上传内容。
- Project 级资源访问校验；即使 Demo 是单用户，也在数据访问层保留 project ownership 边界。
- 提供项目软删除和彻底删除入口；彻底删除需二次确认。

### 20.3 错误处理

- 用户错误：字段级说明与修复建议。
- 数据错误：报告记录行号、字段与可下载错误清单。
- 系统错误：request ID、重试入口，不暴露堆栈。
- 外部 AI 错误：区分限流、超时、无效响应与配额不足。
- 所有 Job 必须幂等；部分失败不得污染已发布 Corpus 或 Analysis Run。

## 21. 埋点与验证指标

所有效率指标同时记录分母、任务规模和口径，不能只报百分比。

### 21.1 Screening Efficiency

- `time_to_first_decision`
- `manual_reviewed_count / total_records`
- `decisions_per_active_minute`
- `llm_scanned_count / total_records`
- `batch_confirmed_count`
- `context_suggestion_acceptance_rate`
- 与纯人工基线相比的工作量下降比例

待验证目标：在 Corpus Quality 不显著下降的前提下，减少 60%–80% 人工初筛工作量，或使筛选效率提升约 2–5 倍。该目标必须通过对照实验验证，不能作为已实现效果宣传。

### 21.2 Corpus Quality

- 在人工 gold set 上计算 Recall/Sensitivity、Precision、Specificity、F1。
- Boundary 命中率与 Boundary 最终转化分布。
- 人工推翻 AI 建议比例，按置信区间和筛选层级拆分。
- 重复检测 precision/recall 的人工抽样检查。

建议优先保护 Recall，具体阈值由研究场景与 protocol 决定，不设全平台统一医学综述阈值。

### 21.3 Analysis Efficiency

- 从 Corpus Freeze 到四类分析 Ready 的时间。
- 首次成功生成率、重跑率、参数修改次数。
- 从图表点击到支撑文献的访问率。

### 21.4 Insight Trust

- 有效 evidence coverage：带有效证据 claim / 全部 claim。
- 数字一致性校验通过率。
- 用户 Accept / Edit / Reject / Needs Review 比例。
- 无法证实 claim 拦截数。
- 用户打开 Evidence Drawer 的比例与人工验证完成率。

### 21.5 关键事件

`project_created`、`file_uploaded`、`mapping_confirmed`、`context_confirmed`、`screening_decision_made`、`decision_undone`、`batch_confirmed`、`context_suggestion_resolved`、`corpus_frozen`、`analysis_started/completed/failed`、`insight_generated/validated/edited/rejected`、`methodology_exported`。

## 22. MVP 开发优先级

### P0：必须跑通

- 单用户 Project 与四 Workspace 导航。
- WoS/Scopus 一种 CSV + 一种 TXT 样例导入、字段映射、预览、基础去重。
- Research Question 与三类 Adaptive Context 的编辑、确认、版本化。
- Embedding、相关度排序、单条人工决策、Undo、Boundary Queue。
- 边界记录 LLM Structured Output 与基本 few-shot。
- 用户确认 Context 建议；重评分不覆盖人工结果。
- Final Corpus 快照。
- 四类真实算法分析和 ECharts 展示。
- Semantic Layer 与带证据 Insight。
- Markdown/JSON/CSV Methodology Export。
- Job 状态、基础错误处理、审计事件和核心埋点。

### P1：提高可用性与可信度

- 批量确认与安全限制。
- 更完整的同义词表、作者规范化和调参体验。
- PRISMA 相关 protocol 的条件式支持。
- SVG/PNG 导出、Context 影响预览、缓存与可靠任务队列。
- gold set 评估页与指标仪表盘。

### P2：Demo 后再评估

- 多用户协作、角色权限、评论和冲突合并。
- 全文处理、更多数据库格式、外部检索 API。
- 高级作者消歧、动态/层次聚类、引用网络。
- PDF/DOCX 报告、机构部署和计费。
- 模型 Fine-tune；只有数据量、基线与收益证据充分时再评估。

## 23. Codex 实施顺序

每一步应形成可运行、可测试的增量，避免先写全部 UI 再补数据链路。

### Task 0：仓库与契约

- 初始化 Next.js、FastAPI、PostgreSQL/pgvector、迁移与本地运行配置。
- 建立共享枚举、API 错误格式、Job 模型和环境变量模板。
- 加入健康检查和最小 CI。
- 完成条件：前后端、数据库可一条命令启动，健康检查通过。

### Task 1：种子数据与导入管线

- 固化 500–1000 篇样例和预期字段映射。
- 实现上传、格式探测、解析、预览、标准化、hash 与去重候选。
- 写解析单元测试和坏文件测试。
- 完成条件：样例可稳定导入，重复与错误报告可查看。

### Task 2：Research Setup

- 实现 Project、研究问题、purpose/protocol。
- 实现 Context 三类编辑器、草稿、确认和版本表。
- 可先用 mock AI 生成规则，再替换真实调用。
- 完成条件：用户可从空项目得到 Context v1。

### Task 3：Embedding 与筛选基础

- 实现 embedding job、缓存、相关度与规则分。
- 实现筛选队列、详情抽屉、单条决策、事件日志、Undo。
- 完成条件：不依赖 LLM 也能筛完整个数据集并恢复进度。

### Task 4：LLM 边界判断与 Adaptive Context

- 接入 Structured Output；加入 schema 校验、预算、重试和成本记录。
- 实现 few-shot 选择与 Context Suggestion Review。
- 接受新版本后仅重评未决策记录。
- 完成条件：边界建议、规则确认、Context v2 和重评分闭环可演示。

### Task 5：Final Corpus

- 实现冻结前检查、不可变 Snapshot、hash 和版本展示。
- 完成条件：可复现相同 Final Corpus，并能创建新版本而不覆盖旧版。

### Task 6：真实文献计量引擎

- 先实现年度趋势，再实现关键词、作者网络和主题聚类。
- 每类分析独立 artifact、测试、参数和失败状态。
- 用小型 fixture 手工验证计数与边权。
- 完成条件：四类结果与预期 fixture 一致，重复运行稳定。

### Task 7：Bibliometric Explorer

- 用 ECharts 实现图表、网络、筛选、Inspector 和 CSV/JSON 导出。
- 完成条件：用户能从节点/簇追溯支撑文献，参数与数据一致。

### Task 8：Semantic Layer 与 Insights

- 实现确定性序列化、evidence registry、token 裁剪策略。
- 接入 Insight Structured Output 和服务端证据/数字校验。
- 实现 Insight Cards、Evidence Drawer 与人工验证状态。
- 完成条件：无有效证据的 claim 无法展示或保存；机会类均有人工验证提示。

### Task 9：Methodology Export

- 汇总输入 hash、Context、筛选事件、Corpus、算法参数、洞察和 manifest。
- 完成条件：从导出包可以识别数据、版本、参数和主要决策链。

### Task 10：端到端验证与 Demo 打磨

- 跑通种子用例，记录人工基线与 AI 辅助数据。
- 补齐加载、空、失败、Stale、回滚状态。
- Playwright 覆盖主路径；故障注入覆盖 LLM 限流和分析失败。
- 完成条件：可连续演示完整闭环；所有效率数字均展示为实测结果或明确的待验证目标，二者不混淆。

## 24. Demo 验收总清单

- [ ] 500–1000 篇种子数据可导入、映射、预览和去重。
- [ ] 三类 Context 可编辑、版本化、确认和回滚。
- [ ] 分层筛选避免全量 LLM 扫描，调用预算可见。
- [ ] 人工决策拥有最高优先级并可审计、Undo。
- [ ] Final Corpus 是不可变快照。
- [ ] 四类计量结果来自真实算法，参数与结果可导出。
- [ ] 图谱节点、边、簇能追溯到文献。
- [ ] Semantic Layer 版本化并具有稳定 evidence IDs。
- [ ] 洞察通过证据、数字和措辞校验。
- [ ] 只使用 Potential Research Opportunity / Underexplored Connection，且提示人工验证。
- [ ] PRISMA 仅在相应 review protocol 下出现。
- [ ] Methodology Export 包含复现所需的 MVP 记录。
- [ ] AI 调用失败时核心人工流程仍可继续。
- [ ] “减少 60%–80% 人工初筛工作量”等只作为待验证目标，未经实测不写成成果。

## 25. 开发决策默认值

为避免 Codex 在第一轮实现中反复等待产品决策，采用以下默认值：

- 单用户、本地优先，不实现登录；数据模型仍保留 `owner_id` 扩展位。
- 先完整支持项目提供的两份种子格式，不承诺任意 WoS/Scopus 导出变体。
- 用户决策永远优先，AI 不自动纳入或排除文献。
- Context 每次确认生成新版本；Corpus 每次冻结生成新 Snapshot。
- LLM 默认最多扫描总记录 20%，可由用户显式提高。
- 聚类默认以 silhouette score 在合理候选 k 中给出建议，用户可覆盖。
- 所有展示性结论都必须通过 Semantic Layer 和 Evidence Validator。
- Demo 成功标准是闭环可信与可演示，不是功能数量最大化。
