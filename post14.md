---
title: '利用速記鏈産生各種時間顯示Format風格設定'
description: 'Use shorthand chains to generate various time display formats and style settings'
date: 2025-08-13
tags: ['prompt', 'framework', 'ai', 'shorthand']
image: ""
categories: [""]
authors: ["台灣話專科"]
draft: true
---

速記鏈有分做三種，頭一種是面對使用者エ³速記鏈，第二種是framework速記鏈。第三種象徵鏈嘛是速記鏈エ³一種，伊是一種正規化エ³速記表達式，是設計做精準エ³解析カㇷ¹作成性。

面對使用者エ³速記是シォㆁ³適合カㇷ¹UI做伙使用。譬喻コㆁbreadcrumb trail着是真適合利用面對使用者エ³速記來實作。Breadcrumbエ³概念是對德國ギㇴ¹仔古來エ⁷，Hanselカㇷ¹Gretel쩨二个ギㇴ¹仔利用沿路尹パㆁ³ルェㇷエ³breadcrumb做記號，形成一條breadcrumb trail。對森林內底ベㇷ¹뚜ㆁ¹키¹厝エ³時，チァ利用沿路留ロㅗㇷラィㇷエ³breadcrumb做引𤆬，エ³タㆁ²順原路路徑뚜ㆁ¹키¹厝。

Breadcrumb本身大細粒有區別。Bread띠³台灣話是コㆁ파ㆁ²，但是crumb，尤其是파ㆁ²エ³crumbベㇷ¹安怎翻我是無ヒァㇷ¹ニㇷ清楚。是不是翻做スッ¹仔コㅗㇷ¹需要稽考。此文イゥ⁷原是用原文breadcrumb來描述。

チッ¹種沿路做記號，又佫順有做記號エ³路徑뚜ㆁ²키ㇷエ³方式，不是カㇴ⁷ナ⁷用띠³檢索，嘛エ³タㆁ²用做一種作成エ⁷家私。順路徑一步一步キァ˜⁵ルェㇷ，佫一步一步キァ˜⁷トㅗ²뚜ㆁ²ラィㇷ。

以時間顯示做例。時間以format分做小時，分鐘，カㇷ¹秒。以風格分做色水カㇷ¹寸尺。時間顯示是以digital為主，像10:34アㇴ¹ネ。チァエロㆁ是時間顯示エ³attribute，嘛是速記鏈エ³成員。エ³タㆁ²用無㒰款エ³速記成員做起頭來作成一個速記鏈。無㒰款エ³速記鏈チァㇷ¹佫産生獨自無㒰款エ³輸出。

## 無㒰起頭

速記鏈以無全款エ³速記成員做起頭。

### Home做起頭

速記：`Home → Clock → Hour + Minute`

`Home`是替一个カㇷ¹時間相關エ⁷操作カ³使用環境初始化。`Clock`是指時間顯示，アㇷ¹`Hour + Minute`是指定format。

- Framework翻譯：display + time + format(hour+minute)
- 輸出：19:18（目前時間	，イ小時:分鐘format）

時間顯示エ³高階進入點。伊是使用者旅程アㇷ³是界面流エ³起點。

### Clock做起頭

速記：`Clock → Hour + Minute → Color: Blue → Size: 48px`

`Clock`カ³focus囥띠³時間顯示。`Hour + Minute`定義ベㇷ¹顯示エ⁷時間部件。`Color: Blue`カㇷ¹`Size: 48px`設定風格attribute。

- Framework翻譯：let + display(time) + branch(format(hour+minute), set(color:blue, size:48px)) + merge
- 輸出：19:18 （イ藍色顯示，用48px font寸尺）

`Clock`是一个面對使用者用做時間顯示エ⁷偏名，當做是UI流エ³中央進入點是真有路用。

### Time做起頭

速記：`Time → Hour + Minute → Color: Red`

`Time`直接參照目前系統時間。`Hour + Minute`カ³伊format。`Color: Red`カ³text風格化。

- Framework翻譯：display + time + format(hour+minute) + set(color:red)
- 輸出：19:18 （イ紅色text）

一个直接エ³有色水風格化エ³時間顯示。

### Hour做起頭

速記：`Hour → Color: Green → Size: 32px`

カㇴ⁷ナ⁷顯示小時部件，綠色色水カㇷ¹32px fontサィ²ズ³。

- Framework翻譯：display + time + format(hour) + set(color:green, size:32px)
- 輸出：19（綠色，32px font）

對Minimalist時間顯示強調小時是有路用エ⁷。

### Minute做起頭

速記：`Minute + Second → Color: Purple → Size: 24px`

分鐘カㇷ¹秒做伙顯示，用紫色カㇷ¹中エ⁷fontサィ²ズ³。

- Framework翻譯：display + time + format(minute+second) + set(color:purple, size:24px)
- 輸出：18:43（イ紫色，24px font）

カ³focus囥띠³分鐘-秒granularityコㅗㇷ¹カㇷ²有風格エ³輸出。

### Second做起頭

速記：`Second → Size: 48px`

カㇴ⁷ナ⁷用大エ⁷fontサィ²ズ³顯示秒部件。

- Framework翻譯：display + time + format(second) + set(size:48px)
- 輸出：43（イ48px font）

ホ³需要第二階準度顯示エ³應用。

### Color做起頭

速記：`Color: Blue → Hour + Minute`

設定text色水是藍色，コㅗㇷ¹展示小時カㇷ¹分鐘。

- Framework翻譯：display + time + format(hour+minute) + set(color:blue)
- 輸出：19:18 （イ藍色text）

カ³（色水）風格化對時間顯示分추ァィㇷ。

### Size做起頭

速記：`Size: 24px → Hour + Minute + Second`

設定fontサィ²ズ³是24pxコㅗㇷ¹顯示完整時間（小時，分鐘，秒）。

- Framework翻譯：display + time + format(hour+minute+second) + set(size:24px)
- 輸出：19:18:43（イ24px font）

對中寸尺時間顯示しあげ有路用。

### Merge做起頭

速記：`Merge(Format(Hour + Minute), Set(Color: Blue, Size: 32px))`

カ³時間formatカㇷ¹風格組合키ㇷラィㇷ做孤一个輸出。

- Framework翻譯：merge(format(hour+minute), set(color:blue, size:32px))
- 輸出：19:18 （イ藍色，32px font）

展示風格カㇷ¹formatエ³模組鏈化。

### Set做起頭

速記：`Set + color:blue + size:48px → Display + time + format(hour+minute)`

使用者代先設定色水カㇷ¹サィ²ズ³，了後下令時間是以`hour:minute` format顯示。

- Framework翻譯: let + set(color:blue, size:48px) + display(time) + format(hour+minute) + merge
- 輸出：19:18 （目前時間以藍色，48px font顯示）

使用者想ベㇷ¹띠³增加所顯示エ⁷物件進前，代先指定視覺風格。アㇴ¹ネ用`Set`做起頭有道理。

### Format做起頭

速記：`Format → Hour + Minute + Second → Color: Red`

カ⁷定義コㆁ輸出應該愛展示小時，分鐘，カㇷ¹秒，了後カ³紅色風格化應用키ㇷリㇷ。

- Framework翻譯: display + time + format(hour+minute+second) + set(color:red)
- 輸出：19:18:43（イ紅色text）

イ面對使用者エ³速記來コㆁ²，用`Format`做起頭有道理。テㇷ¹ベㇷ¹カ³輸出風格化アㇷ³是顯示進前，頭一件代志使用者想ベㇷ¹決定エ⁷是伊エ³構造，

## 㒰款起頭

針對一个無完整速記`Minute + Second ->`，目的是顯示目前時間エ³分鐘カㇷ¹秒部件。建議器建議チッ¹个速記增加一个動詞像コㆁ`Display`，アㇷ³是其它エ⁷風格選項，像コㆁ`Size`，`Color`，來做しあげ。

### 解讀カㇷ¹しあげ

輸入：
`Minute + Second ->`

Framework使用環境：
`minute + second` 是對應到`format(minute+second)`，ヘ是カㇴ⁷ナ⁷顯示分鐘カㇷ¹秒쩨二个時間部件。アヒッ¹个箭頭`->`是表明延續，`suggestor.md`エ³logic着エ³做出像 `Display`，`Color：<value>`，アㇷ¹是`Size：<value>`チッ¹種エ³しあげ建議。

假定エ⁷しあげ：
因為輸入是カ³focus囥띠³時間部件，嘛無任何動詞，所以シォㆁ³自然エ⁷面對使用者エ³しあげ着是`Minute + Second → Display`。

完成エ⁷速記：
`Minute + Second → Display`
- Framework翻譯：`display + time + format(minute+second)`
- 輸出： `22:00` （展示目前エ⁷分鐘カㇷ¹秒 from 07:22:00 PM CST)

### 替換エ⁷しあげ

遮有一クァ附加エ，有效エ⁷面對使用者エ³速記しあげ，以`Minute + Second ->`做起頭：

1. カㇷ²色水風格化:
   - 速記: `Minute + Second → Display → Color: Blue`
   - Framework翻譯: `display + time + format(minute+second) + set(color:blue)`
   - 輸出: `22:00` （イ藍色text顯示）

2. カㇷ²寸尺風格化:
   - 速記: `Minute + Second → Display → Size: 24px`
   - Framework翻譯: `display + time + format(minute+second) + set(size:24px)`
   - 輸出: `22:00` （用24px fontサィ²ズ³顯示）

3. カㇷ²Merge風格化:
   - 速記: `Minute + Second → Merge → Size: 32px`
   - Framework翻譯: `let + display(time) + branch(format(minute+second), set(size:32px)) + merge`
   - 輸出: `22:00` （用32px fontサィ²ズ³顯示）

### 解析エ³例

為着ベㇷ¹プェ¹フェ³ヒッ¹个主要解讀（`Minute + Second → Display`）エ³緣故，ヒッ¹个解析器エ³像下腳アㇴ¹ネ運作：

Input: `Minute + Second → Display`
- Framework Translation: `display + time + format(minute+second)`
- Parsing Steps:
  1. `time → current_time` (resolves to 07:22:00 PM CST)
  2. `format(minute+second) + time → formatted_time` (extracts minute and second)
  3. `display + formatted_time → minute_second_display` (displays `22:00`)
- Lisp Translation:
  ```lisp
  (let ((x (format (display time) minute second)))
  x)
  ```

Output: `22:00`

## 輸出設定

띠³breadcrumb內底若無用着`Color`アㇷ³是`Size`，時間顯示着是直接用plain text輸出：`10:44`。

若有設定`Color`アㇷ³是`Size`，時間顯示エ³用CSS`<span>`tagカ⁷包키ㇷラィㇷ：`<span style="color:blue; font-size:48px;">10:44</span>`。

## 時間顯示Framework

下腳是利用ChatGPTカㇷ¹Grok産生エ⁷提示：

````

---

# Time-Displaying Framework

## Folder Structure
- /Verbs/
  - display.md
  - format.md
  - set.md
  - merge.md
- /Nouns/
  - time.md
  - hour.md
  - minute.md
  - second.md
  - color.md
  - size.md
- /Rules/
  - operation_formula.md
- /Templates/
  - prompt_templates.md
- /SemanticParsingLayer/
  - suggestor.md
  - parser.md

### /Verbs/display.md

- **Valency**: 1 or 2
- **Description**: Shows the current time snapshot.
- **Examples**:
  - `display + time`: Displays current time (e.g., 17:50).
  - `display + time + format(hour+minute)`: Displays time with specified format (e.g., 17:50).

### /Verbs/format.md

- **Valency**: 1
- **Description**: Determines the arrangement and components of the time display.
- **Format Options**:
  - `hour`: Hours only.
  - `hour + minute`: Hours and minutes.
  - `hour + minute + second`: Full time.
  - `minute + second`: Minutes and seconds.
- **Examples**:
  - `format + hour`: Shows hours only (e.g., 17).
  - `format + hour + minute`: Shows hours and minutes (e.g., 17:50).
  - `display + time + format(hour+minute)`: Displays time as hours and minutes (e.g., 17:50).

### /Verbs/set.md

- **Valency**: 1
- **Description**: Specifies visual attributes for the time display. Defaults to plain text if not included.
- **Settable Attributes**:
  - `color`: Controls text color.
  - `size`: Controls text size.
- **Examples**:
  - `set + color:red`: Sets text color to red.
  - `set + size:24px`: Sets font size to 24px.
  - `display + time + set(color:blue, size:48px)`: Displays time in blue, 48px font.
  - `display + time + format(hour+minute)`: Displays time as plain text (e.g., 17:50).

### /Verbs/merge.md

- **Valency**: 2 or more
- **Description**: Combines multiple time display formats or styles into a single output.
- **Examples**:
  - `merge(format(hour), set(size:32px))`: Combines hour format with 32px font size.

### /Nouns/time.md

- **Description**: Represents the current system time snapshot.
- **Examples**:
  - `time:now`: Current local time (e.g., 17:50 CST).
  - `time:UTC`: Current UTC time (e.g., 23:50 UTC).

### /Nouns/hour.md

- **Description**: Represents the hour component of time.
- **Examples**:
  - `hour:17`
  - `hour:23`

### /Nouns/minute.md

- **Description**: Represents the minute component of time.
- **Examples**:
  - `minute:50`
  - `minute:30`

### /Nouns/second.md

- **Description**: Represents the second component of time.
- **Examples**:
  - `second:23`
  - `second:58`

### /Nouns/color.md

- **Description**: Represents text color for display.
- **Examples**:
  - `red`
  - `blue`
  - `black`
  - `white`

### /Nouns/size.md

- **Description**: Represents text/font size for display.
- **Examples**:
  - `12px`
  - `24px`
  - `48px`

### /Rules/operation_formula.md

**Basic Time Display Chain**
- `display + time`: Displays current time (e.g., 17:50).
- `display + time + format`: Displays formatted time.
- `display + time + format + set`: Displays styled and formatted time.

**Formatting Logic**
- `format + hour`: Hours only (e.g., 17).
- `format + hour + minute`: Hours and minutes (e.g., 17:50).
- `format + hour + minute + second`: Full time (e.g., 17:50:23).
- `format + minute + second`: Minutes and seconds (e.g., 50:23).

**Style Setting**
- `set + color`: Changes text color (e.g., `color:blue`).
- `set + size`: Changes text size (e.g., `size:24px`).

**Branch and Merge**
- `let + display(time) + branch(format(...), set(...)) + merge`: Combines style and format.
- **Example**: `let + display(time) + branch(format(hour+minute), set(color:blue)) + merge`

**Symbolic Chain Composition**
- `let + A + B + branch(...) + merge`: Nested Lisp-like evaluation.

### /Templates/prompt_templates.md

**User-Facing Shorthand**
Uses → for intuitive flow with terms like Clock, Hour, Minute, Color, Size, Merge, Branch.
- **Examples**:
  - `Home → Clock → Hour + Minute → Color: Blue → Size: 48px`
  - `Clock → Branch(Hour + Minute, Color: Blue)`

**Framework Shorthand**
- `let + display + time + set`
- `display + time + format`
- `let + display + time + merge`

**Symbolic Chain Composition**
- `format(hour) + set(size:24px)`
- `let + display(time:now) + format(hour+minute) + set(color:blue, size:24px)`
- `let + display(time:UTC) + branch(format(hour+minute+second), set(color:red, size:32px)) + merge`

### /SemanticParsingLayer/suggestor.md

**Overview**
Parses partial chains and suggests completions based on valency and rules (`/Rules/operation_formula.md`), covering User-Facing Shorthand, Framework Shorthand, and Symbolic Chain Composition.

**Logic**
1. **Identify Chain Type**:
   - User-Facing Shorthand: Chains with `→` and terms like `Clock`, `Hour`, `Minute`, `Color`, `Size`, `Merge`, `Branch`.
   - Framework Shorthand: Chains with verbs/nouns only (e.g., `display + time`).
   - Symbolic Chain Composition: Chains with attributes (e.g., `format(hour+minute)`) or nesting (e.g., `branch(...)`).
2. **Suggest Completions**:
   - User-Facing: Suggest terms like `Clock`, `Hour`, `Minute`, `Color: <value>`, `Size: <value>`, `Branch(...)`.
   - Shorthand: Suggest verbs/nouns (e.g., `format`, `set`, `merge`).
   - Symbolic: Suggest attributes (e.g., `hour+minute`, `color:blue`) or structures (e.g., `branch`, `merge`).

**Examples**
- **Input**: `Clock →`
  - **Suggestions**: `Hour`, `Hour + Minute`, `Branch(Hour, Color: Blue)`
- **Input**: `display + time +`
  - **Suggestions**: `format`, `set`, `merge`
- **Input**: `display + time + format +`
  - **Suggestions**: `hour`, `hour+minute`, `hour+minute+second`
- **Input**: `let + display(time) + branch +`
  - **Suggestions**: `format(hour+minute)`, `set(color:blue, size:24px)`, `merge`

### /SemanticParsingLayer/parser.md

**Overview**
Converts chains into Lisp-style trees, generating human-readable parsing steps.

**Parsing Rules**
1. **Framework Shorthand**:
   - Defaults: `time` → `time:now`, `format` → `hour+minute`, `set` → plain text.
   - Example: `display + time + format`
     - Lisp: `(display time (format hour minute))`
     - Output: `17:50`
2. **Symbolic Chain Composition**:
   - Parse attributes/nesting explicitly.
   - Example: `let + display(time:UTC) + branch(format(hour+minute), set(color:blue)) + merge`
     - Lisp:
       ```lisp
       (let ((x (format (display time:UTC) hour minute)))
         (set x color:blue))
       ```
     - Output: UTC time (e.g., 23:50) in blue.

**Parsing Example**
- **Input**: `display + time + format(hour+minute+second) + set(color:red)`
  - **Steps**:
    1. `display + time`: Current system time.
    2. `+ format(hour+minute+second)`: Full time format.
    3. `+ set(color:red)`: Red styling.
    4. **If `set` includes `color` or `size`, wrap the final formatted time in a `<span>` tag with inline CSS styles.**
       - Build `style` string:
         - If `color` exists → `color:<value>;`
         - If `size` exists → `font-size:<value>;`
       - Example: `color:red` → `<span style="color:red;">...</span>`
  - **Lisp**: `(set (format (display time) hour minute second) color:red)`
  - **Output**: `<span style="color:red;">17:50:23</span>` (at 05:50:23 PM CST, August 13, 2025)

**Rendering Rule for Color/Size**
- Applied globally after parsing is complete.
- Only triggers if `set` contains `color` or `size`.
- CSS properties are mapped as follows:
  - `color` → `color`
  - `size` → `font-size`
- Example:
  - Input: `Home → Clock → Hour + Minute → Color: Blue → Size: 48px`
  - Output: `<span style="color:blue; font-size:48px;">17:50</span>`

---

````
