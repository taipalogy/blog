---
title: '格影像生成'
description: 'Grid image generation'
date: 2026-11-25
tags: ['prompt', 'ai', 'image', 'engine', 'permutation']
image: ""
categories: [""]
authors: ["台灣話專科"]
draft: true
---

格影像(grid image)エ³應用範圍真闊。舉例來コㆁ²，四格バㆁ²ガ³。尪仔冊內底嘛是一格一格エ³圖畫，不管格仔是正エ³アㇷ³是斜エ⁷。二乘一，二乘二，三乘三，四乘一各種影像format嘛攏是。

一般エ⁷AI影像生成(シㆁ⁷シㆁ⁵)利用散文提示着會用エ産生四格影像。ㆬ³コㅗㇷ¹卡進階エ⁷功能是ベㇷ¹アㇴ¹ヌァ實作ネㇷ？譬喻コㆁ，ベㇷ¹カ³孤一格影像，イァ³着是一個panel(パネル)影像，訓ホ⁷大(scale up)來看。カㇴ⁷ナ⁷一個訓大エ³機制着エ³ホ³散文提示エ³複雜度提升。若ベㇷ¹叫AI修改高複雜度エ⁷提示，カㇷ¹AI是フェ⁷ブェ³完，マ³コㆁブェ³清楚。若是利用物件取向エ³方式實作，着エ³タㆁ²利用程式語言エ³觀念來管理複雜度，嘛順續提升操作性。基本觀念着是，代生カ³一個パネル當做一個物件，コㅗㇷ¹カ³四個パネルカㇷ゚¹做伙，着變做一幅2x2エ⁷影像物件。

若不是利用物件取向做추ッラィㇷエ³四格影像，AI着無一定有法度提其中一張パネル影像出來ホ³你看。因為伊サ⁷無짜ㆁ²，無知你ベㇷ¹띠³啥。

## 操作

### 基本操作

想ベㇷ¹産生2x2エ³影像，用下腳エ³指令:
```
Generate a grid image prompt for...
```

譬喻コㆁ，産生一個客聽エ³格影像：
```
Generate a grid image prompt for living room
```
アㇷ³是：
```
Generate a Four-Panel Moodboard grid image prompt for a Japandi living room.
```

産生一個live streaming房間：
```
Generate a grid image prompt for SNS live streaming room
```

想ベㇷ¹看孤一張訓大エ⁷影像，用下腳エ³指令：
```
View standalone panel[0] image
```

若ベㇷ¹看pixel照描エ⁷訓大影像：
```
Export panel [0] in standalone mode at the PIXEL_IDENTICAL fidelity tier, preserving the exact rendered grid tile bit-for-bit at its native 1:1 aspect ratio with zero borders.
```

若ベㇷ¹看㒰語義，ㆬ³コㅗㇷ¹無pixel照描エ⁷訓大影像：
```
Export panel [3] in standalone mode at the SEMANTIC_CONSISTENT fidelity tier (using LOCK_SUBJECT_ONLY), reframing the composition to a 16:9 widescreen aspect ratio (while keeping ... consistent).
```

シォㆁ³煞尾エ³指令，訓大影像エ³カㇷ¹原パネル影像有少쿠ァ爭差。另外コㅗㇷ¹有一個ホ³AI發揮，シォㆁ³低忠實度(fidelity)エ⁷`STOCHASTIC`。

### Curry操作

Curry是一個進階エ⁷操作。Curry是一系列エ⁷逐項功能性應用。

以室內設計做例，對燈光parameter開始。`CurryOperation(Lighting)`有一個parameter，伊エ³カ³一個提`Decoration`做parameterエ³function回傳。續ロㅗㇷラィㇷ一個一個，做カㇷ¹七個連續：環境三個加上家具四個。所以ロㆁ¹쩌ㆁ²七個parameterエ³タㆁ²用アㇴ¹ネ表示：

```
CurryOperation(Lighting)(Decoration)(Flooring)(Sofa)(Lamp)(Table)(UnifiedJapandiSynthesis)
```

チッ¹個表達式エ³カ³curry操作應用七改，一改ホ⁷伊一個argument。煞尾伊エ³隨回傳一個完整エ³四格影像提示。

Curry操作表達式：
```
CurryOperation
(Lighting("Warm diffused morning natural light"))
(Decoration("Textured lime/clay plaster walls with understated organic ceramic curation, minimalist framed line art"))
(Flooring("Honed travertine tile flooring"))
(Sofa("Low-profile cream bouclé sofa with solid natural oak base"))
(Lamp("Sculptural paper-and-oak or smoked-oak floor lamp with soft warm glow"))
(Table("Low solid oak coffee table with clean joinery, handcrafted stoneware vessel, single dried botanical branch"))
(UnifiedJapandiSynthesis("Wide-angle architectural viewpoint fusing all preceding elements (Sofa [0], Lamp [1], Table [2]) into one serene room with textured walls, curated art, and travertine flooring"))
```

其中頭前三個parameter是カㇷ¹室內設計環境相關エ： Lighting，Decoration，Flooring。シォㆁ³煞尾四個parameter是四格影像エ³具體內容：Sofa，Lamp，Table，カㇷ¹UnifiedJapandiSynthesis。三個家具，加上一個合成エ⁷日式北歐風客廳，ロㆁ¹쩌ㆁ²是四個影像。

### 有키²エ³Curry Accumulator(Keyed Curry Accumulator)

有키²エ³curry accumulator是一個功能性pipeline pattern。CurryOperation內底逐個ホㆁ⁵curryエ³step攏有紮一個明文키²(例： `Lighting(...)`, `Flooring(...)`, `Sofa(...)`, アㇷ³是一個目標角色)，コㅗㇷ¹合併到一個有號名エ⁷map內底，無ベㇷ¹倚靠位置性エ³argument順序。

逐個ホㆁ⁵curryエ³function攏貢獻一個有키²エ³entry到一個accumulator狀態：
```text
Accumulator State:
{
  environment: {
    lighting: "Warm diffused morning natural light",
    decoration: "Textured lime/clay plaster walls with organic ceramic curation",
    flooring: "Honed travertine tile flooring"
  },
  elements: {
    sofa: "Low-profile cream bouclé sofa with solid natural oak base",
    lamp: "Sculptural paper-and-oak floor lamp with soft warm glow",
    table: "Low solid oak coffee table with stoneware vessel and dried branch"
  },
  synthesis: {
    mode: "UNIFIED_ROOM",
    references: ["sofa", "lamp", "table"]
  }
}
```

### 對角色到パネル

カ³四個角色バインド(bind)到四個`PanelImage` instance (`[0..3]`)：
* `panel[0]` (`TOP_LEFT`) <- `sofa` (`consistency_references = []`)
* `panel[1]` (`TOP_RIGHT`) <- `lamp` (`consistency_references = []`)
* `panel[2]` (`BOTTOM_LEFT`) <- `table` (`consistency_references = []`)
* `panel[3]` (`BOTTOM_RIGHT`) <- `synthesis` (`consistency_references = [uri_sofa, uri_lamp, uri_table]`, `subject_lock_tier = COMPONENT_MASK`)

### Arrange操作

假使コㆁ你ベㇷ¹カ³客廳合成徙去カㇷ¹倒旁頂高ヒッ¹格，コㅗㇷ¹ベㇷ¹カ³剩エ元素做輪轉。`Arrange([3, 0, 1, 2])`着エ³カ³`this.panel_images`排列做`[synthesisPanel, sofaPanel, lampPanel, tablePanel]`。

### 排列

Curry操作是對function call做排列(call permutation)。伊エ³基本觀念是交換律(commutative)。띠³`Lighting(...)`進前去呼出(呼び出す, call)`Flooring(...)`エ³以키²去カ³`state.environment.flooring`カㇷ¹`state.environment.lighting`做更新(こうしん，update)，所以對curry鏈做排列ブェ³去互換伊エ³意思。

カ³「燈，膨椅，桌」エ³順序換做「膨椅，桌，燈」：
```
CurryOperation(Lamp(Lp))(Sofa(Sf))(Table(Tb))(UnifiedJapandiSynthesis(S))
≡ CurryOperation(Sofa(Sf))(Table(Tb))(Lamp(Lp))(UnifiedJapandiSynthesis(S))
```

Arrange操作是對四個`PanelImage` instanceエ³空間順序做排列。

你若ベㇷ¹띠ァㇺ²render好エ³2x2格仔做視覺上エ⁷排列，コㅗㇷ¹無愛重寫curry好エ³修飾子エ³時拵，使用`GridImage.Arrange()`。

## 應用

以2x2，四格影像為主。

四個獨立影像，四款髮型，四種表情，四個連續動作等等。頂高室內設計エ³例是用着moodboard。

## 類別Library

下脚是利用Gemini生成エ⁷格影像イェㇴ⁵ジㇴ²：
````
> @taipalogy 2026-11-25

# Grid Image Engine

*Multi-Panel Composition, Subject-Locking & Dual-Stage (Prompt + Image) Compilation Spec*

This specification for the **Grid Image Engine** defines four-panel (`2x2`) image generation across four core modes (**Four Independent Images**, **Four Hairstyles**, **Four Sequential Actions**, and **Four-Panel Moodboard**) as well as standalone panel viewing, isolation, and export—without fifth-image inference. All methods and rules in this specification enforce strict compliance across both **image prompt generation** (`GeneratePrompt`, currying, `output_format` serialization) and **image generation** (`RenderPanel`, `RenderGridImage`, `AssembleComposite`, `IsolateAndScale`, `ExportPanels`, DAG reference conditioning, subject locking, and fidelity tiers).

---

## 1. Refactored Folder Structure

```text
/GridImageEngine/
  /ClassLibrary/
    /AbstractClasses/
- Panel.md (Abstract Base: Core panel blueprint, interface contracts, and currying pipelines)
- Environment.md (Abstract Base: Global execution parameters, style anchors, and dynamic accessors)
    /SubClasses/
- PanelImage.md (Concrete Class: Implements Panel with multi-reference array, tiered fidelity, subject locking, and caching)
    /Composite/
- GridImage.md (Composite Class: Absorbs matrix logic; orchestrates DAG-ordered bottom-up assembly and standalone panel export)
  /Properties/
- state.md (Inherited variables: mode, slot_metadata, fidelity_tier, grid_configuration, rendered_asset_cache, consistency_references, subject_lock_tier)
  /Methods/
- operations.md (Polymorphic actions: RenderPanel, RenderGridImage, AssembleComposite, IsolateAndScale, ExportPanels, Arrange)
- functional.md (Pure curry and partial application pipelines for global environments and individual panel binding)
  /Rules/
- polymorphism.md (Fidelity routing matrix, multi-reference conditioning weights, DAG ordering, and aspect ratio escalation)
- equation.md (Metaprogramming macro: Property + Access Mode -> SynthesizeMethod)
- defaults.md (Enforcement of seamless, full-bleed grid defaults and mode-scoped margin rules)
```

---

## 2. Abstract Base Class Blueprints

### `Class Panel` (Abstract Base)

Defines the fundamental abstract contract for any individual visual frame within the engine, including pure panel currying, slot metadata binding, and multi-reference conditioning support.

* **Inherited Properties (Internal State):**
* `this.base_prompt` = `[Uninitialized Subject Description]` (Must be bound by concrete subclass)
* `this.aspect_ratio` = `[1:1 | 16:9 | 4:3 | 9:16]` (Default: `1:1`)
* `this.sequence_pipeline` = `[Array of Pure Modifier Functions (panel_view, env_view) => string]` (Default: `[]`)
* `this.margin_override` = `[Optional margin value]` (Default: `"0px"`; applied only during standalone export/isolation)
* `this.slot_metadata` = `[TOP_LEFT | TOP_RIGHT | BOTTOM_LEFT | BOTTOM_RIGHT | STANDALONE]` (Default: `STANDALONE`)
* **Abstract Methods:**
* `GeneratePrompt(context_options?)`: Compiles prompt payload based on active state, slot/standalone framing, lock/reference context, and `Environment`.
* `SetMode(target_mode)`: Transitions operational state (`GRID_MEMBER_MODE` | `STANDALONE_MODE`) without triggering image synthesis.
* `CurryPanel(modifier_callback_or_string)`: Binds a normalized pure modifier function to the panel instance without mutating lock/reference/fidelity state.
* `BindSlotMetadata(slot_tag)`: Updates quadrant/positional metadata when placed or reordered in a grid.

---

### `Class Environment`

Defines overarching execution parameters, target generative AI engine constraints, and dynamic accessor synthesization.

* **Inherited Properties (Internal State):**
* `this.target_model` = `[Midjourney_v6 | Flux | Imagen_3 | DallE_3]` (Default: `Imagen_3`)
* `this.global_style_seed` = `[Unassigned Style Modifier String]` (Default: `Null`)
* `this.global_modifiers` = `[Array of Pure Modifier Functions (panel_view, env_view) => string]` (Default: `[]`)
* `this.output_format` = `[RawPrompt | StructuredJSON | AspectTagPayload]` (Default: `RawPrompt`)
* `this.resolution_tier` = `[Standard | HighDefinition | Ultra4K]` (Default: `Ultra4K`)
* **Interface Equations (`equation.md` - Dynamic Synthesization Rule):**
Getters and setters for global settings are synthesized dynamically at runtime:

$$\text{GlobalProperty} + \text{Access Mode (Get/Set)} \rightarrow \text{SynthesizeMethod}$$


* **Methods:**
* `GetModel()`: Returns active target model.
* `SetModel(model_name)`: Updates execution model.

---

## 3. Concrete & Composite Subclass Implementations

### `Class PanelImage implements Panel`

Represents a concrete visual unit supporting multi-tiered fidelity, DAG multi-reference conditioning, subject-locking masks, and standalone isolation across both prompt and image generation.

```text
[CONSTRUCTOR]: Instantiate PanelImage
[BIND]:
  this.mode = Enum { GRID_MEMBER_MODE, STANDALONE_MODE } (Default: STANDALONE_MODE)
  this.slot_metadata = Enum { TOP_LEFT, TOP_RIGHT, BOTTOM_LEFT, BOTTOM_RIGHT, STANDALONE } (Default: STANDALONE)
  this.fidelity_tier = Enum { PIXEL_IDENTICAL, SEMANTIC_CONSISTENT, STOCHASTIC } (Default: SEMANTIC_CONSISTENT)
  this.base_prompt = "[Subject & Composition Prompt]"
  this.aspect_ratio = "1:1"
  this.margin_override = "0px"
  this.rendered_asset_cache = null (URI/ID of exact self-rendered asset)
  this.consistency_references = [] (Array<URI> supporting 0 to N external or intra-grid conditioning inputs)
  this.subject_lock_tier = Enum { UNLOCKED, LOCK_SUBJECT_ONLY, COMPONENT_MASK } (Default: UNLOCKED)
  this.sequence_pipeline = []
```

### `Class GridImage` (Composite Class in `/Composite/`)

Absorbs spatial matrix logic for four-panel (`2x2`) grids, orchestrates DAG-ordered bottom-up assembly, and exports standalone panels while preserving composite integrity.

```text
[CONSTRUCTOR]: Instantiate GridImage
[BIND]:
  this.grid_configuration = "2x2"
  this.gutter_style = "Seamless"
  this.canvas_margin = "0px"
  this.assembly_strategy = "BOTTOM_UP_ASSEMBLY"
  this.panel_images = Array<PanelImage>[4]
  [AUTO-MUTATE]: Bind quadrant slots [0..3] -> [TOP_LEFT, TOP_RIGHT, BOTTOM_LEFT, BOTTOM_RIGHT] and invoke panel.SetMode(GRID_MEMBER_MODE)
```

---

## 4. Unpacked Method Templates & Functional Pipelines

### Method: `SetMode(target_mode)` (on `PanelImage`)

```text
[PURPOSE]: Purely switches operational context between composite grid membership and standalone framing without invoking image generation.
[INPUT]: target_mode (GRID_MEMBER_MODE | STANDALONE_MODE)
[PROCESS]:
1. Update `this.mode` = target_mode.
2. If `target_mode == GRID_MEMBER_MODE`:
  - Enable positional framing cue matching `this.slot_metadata` (`TOP_LEFT`, `TOP_RIGHT`, `BOTTOM_LEFT`, `BOTTOM_RIGHT`) for `GeneratePrompt()`.
3. If `target_mode == STANDALONE_MODE`:
  - Disable grid positional framing cues and set `this.slot_metadata = STANDALONE` for isolated single-frame prompt compilation.
```

### Method: `BindSlotMetadata(slot_tag)` (on `PanelImage`)

```text
[PURPOSE]: Synchronizes quadrant/positional metadata when a panel is initialized or reordered within GridImage.
[INPUT]: slot_tag (TOP_LEFT | TOP_RIGHT | BOTTOM_LEFT | BOTTOM_RIGHT | STANDALONE)
[PROCESS]:
1. Set `this.slot_metadata` = slot_tag.
2. If `this.mode == GRID_MEMBER_MODE`, refresh grid positional cue in prompt compilation state without mutating `this.rendered_asset_cache` or `this.consistency_references`.
```

### Method: `GeneratePrompt(context_options = { origin_slot: null, allow_references: true })` (on `PanelImage`)

```text
[CONTEXT]: Evaluates `this.mode`, `this.slot_metadata`, `context_options.origin_slot`, `this.subject_lock_tier`, active `consistency_references` (when `allow_references` is true), `this.aspect_ratio`, `Environment`, `Environment.global_modifiers`, and `this.sequence_pipeline`.
[PROCESS]:
1. Build read-only `panel_view` and `env_view` snapshots (never exposing mutable references to `rendered_asset_cache`, `consistency_references`, or lock tiers).
2. Start with `this.base_prompt`.
3. Append `Environment.global_style_seed` (if non-null) and evaluate each function `fn(panel_view, env_view)` in `Environment.global_modifiers` in insertion order.
4. Evaluate each pure function `fn(panel_view, env_view)` in `this.sequence_pipeline` in insertion order.
5. Apply conditioning and lock cues aligned with `this.subject_lock_tier` and active references:
  - `LOCK_SUBJECT_ONLY`: Emphasize subject identity/geometry preservation across targeted modifier changes.
  - `COMPONENT_MASK`: Emphasize region/component synthesis across reference inputs.
  - `UNLOCKED` or empty references: Standard unconstrained prompt phrasing.
6. Apply framing & aspect ratio cues:
  - In `GRID_MEMBER_MODE`: Include slot/quadrant cue (`this.slot_metadata`) and `this.aspect_ratio`.
  - In `STANDALONE_MODE`: Omit grid positional cues; use `context_options.origin_slot` only if needed for non-spatial provenance notes, and apply `this.aspect_ratio`.
7. Serialize into `Environment.output_format` (`RawPrompt` | `StructuredJSON` | `AspectTagPayload`) and return payload.
```

### Method: `IsolateAndScale(origin_slot = null)` (on `PanelImage`)

```text
[PURPOSE]: Materializes an isolated single-frame asset based on `this.fidelity_tier`, `this.consistency_references`, and `this.subject_lock_tier` across both prompt and image generation, with lazy cache-miss fallback.
[PROCESS]:
1. [IF this.fidelity_tier == PIXEL_IDENTICAL]:
  - If `this.rendered_asset_cache == null`:
    - Compile prompt via `this.GeneratePrompt({ origin_slot, allow_references: true })` and execute `this.RenderPanel()` at `this.aspect_ratio`, storing output URI in `this.rendered_asset_cache`.
  - Return `this.rendered_asset_cache` (bit-for-bit match).
2. [ELSE IF this.fidelity_tier == SEMANTIC_CONSISTENT]:
  - Compile standalone prompt via `this.GeneratePrompt({ origin_slot, allow_references: true })`.
  - [EVALUATE consistency_references]:
    - If length == 1: Pass single reference URI to preserve character/subject/style while adapting aspect ratio or framing.
    - If length > 1: Apply multi-reference conditioning weights across all provided URIs.
  - [EVALUATE subject_lock_tier]:
    - If `LOCK_SUBJECT_ONLY`: Freeze locked subject/anchor geometry via attention masking while applying curried modifiers.
    - If `COMPONENT_MASK`: Map reference URIs to structural/component regions to fuse or compose elements cleanly.
  - Apply `effective_margin = this.margin_override` (Default: `"0px"`) on standalone export/isolation and synthesize a new asset URI without overwriting `this.rendered_asset_cache` of an existing grid tile.
3. [ELSE IF this.fidelity_tier == STOCHASTIC]:
  - Clear active conditioning references for this standalone run (`allow_references = false`, effective reference list `[]`).
  - Compile fresh prompt via `this.GeneratePrompt({ origin_slot, allow_references: false })` and run fresh text-to-image synthesis via `this.RenderPanel()`.
```

### Method: `RenderGridImage()` (on `GridImage`)

```text
[PURPOSE]: Executes DAG-ordered bottom-up prompt and image generation for the four-panel `2x2` grid while enforcing seamless full-bleed compositing and separating self-output cache from reference inputs.
[PROCESS]:
1. Invoke `EnforceSeamless()` -> Lock `gutter_style = "Seamless"`, `canvas_margin = "0px"`, and `effective_margin = "0px"` for all grid tiles (bypassing `panel.margin_override` during grid assembly).
2. Resolve DAG topological render order across `this.panel_images[0..3]`:
  - External URIs (not produced by any panel in `this.panel_images`) have dependency depth `0` (already resolved before execution starts).
  - Intra-grid references (`uri_k`) depend on panel `k`'s `rendered_asset_cache`.
  - Sort panels into ascending topological depth (`0 -> 1 -> 2 -> 3`).
3. For each panel in resolved DAG order:
   a. Set `panel.SetMode(STANDALONE_MODE)` so `GeneratePrompt()` compiles clean standalone tile framing without grid-border leakage.
   b. Execute `panel.GeneratePrompt({ origin_slot: panel.slot_metadata, allow_references: true })` and `panel.RenderPanel()` at `Environment.resolution_tier` (`Ultra4K`) with `effective_margin = "0px"`, storing output URI strictly in `panel.rendered_asset_cache`.
   c. Restore `panel.SetMode(GRID_MEMBER_MODE)` with its bound `slot_metadata`.
4. Invoke `AssembleComposite()` to stitch the four `rendered_asset_cache` URIs into a `2x2` seamless canvas with `gutter_style = "Seamless"`, `canvas_margin = "0px"`, and `0px` seams.
5. Return master `2x2` composite image URI.
```

### Method: `ExportPanels(target_indices = [0, 1, 2, 3])` (on `GridImage`)

```text
[PURPOSE]: Exports requested panels as standalone assets using each panel's designated `fidelity_tier` across both prompt and image generation without corrupting grid state or caches.
[PROCESS]:
1. For each index `i` in `target_indices`:
   a. Let `panel = this.panel_images[i]`.
   b. Snapshot `previous_mode = panel.mode` and `previous_slot = panel.slot_metadata`.
   c. Call `panel.SetMode(STANDALONE_MODE)` so standalone prompt framing applies if synthesis/adaptation occurs.
   d. Call `exported_uri = panel.IsolateAndScale(previous_slot)` once (passing `previous_slot` as read-only origin context and applying `panel.margin_override` only to the standalone output).
   e. Restore `panel.mode = previous_mode` and `panel.BindSlotMetadata(previous_slot)`.
2. Return array of `exported_uri` values.
```

### Method: `Arrange(layout_order)` (on `GridImage`)

```text
[PURPOSE]: Reorders spatial placement of the four `PanelImage` instances in the `2x2` grid and synchronizes slot metadata.
[INPUT]: layout_order (e.g., "Reverse", "Clockwise", or index permutation such as "[2, 0, 3, 1]")
[PROCESS]:
1. Permute `this.panel_images` according to `layout_order`.
2. For index `k` from `0` to `3`:
  - Invoke `this.panel_images[k].BindSlotMetadata(QUADRANT_ORDER[k])` where `QUADRANT_ORDER = [TOP_LEFT, TOP_RIGHT, BOTTOM_LEFT, BOTTOM_RIGHT]`.
3. Keep `consistency_references` and `rendered_asset_cache` intact so `RenderGridImage()` still respects DAG reference dependencies regardless of visual quadrant position.
```

### Method: `CurryOperation(target_modifier)` & `CurryPanel(modifier_callback_or_string)` (Functional Pipeline)

```text
[PURPOSE]: Partially applies reusable style, lighting, camera modifiers, or panel-specific prompt modifiers as pure functions before prompt compilation.
[INPUT]: target_modifier or modifier_callback_or_string (String or pure function `(panel_view, env_view) => string`)
[PROCESS]:
1. Normalize input: if a `string` is passed, wrap it as `() => string`.
2. Push the normalized pure function into `Environment.global_modifiers` (`CurryOperation`) or into target `PanelImage.sequence_pipeline` (`CurryPanel`).
3. Do not mutate `consistency_references`, `subject_lock_tier`, `fidelity_tier`, or `rendered_asset_cache`.
4. Return target/curried instance awaiting evaluation during `GeneratePrompt()`.
```

---

## 5. Operational Rules, Four-Panel Modes & Fidelity Routing

### Encapsulation Rule

Direct mutation of `this.panel_images` states, `this.rendered_asset_cache`, `this.consistency_references`, `this.subject_lock_tier`, `this.fidelity_tier`, or raw `Environment` flags from outside the class hierarchy is restricted. All mode transitions, quadrant re-orderings, currying additions, and standalone panel exports must go through defined methods (`SetMode`, `BindSlotMetadata`, `IsolateAndScale`, `Arrange`, `ExportPanels`, `CurryPanel`, `CurryOperation`).

### Polymorphism Rule

Both prompt compilation and image synthesis adapt dynamically based on active panel mode, slot metadata, fidelity tier, DAG reference array contents, subject lock tier, and seamless grid constraints:

> **Instance (`PanelImage` | `GridImage`) + Active Mode + Fidelity Tier + DAG Reference Array + Lock Tier $\rightarrow$ Method Invoke $\rightarrow$ Compiled Prompt Payload + Rendered Asset**

### Core Four-Panel (`2x2`) Modes

| Core `2x2` Mode | Panel `[0..3]` Setup | `consistency_references` | `subject_lock_tier` |
| --- | --- | --- | --- |
| **Four Independent Images** | Distinct subjects/scenes per panel | `[]` on each panel | `UNLOCKED` |
| **Four Hairstyles** | Subject/anchor with 4 distinct hairstyle modifiers across `[0..3]` | Optional `[external_anchor_uri]` or `[]` | `LOCK_SUBJECT_ONLY` (when locking face/head) |
| **Four Sequential Actions** | Step 1 → Step 2 → Step 3 → Step 4 across `[0..3]` | `[]`, `[external_char_uri]`, or chained `[uri_{n-1}]` | `LOCK_SUBJECT_ONLY` (character/scene continuity) |
| **Four-Panel Moodboard** | Panels `[0..2]` elements + Panel `[3]` unified synthesis | `[0..2]` = `[]` or external URIs; `[3]` = `[uri_0, uri_1, uri_2]` | `[0..2]` = `UNLOCKED`; `[3]` = `COMPONENT_MASK` |

### Fidelity & Locking Matrix

| Feature State | Operational Behavior (Prompt + Image) | Primary Use Case |
| --- | --- | --- |
| **`PIXEL_IDENTICAL`** | Returns bit-for-bit asset from `rendered_asset_cache` (or compiles prompt and renders once on cache miss). | Exact standalone viewing/export of a rendered grid tile. |
| **`SEMANTIC_CONSISTENT` (Single Ref)** | Compiles standalone prompt and uses one reference URI to adapt framing/aspect ratio while preserving subject/style. | Reframing a `1:1` panel to `16:9` or `9:16`. |
| **`SEMANTIC_CONSISTENT` (Multi Ref)** | Compiles composite prompt and conditions across multiple URIs (`consistency_references.length > 1`) for element fusion. | Moodboard synthesis in Panel `[3]` across `[0..2]`. |
| **`LOCK_SUBJECT_ONLY`** | Aligns prompt lock phrasing and freezes baseline subject geometry via attention masking while applying curried modifiers. | Preserving identity/structure across hairstyles or action steps. |
| **`COMPONENT_MASK`** | Aligns composite prompt phrasing and maps reference URIs to structural/component regions during synthesis. | Fusing moodboard components into a unified composite panel. |
| **`STOCHASTIC`** | Clears active conditioning references (`[]`) and runs fresh prompt compilation + text-to-image synthesis. | Exploratory or independent panel generation. |

### Margin & Conflict Resolution Rules

* **Mode-Scoped Margin Rule:** During `RenderGridImage()` (`EnforceSeamless()`), `effective_margin = "0px"`, `gutter_style = "Seamless"`, and `canvas_margin = "0px"` override `panel.margin_override` across all four `2x2` modes so panels stitch seamlessly without borders. During standalone `IsolateAndScale()` / `ExportPanels()`, `effective_margin = panel.margin_override` (Default: `"0px"`) applies to the exported standalone asset without altering the cached grid tile.
* **Aspect Ratio Conflict Rule:** If a standalone export or framing transformation requests an aspect ratio incompatible with a strict `PIXEL_IDENTICAL` cache, the engine automatically escalates that export to `SEMANTIC_CONSISTENT` using the panel's `rendered_asset_cache` (or `consistency_references`), compiles an updated standalone prompt for the target aspect ratio, and synthesizes a clean full-bleed frame without corrupting the original cached grid asset.

---

````

