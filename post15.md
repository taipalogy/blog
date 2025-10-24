---
title: '規格驅動開發專案管理'
description: 'Project Management in Spec-Driven Development'
date: 2025-10-16
tags: ['prompt', 'framework', 'ai', 'shorthand']
image: ""
categories: [""]
authors: ["台灣話專科"]
draft: true
---

規格驅動功能項管理Framework是準做一个管理軟体規格エ³語義カㇷ¹視覺上エ⁷層次，是一个類似Head-Up Display (HUD)アㇷ³是資訊圖表産生器エ³概念。伊カ³對下底イェㇴ⁵ジㇴ²，像Amazon Kiroアㇷ³是GitHub Spec Kit，來エ⁷文字エ⁷規格（例，YAML/Markdown）轉換做可巡覽、ホ³人讀有エ⁷視覺物件，包括map, cluster, attribute heatmap, dependency flow等等。

チッ¹个framework透過カ³結構化エ³規格當做版本控制、意圖捕捉エ³人工産出，ハㇺ³Sean Grove對規格エ³定義相容。チァエ産出，包括規格、文件、カㇷ¹template等等結構化エ³、有形エ⁷輸出，マ³コㅗㇷ¹エ³驅動對功能項カㇷ¹attributeエ³管理。マ³エ³タㆁ²準做一个カ³人類AI共同協作エ³流程カㇷ¹任務對ホ⁷齊エ⁷真相來源，也着是一个エ³確保持續エ³理解、合作、カㇷ¹開發任務執行エ⁷，有決定性エ³參照。

チッ¹个framework透過對規格、功能項，カㇷ¹attributeエ³定義カㇷ¹管理，以一種有結構エ³，可追蹤エ，ハㇺ³需求，規格，validationエ³標準實行有對ホ⁷齊エ⁷樣態，相容於專案管理。

因為チッ¹个framework無包括像GitHub Spec Kitエ³plan，task，implement等指令，所以特別強調專案管理內底エ³功能項管理。マ³是因為アㇴ¹ネ，所以frameworkコㅗㇷ¹附加一个HUD overlayエ³功能，エ³用エ對專案內容エ³變化カㇷ¹影響範圍做即時エ⁷顯示。

ツ³アㇴ¹ネ，「Spec-Driven」有カㇷ¹framework方法論對應，「Feature」有カㇷ¹資料庫單位對應，「Semantic Infographics」有カ³HUD overlay突顯추ッラィㇷ。一个ホ³規格驅動エ³提示驅動frameowrkマ³着エ³用エ管理一个專案內底エ³功能項ア⁷。

## 規格驅動

最近OpenAIエ³Sean Grove提出一个觀念號做Spec Driven Development。Spec着是specification，着是規格エ³意思。對一個規格來コㆁ²，伊エ³有一个目標カㇷ¹動機，表示ベㇷ¹開發エ³方向，カㇷ¹開發エ³原因理由。一个規格マ³アィ²表示啥乜事項無包括띠³規格內底。

Sean Grove띠³演講The New Code內底指出，規格着是新エ⁷程式碼。意思着是對規格エ³タㆁ²産生程式碼、UI、測試、文件、教學等等。

譬喻コㆁ，有一个地理視野（GeoSight）エ³系統，ラㇴエ³タㆁ²カ³伊用띠³物資登記カㇷ¹配送。像コㆁ最近띠³花蓮光復災區着有뚜¹띠ㅗㇷ³需要各種物資登記、管理、カㇷ¹配送エ³情形，像水ラㇷ、食物ラㇷ、民生用品ラㇷ，各種工具ラㇷ。着エ³用エ用チッ¹个framework來做軟體系統開發內底功能項エ³管理。

## 規格動詞

規格驅動功能項管理Framework內底有幾若个規格動詞：
* Specify：定義一个功能項，也着是feature
* Prioritize：設定優先權
* Bundle：カ³功能項包做一个module(模組)
* Trace：對依存路徑行
* Validate：檢查一致性，coverage
* Simulate：カ³功能項アㇷ³是module提去模擬，看尹アㇴ¹ツァ˜開展（카ィ⁷띠ェㇴ²）アㇷ³是過渡

規格動詞是規格驅動功能項管理Frameworkエ³生命週期動作，軟體開發動作，處理規格エ³語義本身。尹エ³タㆁ²對一个アㇷ³是二个以上エ⁷功能項做操作。尹改變規格エ³state。

控制層spec layer是對規格エ³設計カㇷ¹處理。利用`spec::`來做規格動詞エ³接頭詞。

## Attribute動詞

Attribute動詞是規格驅動功能項管理Frameworkエ³資料操作動作，處理功能項內底エ³field/屬性。尹エ³タㆁ²對一个功能項內底エ³各種attribute做操作。尹無改變規格。尹保留規格エ³state。尹カ³attributeエ³view重新塑形，是視覺化驅動エ⁷。

以資料庫エ³角度來看，伊是カ³功能項內底エ³孤一个attribute當做是一个field。囥띠ァㇺ²資料庫內底エ³一个功能項號做一个功能項entry。

* Surface：カ³重點attributeギゥ추ッ¹ラィ⁷看
* Filter：過濾
* Sort：排序
* Cluster：分做一个cluster
* Highlight：強調突顯

控制層attribute layer是資料カㇷ¹功能項attributeエ³視覺化。利用`attr::`來做attribute動詞エ³接頭詞。

## 地理視野（GeoSight）系統

地理視野系統功能項以中文表示，是利用Gemini産生エ：
* "F001"，"地理視野地圖 (GeoSight Map)"
* "F002"，"智能配送路徑優化"
* "F003"，"災區交通與路況標註"
* "F004"，"任務即時追蹤與狀態更新"
* "F005"，"快速一鍵餐食提報"
* "F006"，"PWA 離線資料暫存與同步"
* "F007"，"緊急工具提報與媒合"
* "F008"，"代理人/無網路替代提報"
* "F009"，"庫存實時儀表板"
* "F010"，"領取憑證 QR Code 核銷"
* "F011"，"物資分配溯源記錄"
* "F012"，"災區數據分析報告"

若ベㇷ¹カ³쩨12項功能下ルェㇷ¹資料庫，用下腳チッ¹个指令：
`encode all 12 features into the framework's database schema(spec_database.md)`

資料庫內底有地理視野エ³規格了後，着エ³タㆁ²開始利用framework做操作。

## 操作

### Surface，Highlight
Surface：為着能見度，カ³選着エ³attribute顯示추ッラィㇷ。띠³一个view內底，注重表現特定エ⁷資料（例，title，priority）。
Highlight：強調特定エ⁷attribute（像risk_level，validation_status）來ホ⁷ラㆁ⁷注意，通常是視覺上エ⁷(例，color-coding critical issues)。

尹ロㆁ是ホ³attributeコㅗㇷ¹卡ホ³人注目。Surface是カ³尹包括띠³輸出內底，highlight是視覺上去カ³尹強調。ア¹ㆬ³コㅗㇷ¹，surface是カㇷ¹資料選擇有關，アhighlight是カㇷ¹視覺的エ³突顯有關。

```
specify(features("F001,F002,F003")) + surface(attribute("title,priority,risk_level")) + highlight(attribute("risk_level")) + layout(view("kanban"))
```

チッ¹个鏈利用資料庫ホ³GeoSightエ³dashboard module浮키ㇷラィㇷ，コㅗㇷ¹用highlight來協助快速風險評估。

### Bundle，Cluster
Bundle:為着組織的エ³目的，カ³功能項以明示方式組키ㇷラィㇷ變做一个module，創造一个定義好エ³結構。
Cluster:為着分析アㇷ³是視覺化コㅗㇷ¹無愛創一个持續性エ³module，基於共享エ³屬性（例，依存關係，module），カ³功能項アㇷ³是attribute以動態方式分組。

尹ロㆁ是牽涉着カ³功能項分組，ㆬ³コㅗㇷ¹bundle是創造一个正式、有持續性エ³module，アcluster是一个分析性アㇷ³是視覺性エ³分組，無啥可能有持續性。

```
specify(features("F005,F006,F007")) + bundle(module("PWA Module")) + trace(attribute("dependencies")) + cluster(attribute("dependencies")) + layout(view("dependency_graph"))
```

쩨充份利用資料庫エ³module field，用띠³組織エ³bundleカㇷ¹用띠³GeoSight前線依存關係視覺化エ³clusterロㆁエ³タㆁ²ホㆁ⁵展示추ッラィㇷ。

### Prioritize，Sort
Prioritize:Assign一个優先權value到一个功能項或者是module（例，"high"，"medium"），反映伊エ³重要性アㇷ³是緊急性，修改ヘ功能項エ³attribute。
Sort:為着顯示アㇷ³是分析，針對一个attribute（例，priority，effort）カ³功能項アㇷ³是module重新排序， 無改變추⁷띠³下底エ³資料。

尹ロㆁ是對排序做處理。Prioritize設定ホ³sortエ³タㆁ²用來對事項做排序エ⁷優先權attribute。ㆬ³コㅗㇷ¹，prioritizeエ³改變資料，アsortカㇴ⁷ナ⁷カ³畫面呈現組織키ㇷラィㇷ。

```
specify(features("F009,F010")) + prioritize(features("F009,F010"), attrs{priority:"high"}) + surface(attribute("id,title,priority")) + sort(attribute("priority"), attrs{order:"desc"}) + layout(view("kanban"))
```

チッ¹个鏈對투ㇴ³好エ³資料庫ギゥ資料，カ³GeoSightエ³物流功能項提昇，確保高優先權項目，像庫存警示，エ³像泡アㇴ¹ネ浮키ㇷラィㇷ。

### Trace，Validate
Traceカㇷ¹validateロㆁ是提孤一个attribute當做argument，雖然尹二个ロㆁ是spec verb。

Trace是提一个attribute（例，dependencies），專注띠³追隨跨功能項アㇷ³是moduleエ³特定關係アㇷ³是屬性。伊エ³目的是對結띠³孤一个attributeエ³連結（例，依存關係鏈）做追蹤，愛有分析上エ⁷精準性，

Validate是，對ヒッ¹个特定エ³跨功能項アㇷ³是moduleエ³屬性，提一个attribute（例，"test_coverage"アㇷ³是 "validation_status"）去檢查一致性カㇷ¹coverage。

ㆬ³コㅗㇷ¹，Traceカㇷ¹validateロㆁ是透過カ³attribute檢查應用到相關エ，ホ³查詢カㇷ¹上下文所指定エ⁷實体（例，功能項，module），以隱示エ⁷方式對規格/功能項做操作。

チッ¹个frameworkカ³卡濶エ³操作轉授ホ³鏈키ㇷラィㇷエ³動詞（例，カㇷ¹surfaceアㇷ³是cluster結合），應對複雜規格/功能項分析。

```
trace(attribute("dependencies"), attrs{feature_id:"F002"}) + validate(attribute("test_coverage"), attrs{feature_id:"F002"}) + surface(attribute("test_coverage"))
```

若真正ベㇷ¹traceアㇷ³是validate對幾若个attributeアㇷ³是規个規格做操作，你エ³タㆁ²カ³幾若个call鏈키ㇷラィㇷアㇷ³是띠ァㇺ²framework內底定義一个新動詞。

### 新需求
功能性需求（啥，為啥乜）：
使用者故事是功能性需求シォㆁ³カィ²直接エ³表達。逐个故事ロㆁ有カ³誰需要啥カㇷ¹為啥乜表達ホ⁷清楚。
驗收標準是詳細エ³，可檢證エ³條件，是逐个使用者故事ロㆁ有附カㇷ²エ³。

非功能性需求（グァ³好，如何）：
技術制限。功能項所需要使用エ⁷工具，framework。
非技術需求。包括安全性，效能。言明功能項エ³品質，可靠性。

若是有新エ⁷需求，エ³タㆁ²增加一个新功能項。利用新功能項エ³描述來カ³新需求エ³規格貯レㇷ，而且模擬伊エ³影響。

```
specify(feature("F013"), attrs{priority:"high", dependencies:"F004"}) + simulate(feature("F013")) + surface(attribute("priority,description"))
```

若是有增加一个新エ⁷功能項，frameworkエ³HUD自動化鏈エ³カ³kanban（看板）viewアㇷ³是dependency graph啟動，根據ヒッ¹个改變エ³上下文。

通常エ³ホㆁ⁷啟動去顯示新功能項エ³attribute：
Kanban（看板）view：
```
specify(feature("F013")) + surface(attribute("title,priority,dependencies")) + layout(view("kanban"))
```

若是新功能項有依存關係：
Dependency graph：
```
trace(attribute("dependencies"), attrs{feature_id:"F013"}) + layout(view("dependency_graph"))
```

HUD自動化鏈是ホ³語義解析層觸發エ³。語義解析層エ³透過建議器去偵測像功能項增加チッ¹種エ³改變，コㅗㇷ¹根據上下文去啟動相關エ⁷view。

띠ァㇺ²純文字エ⁷使用環境內底，マ³エ³タㆁ²用ASCII sketch來畫圖。

### HUD作成速記表達

1. Attribute Bar
```
attr::surface(priority,risk,coverage) + attr::highlight(priority="high")
```

2. Dependency Radar
```
spec::trace(dependencies) + attr::cluster(dependencies)
```

3. Heatmap Panel
```
attr::cluster(risk_level) + attr::highlight(coverage<80%)
```

4. Timeline Strip
```
rule::sequence(lifecycle_stage) + layout(view("timeline"))
```

5. Filter Lens
```
attr::filter(status="open") + layout(view("kanban"))
```

6. Highlight Glow
```
attr::highlight(coverage_gap) 
```

7. Composition Cluster
```
spec::bundle(module="Command Center") + rule::composition(nested="subspecs")
```

若準一改着ベㇷ¹띠³所有エ⁷overlay，一个multi-panel HUD：
```
spec::trace(dependencies) 
+ attr::surface(priority,risk,coverage) 
+ attr::cluster(risk_level) 
+ attr::highlight(coverage<80%) 
+ rule::sequence(lifecycle_stage)
```

アㇴ¹ネ，`verbs = operators`，`attributes = data feeds`，カㇷ¹`HUD = composed visualization`。

## Attribute是Argument
Attribute是ホㆁ⁵當做名詞屬性對待，顛倒不是一个獨自存在エ⁷實体。チッ¹个framework假定attribute是名詞（例，一个功能項有一个優先權attribute）固有エ³，而且無需要一个分別エ⁷/Nouns/attribute.md。另一方面，attribute是ホㆁ⁵定義띠³資料庫schema內底，而且是透過attribute動詞處理。

## 規則

規則不是名詞（像功能項アㇷ³是module），因為尹是管コㆁ實体是アㇴ¹ツァ˜ホㆁ⁵處理，不是去代表實体。另外一方面，尹像meta動詞アㇴ¹ネ動作，用一个查詢鏈去指揮運作其它エ⁷動詞(spec::*, attr::*)。

規則透過提供語境차ㇺ³制限カㇷ¹名詞、動詞互補，ホ³尹ホㆁ⁵包括띠³查詢鏈アㇷ³是速記內底成做有效。舉例來コㆁ²，rule::sequence確保띠³你エ³查詢內底エ³timeline viewカㇷ¹生命週期階段有對ホ⁷齊，增強ヒッ¹个HUDエ³關聯性。

## 上下文敏感

有カㇷ²一个地理視野(GeoSight) 專案エ³規格驅動功能項管理Framework是上下文敏感エ³，因為伊エ³語義解析層エ³針對最近エ⁷規格改變アㇷ³是資料庫上下文去カ³查詢做調適。ホ³合スエ、針對地理視野災難回應需要エ³動態回應，成做有可能。

## Framework

規格驅動功能項管理Framework，カㇷ²語義資訊圖表

以下prompt利用ChatGTP，Grok産生：
````

---
# Spec-Driven Feature Management Framework with Semantic Infographics

The New Code — Sean Grove, OpenAI

The framework deliberately excludes the plan, task, and implement phases, focusing exclusively on enhancing the specify command of GitHub Spec Kit.

## Folder Structure
```
/PromptFramework/
  /SpecVerbs/            (specify.md, prioritize.md, bundle.md, trace.md, validate.md, simulate.md)
  /AttributeVerbs/       (surface.md, filter.md, sort.md, cluster.md, highlight.md)
  /Nouns/                (feature.md, module.md, requirement.md, dependency.md)
  /Rules/                (composition_rules.md, validation_rules.md, sequence_rules.md)
  /Templates/            (spec_templates.md, module_templates.md, dependency_templates.md, sequence_templates.md, hud_queries.md)
  /SemanticParsingLayer/ (suggestor.md, parser.md)
  /Database/             (spec_database.md)
  /Visualizations/       (semantic_hud.md)   # Unified semantic HUD overlay: gantt chart, dependency graph, kanban, heatmap, timeline, attribute bars, highlights
```

## /SpecVerbs/

### /SpecVerbs/specify.md

**Purpose**: Define a feature.  
**Valency**: 2 (takes a noun like feature/module and optional attrs dictionary).  
**Examples**:  
- `specify(feature("Login"), attrs{priority:"high"})`

### /SpecVerbs/prioritize.md

**Purpose**: Assign priority.  
**Valency**: 1 (takes a target like feature id or list, with priority value in attrs).  
**Examples**:  
- `prioritize(feature("F001"), attrs{priority:"high"})`  

### /SpecVerbs/bundle.md

**Purpose**: Group features into modules.  
**Valency**: 2 (takes features or ids to group, and target module).  
**Examples**:  
- `bundle(features("F001,F002"), module("Auth"))`  

### /SpecVerbs/trace.md

**Purpose**: Follow dependencies.  
**Valency**: 1 (takes attribute like dependencies, with target id in attrs).  
**Examples**:  
- `trace(attribute("dependencies"), attrs{feature_id:"F001"})`  

### /SpecVerbs/validate.md

**Purpose**: Check consistency, coverage.  
**Valency**: 1 (takes attribute like test_coverage or validation_status).  
**Examples**:  
- `validate(attribute("test_coverage"))`  

### /SpecVerbs/simulate.md

**Purpose**: Preview rollout, transitions.  
**Valency**: 1 (takes target like features or modules for simulation).  
**Examples**:  
- `simulate(features("F001,F002"))`  

## /AttributeVerbs/

### /AttributeVerbs/surface.md

**Purpose**: Show selected attributes.  
**Valency**: 1 (takes attribute names to display).  
**Examples**:  
- `surface(attribute("title,priority,status"))`  

### /AttributeVerbs/filter.md

**Purpose**: Constrain features by attribute values.  
**Valency**: 2 (takes attribute and filter values in attrs).  
**Examples**:  
- `filter(attribute("priority"), attrs{value:"high"})`  

### /AttributeVerbs/sort.md

**Purpose**: Reorder by priority, effort, etc.  
**Valency**: 2 (takes attribute to sort by, and order/direction in attrs).  
**Examples**:  
- `sort(attribute("priority"), attrs{order:"desc"})`  

### /AttributeVerbs/cluster.md

**Purpose**: Group by dependencies, modules, risk.  
**Valency**: 1 (takes attribute to cluster by).  
**Examples**:  
- `cluster(attribute("dependencies"))`  

### /AttributeVerbs/highlight.md

**Purpose**: Emphasize risky or critical attributes.  
**Valency**: 1 (takes attribute to highlight).  
**Examples**:  
- `highlight(attribute("risk_level"))`  

## /Nouns/

- **feature.md**: Atomic functionality unit.
- **module.md**: Feature grouping.
- **requirement.md**: Functional/non-functional spec.
- **dependency.md**: References across features.

## /Rules/

### /Rules/composition_rules.md

Rules for how features bundle into modules.

### /Rules/validation_rules.md

Rules for cycles, coverage, consistency checks.

### /Rules/sequence_rules.md

**Workflows**: specify → prioritize → bundle → validate → simulate.  
**HUD-Integrated Sequences**: After any spec::update or spec::remove: Suggest/Run hud_queries.md HUD Automation Chain (templates) for on-demand HUD expansion.  
**Example**: spec::update(priority) → Run HUD Automation Chain with filter("priority_update") → Expand to chain with Kanban highlight.

## /Templates/

### /Templates/spec_templates.md

Templates for features like login, search, checkout.  
**Example Queries**:  
1. Define & prioritize features:  
`specify(feature("Login"), attrs{priority:"high"}) + specify(feature("Search"), attrs{priority:"medium"}) + attr::surface(attribute("title,priority,status"))`  
2. Sort backlog by priority:  
`attr::surface(attribute("id,title,priority,status")) + attr::sort(attribute("priority"), attrs{order:"desc"}) + layout(view("kanban"))`  
3. Trace dependencies:  
`spec::trace(attribute("dependencies"), attrs{feature_id:"F001"}) + attr::cluster(attribute("dependencies")) + layout(view("dependency_graph"))`  
4. Validate coverage:  
`spec::validate(attribute("test_coverage")) + attr::highlight(attribute("validation_status")) + layout(view("heatmap"))`

### /Templates/module_templates.md

Templates for bundles like auth, payment, analytics.

### /Templates/dependency_templates.md

Predefined dependency chains.

### /Templates/sequence_templates.md

Workflow templates.

### /Templates/hud_queries.md

**Purpose**: Compact queries to surface and expand HUD Automation Templates (Shorthand Chains) on-demand, reducing static framework space.  
**HUD Automation Chain**:  
`attr::surface(attribute("hud_chains")) + attr::filter(attribute("change_type"), attrs{value:"{optional_change_type}"}) + attr::sort(attribute("change_type")) + layout(view("kanban"))`  
- Usage: Replace `{optional_change_type}` with e.g., "priority_update" to filter; omit for all chains. Expands to full shorthand chains (e.g., spec::update + highlights + layouts).  
- Data Source: Pulls from Database hud_configs dataset.  
**Notes**:  
- Expansion: Run via semantic parser (e.g., "show HUD templates" → HUD Automation Chain). For full view, chain with `attr::highlight` or other verbs.  
- Extensibility: Update hud_configs dataset to add new chains.  
- Context-Sensitivity: Queries auto-apply based on recent spec changes (link via sequence_rules.md).

## /SemanticParsingLayer/

### /SemanticParsingLayer/suggestor.md

Hints for related features/attributes.

### /SemanticParsingLayer/parser.md

**Parsing Logic**: Natural language → framework ops.  
**HUD Extensions**: Parse/Expand from hud_queries.md (e.g., "show HUD for update" → Run HUD Automation Chain with filter; "view templates" → Run HUD Automation Chain). Suggest based on change detection (e.g., post-update, prompt chain expansion).

## /Database/

### /Database/spec_database.md

**Feature Dataset**:  
Fields: `id, title, description, priority, status, effort, risk_level, dependencies, test_coverage, validation_status`.  
**HUD Configs Dataset**:  
Fields: `id, change_type, chain_script, triggers`.  
- Example Entry: `{id:1, change_type:"feature_addition", chain_script:"specify(feature("{feature_name}"), attrs{priority:"{priority}"}) + attr::surface(...) + ...", triggers:{"kanban":true, "timeline":true, ...}}`  
- Stores compact JSON-like data for queries to expand (e.g., HUD Automation Chain surfaces/formats chain_script).
---

````
