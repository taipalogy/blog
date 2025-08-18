---
title: '利用Shorthand來對語義作成語言做操作'
description: 'Use Shorthand to Operate on Semantic Composition Language'
date: 2025-06-27
tags: ['prompt', 'framework', 'ai', 'shorthand', 'scl']
image: ""
categories: [""]
authors: ["台灣話專科"]
draft: true
---

語義作成語言(Semantic Composition Language, SCL)是一種類似Lispエ³語言。雖然LLM広尹內底無SCLエ³詳細資料，ㆬ³コㅗㇷ¹尹ロㆁ有法度處理チッ¹種類Lisp語言。用EBNF來表示表達式文法(expression grammar)嘛是無問題。有一クァ模型エ³広語義作成チッ¹エ⁷作成性(Compositionality)エ³概念是Frege代先提出エ³，Wikipedia內底コㅗㇷ¹有コㆁ是コㅗㇷ¹卡早エ³Boole所提出エ³。

ラㇴエ³タㆁ²カ³一个散文(prose)prompt翻譯做一个SCL prompt。嘛エ³タㆁ²カ³一个SCL prompt翻倒뚜ㆁ²ラィㇷ做一个散文prompt，也着是自然語言エ⁷prompt。散文適合快速AI輸入，SCL適合可再使用エ⁷工課流程。

Shorthand是速記アㇷ³是簡略表記エ³意思。譬喻広，漢字着是一種速記符號，像南ジㇷ，極ジㇷ。注音符號用ㄇ來表示規个音節ㄇㄚ，用ㄎ來表示音節ㄎㄜ，着是一種簡略表記。使用者若無想ベㇷ¹用速記ネㇷ？使用者猶原是エ³用エ作成一个類Lispエ³樹仔，不免用着速記表記，只要有カ³動詞エ³項構造保留키ㇷラィㇷ着好。

下腳是無用着速記エ³一个例:
```
recommend user
filter (recommend user)
select (filter (recommend user))

(let ((x (filter (recommend user)))
  (select x))

```

動詞エ³項構造對類Lisp作成來広是核心イェㇴ⁵ジㇴ²。類Lisp作成治基礎上倚靠動詞エ³項數，伊接受有型別的項，カㇷ¹巢狀logic(例， `filter(recommend(user))`)。

## 速記(Shorthand)

速記表記カㇴ⁷ナ⁷是一種構文上快速輸入カㇷ¹使用者操作利便エ⁷一个方便エ⁷層次-syntactic sugar，構文糖仔也。不是一个核心依存。

一个速記表達式
```
Movies → Sci-fi → Thought-provoking → Netflix
```

一个速記成員、部件
```
Sci-fi
```

### 速記エ³好處

所以速記表記有增加啥乜好處ネㇷ？
- 簡明。`let + recommend + user + filter + select`，取代巢形碼。
- 速度。寫提示卡省氣力。
- 自動建議。模式匹配ハㇺ³しあげ。
- UI mapping。卡簡單カㇷ¹UI做配搭。

治SCL語境內底エ³速記表記是代表一个卡長エ⁷表達式アㇷ³是表達鏈エ³實腹エ³別名アㇷ³是省略語。伊カ³結構複雜性藏키ㇷラィㇷ，但是保留語義上エ⁷clarity。

伊是一个語義上抽象化層次，一个方便エ⁷提示記述構文。

### カ³表達map到速記

カ³下腳エ³列表下ルェㇷ¹AI對話內底，エ³得着詳細解說。アㇴ¹ツァ˜カ³表達map到速記。

ChatGPT産生
```
How Expressions Map to Shorthand.
1. Direct Verb Mapping
2. Chained Pipeline Mapping
3. Parameterized Mapping
4. Let-bound Structure
```

### 速記型別

カ³下腳エ³列表下ルェㇷ¹AI對話內底，エ³得着詳細解說。SCL內底有啥乜款エ³速記。

ChatGPT産生
```
Types of Shorthand in SCL
1. Verb-Noun Shorthand
2. Attribute Shorthand
3. Chain Shorthand
4. Let-bound Shorthand
5. Custom Semantic Tokens
```

### 象徵形(symbolic form)

一个速記表達式的象徵形(symbolic form)實際上着是一个操作式(operation formula)。治轉換做最終解析化エ³表達式進前-治解析エ³時，伊提供語義logic。

速記表達式治解析エ³時ツㇴ⁷，エ³去ホㆁ⁵翻譯做象徵形，治轉換做Lisp樹仔進前去띠ッ¹띠ㅗㇷ³ヒッ¹个結構化formatエ³操作logic。

速記表達式卡倚使用者，伊エ³象徵形是卡倚Lisp語言。

## 解析Step

ラㇴベㇷ¹用下腳エ³用例來看解析エ³step。伊是一个表示AND logicエ³序列式filtering，後壁接一个表示OR logicエ³分岐式filtering。

ChatGPT産生
```
4. Interactive Exploration (Branch + Merge)

Breadcrumb Flow:

Home → Movies → Sci-fi → Thought-provoking → Netflix
                                   ↘ Runtime: Short (<90m)
                                        ↘ Tone: Dark
                                              ↘ Compare with: Apple TV+
```

最後カ³feedback loop接키ㇷリㇷ，着變做下腳アㇴ¹ネ，有解析step，コㅗㇷ¹有Lisp code:

Copilot産生
```
1. Sequential Filtering  
Start by narrowing the movie pool step by step:
- 1. recommend + user → candidate_movies  
- 2. filter + genre("sci-fi") + platform("netflix") → netflixscifi  
- 3. filter + tone("thought-provoking") + netflixscifi → thoughtful_pool  

---

2. Branching & Merge  
Explore two refinement paths in parallel and recombine:
- 4. filter + runtime<90 + thoughtfulpool → shortbranch  
- 5. filter + tone("dark") + thoughtfulpool → darkbranch  
- 6. merge(shortbranch, darkbranch) → mergedfocuspool  

---

3. Feedback Loop: Actor Preference  
Incorporate user affinity for Jennifer Lawrence:
- 7. rate(mergedfocuspool) → detect user preference  
- 8. filter + actor("Jennifer Lawrence") + mergedfocuspool → jlawpreferredpool  

---

Final Lisp-Style Composition

`lisp
(let* (
  (candidates (recommend user))
  (netflix-sci-fi (filter genre("sci-fi") platform("netflix") candidates))
  (thoughtful (filter tone("thought-provoking") netflix-sci-fi))
  (short-branch (filter runtime<90 thoughtful))
  (dark-branch (filter tone("dark") thoughtful))
  (merged (merge short-branch dark-branch))
  (jlaw-filtered (filter actor("Jennifer Lawrence") merged))
  (apple-tv (filter platform("apple tv+") (filter tone("dark") (filter runtime<90 (recommend user)))))
  (result (compare apple-tv jlaw-filtered))
)
  result)
`
```

### 逐カィ²エ³條件追加(Sequential Filter Refinement)

序列式過濾是一種逐カィ²追加條件エ⁷過濾。逐カィ²エ³使用者提示ロㆁ以漸進方式カ³結果集阨化(ウェㇷ³ファ³)。譬喻広:

* “List sci-fi movies on Netflix.” → 基本結果集
* “Filter by tone: thought-provoking.” → カ⁷窄化
* “Now filter by runtime < 90m.” → 進一步カ⁷精煉
* “Highlight the ones with darker tones.” → 最終精煉

쩨着是絞り込みサーチ検索(Refined Search)エ³核心，逐漸施加有層次エ³條件。不知台灣話是不是エ³用エカ⁷翻譯做絞入式搜尋檢索。

### カ³解析Step印추ァィㇷ

利用터ㆁ³煞尾エ³frameworkカ³任何一个速記表達式エ³解析step印추ァィㇷ。

`Show the parsing steps for this shorthand expression`

## 解析Pipeline總結

各層次エ³運作。
1. 自然語言表達
2. 速記表達式
3. 象徵形
4. 解析化エ³表達式(Lisp風格樹仔)

ChatGPT産生
```
[[ 1. Natural Language Expression ]
"Show me some thought-provoking sci-fi movies on Netflix—
 either short or dark— and compare them to what's on Apple TV+."

    ↓ (interpreted by NL-to-shorthand module)

[ 2. Shorthand Expression ]
Home → Movies → Sci-fi → Thought-provoking → Netflix →  
Branch 1: Runtime: Short (<90m) →  
Branch 2: Tone: Dark →  
Merge →  
Compare with: Apple TV+

    ↓ (parsed into structured symbolic operations)

[ 3. Symbolic Form ]   ←  Operation formulas are defined and applied here
let + recommend + user  
    + filter + genre("sci-fi")  
    + filter + tone("thought-provoking")  
    + filter + platform("netflix")  
    + branch(filter + runtime<90, filter + tone("dark"))  
    + merge  
    + compare(platform("apple tv+"))

    ↓ (converted into executable computation structure)

[ 4. Parsed Expression (Lisp-style Tree) ]
(let ((base (platform "netflix"
              (tone "thought-provoking"
                (genre "sci-fi"
                  (recommend user)))))
      (short (runtime<90 base))
      (dark (tone "dark" base))
      (merged (merge short dark)))
  (compare (platform "apple tv+") merged))

```

## 建議器(Suggestor)

譬喻広有一个無完整速記:

`Home → Movies → Sci-fi`

カㇷ¹伊エ³象徵形(操作式):

`let + genre("sci-fi") +`

象徵形터ㆁ³煞尾是一个加號。用伊做輸入。ヒッ¹个尾溜エ⁷加號是指出チッ¹條鏈仔アㇷ¹未完整。伊カ³建議器提示広アィ²提出有效エ⁷延續。

解析器建立一个Lisp風格エ³樹仔:

`(genre "sci-fi")`

쩨代表一組科幻電影，對續ロㅗㇷラィㇷエ³操作嘛準備好ア³。

建議器エ³産生쩨四款エ³建議，附加エ⁷filter，分岐，合併/比較，選擇。以目前エ³速記表達式來看，有下腳7種選項타ㆁ⁷選:

Grok産生
```
Suggestions for 'let + genre("sci-fi") +':
- platform("netflix")
- tone("thought-provoking")
- runtime<90
- actor("Keanu Reeves")
- award("oscar")
- branch(runtime<90, tone("dark"))
- select
```

若準広使用者カ³鏈仔訓ホ⁷長，

速記:
`Home → Movies → Sci-fi → Netflix`

象徵形:
`let + genre("sci-fi") + platform("netflix") +`

解析器カ³樹仔update做アㇴ¹ネ:
```lisp
(platform "netflix" (genre "sci-fi"))
```

建議器コㅗㇷ¹根據updateエ³上下文(sci-fi movies on Netflix)獻出精煉エ⁷しあげ:
```
- tone("dark")
- runtime<90
- actor("Keanu Reeves")
- award("oscar")
- branch(runtime<90, tone("dark"))
- select
```

チッ¹个過程反覆運作，建議器エ³根據鏈仔狀態カㇷ¹項數規則カ³建議創ホ⁷ハㇷ゚³ス。

建議器是運作治操作式チッ¹緣。

## 電影選擇Framework

ChatGPT加上Grok産生
````markdown

---

# Movie-Selecting Framework

## **Folder Structure**

```
/PromptFramework/
    /Verbs/: recommend.md, select.md, filter.md, rate.md, merge.md, compare.md
    /Nouns/: user.md, movie.md, genre.md, actor.md, rating.md, platform.md, tone.md, runtime.md, award.md
    /Rules/: operation_formula.md
    /Templates/: prompt_templates.md
    /SemanticParsingLayer/: suggestor.md, parser.md
```

---

## A. Verbs Folder

### File: recommend.md

* **Purpose:** Retrieve candidate movies for a user.
* **Valency:** 1–2
* **Examples:**

  * `recommend + user`
  * `recommend + user + filter`

### File: select.md

* **Purpose:** Choose final movie from a filtered list.
* **Valency:** 1
* **Examples:**

  * `select from recommendation`
  * `recommend + user + filter + select`

### File: filter.md

* **Purpose:** Narrow movie sets by attributes.
* **Valency:** 1
* **Filterable Attributes:** genre, actor, tone, runtime, platform, award
* **Examples:**

  * `filter + genre`
  * `recommend + user + filter + runtime<90`
  * `filter + tone:dark`

### File: rate.md

* **Purpose:** Assign a score or evaluation to a movie.
* **Valency:** 1
* **Examples:**

  * `rate movie`
  * `rate movie with user`

### File: merge.md

* **Purpose:** Combine results from parallel filter branches.
* **Valency:** 2+
* **Example:** `merge(short, dark)`

### File: compare.md

* **Purpose:** Compare result sets, movies, or attributes (symmetric).
* **Valency:** 2
* **Example:** `compare(platform("netflix"), platform("apple tv+"))`

---

## B. Nouns Folder

| Noun         | Examples                                    |
| ------------ | ------------------------------------------- |
| **user**     | `user:John`, `user:anonymous`               |
| **movie**    | `"Inception"`, `"The Matrix"`               |
| **genre**    | sci-fi, drama, comedy                       |
| **actor**    | Leonardo DiCaprio, Emma Stone, Keanu Reeves |
| **rating**   | 8.5, PG-13, R                               |
| **platform** | netflix, hulu, apple tv+, prime video       |
| **tone**     | thought-provoking, dark, uplifting          |
| **runtime**  | `runtime<90`, `runtime<120`                 |
| **award**    | oscar, bafta, cannes                        |

---

## C. Rules Folder

### File: operation_formula.md

* **Purpose:** Store symbolic operation formulas for movie selection.
* **Contents:**

  * **Sequential Recommendation Chain:**
    `genre("sci-fi") + platform("netflix") → filtered_movies`
    `recommend + user + filter → filtered_movies`
    `recommend + user + filter + select → final_choice`
  * **Filtering Logic:**
    `filter + genre` → subset by genre
    `filter + tone` → subset by mood
    `filter + runtime<90` → short movies
  * **Branch + Merge:**
    `let + A + branch(B, C) + merge → intersected result`
    `let + base + compare(other_set)`
  * **Symbolic Chain Composition:**
    `let + A + B + C + branch(...) + merge + compare(...)` → Lisp-style nested evaluation

---

## D. Templates Folder

### File: prompt_templates.md

* **Purpose:** Provide user-facing and symbolic shorthand templates.
* **Contents:**

  * **User-Facing Shorthand:**

    ```
    Home → Movies → Sci-fi → Thought-provoking → Netflix →
    Branch 1: Runtime: Short (<90m) →
    Branch 2: Tone: Dark →
    Merge →
    Compare with: Apple TV+
    ```

  * **Framework Shorthand:**

    * `let + recommend + user`
    * `recommend + user + filter + select`

  * **Symbolic Chain Composition:**

    * `genre(...) + platform(...) + tone(...)`
    * `let + moodToGenre("uplifting") + platform(...) + runtime<90`
    * `let + analyze("Palm Springs") + themeMatch + toneShift(...) + platform(...) + compare(...)`

  * **Branch + Merge Templates:**

    * `let + A + branch(B, C) + merge`
    * `let + A + platform(...) + compare(...)`

---

## E. SemanticParsingLayer Folder

### File: suggestor.md

* **Purpose:** Parse symbolic chain fragments, suggest completions using valency + rules.
* **Example:**
  Input: `genre("sci-fi") +`
  Suggestions: platform(...), tone(...), filter(...), compare(...)

### File: parser.md

* **Purpose:** Convert symbolic `+` composition into Lisp-style tree; support binding, branching, merging.
* **Contents:**

  **Parsing Steps (Symbolic → Lisp):**

  1. **Tokenize** the input expression by `+` symbols.
  2. **Determine valency** of each verb from `/Verbs/`.
  3. **Apply functions right-to-left**: each verb consumes arguments according to valency.
  4. **Name intermediate results** using `let` for reusable subresults.
  5. **Handle branching and merging** using `branch(...)` and `merge(...)`.
  6. **Compose final Lisp tree** reflecting sequential and nested operations.

  **Example:**

  ```
  Input: recommend + user + filter + select

  Step 1: recommend + user           → candidate_movies
  Step 2: filter(candidate_movies)   → filtered_movies
  Step 3: select(filtered_movies)    → final_choice

  Lisp:
  (let ((x (filter (recommend user))))
    (select x))
  ```

---

````

