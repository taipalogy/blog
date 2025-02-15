---
title: '提示驅動Framework紹介'
description: 'introduction to prompt-driven framework'
date: 2024-12-29
tags: ['prompt', 'framework', 'ai', 'translation']
image: ""
categories: [""]
authors: ["台灣話專科"]
draft: false
---

提示驅動Frameworkエ³英文是Promp-Driven Framework。一般來コㆁ²，アㇴ¹ネ翻是無問題。日本話是コㆁ¹プロンプト駆動フレームワーク。英語エ³driven是被動形。

カ⁷ChatGPTムㆁ³コㆁ：
``` 

So we don't express the passive form of driven in the construction of プロンプト駆動フレームワーク? 

``` 

ChatGPT應コㆁ：
``` 

Correct! In the construction プロンプト駆動フレームワーク (puronputo kudō furēmuwāku, prompt-driven framework) in Japanese, the passive form of "driven" is not explicitly expressed. Instead, 駆動 (kudō) is used, which is an active noun form meaning "driving" or "drive". 

``` 

Prompt-driven翻做台語是「ホ³提示驅動エ⁷」，「提示驅動エ⁷」，或者是「被提示驅動的」。被ジㇷ用띠³漢語或者是書面語，無ヒァ捷用。Prompt-driven framework翻做ホ³提示驅動エ⁷framework，是シㅗ¹쿠ァロㅗ⁷ソㅗ，ㆬ³コㅗㇷ¹イ文法來コㆁ²是正確エ³。アㇷ¹コㅗㇷ¹提示驅動Framework是一个卡簡明エ⁷表達。另外一種表達是提示驅動型Framework。因為ケ⁷一个型ジㇷ，意思カㇷ¹prompt-driven frameworkマ³シㅗ¹쿠ァ有爭差。

Frame是框エ³意思。Work是穡頭、카ㆁ⁷쿠ェ³エ³意思。Framework對台灣話來コㆁ²是新エ⁷概念，看ベㇷ¹アㇴ¹ツァ˜翻做台灣話，マ³타ㆁ⁷直接用外來語表達着好。

提示驅動型framework是カ³動詞エ³項構造（トㆁ³ス⁵エ³ハㆁ³キㅗ¹쩌ㅗ⁷，動詞の項構造，the argument structure of a verb）用做概念エ⁷模型，チォㆁ³一个動作カㇷ¹伊所需要エ³輸入是アㇴ¹ツァ˜形成一貫エ³提示定義ホ⁷好。Folder構造提供一个實用エ⁷，組織テㇰエ³層次，カ³概念エ⁷模型用code實作。

提示驅動型framework是カ³動詞エ³項構造（トㆁ³ス⁵エ³ハㆁ³キㅗ¹쩌ㅗ⁷，動詞の項構造，the argument structure of a verb）用做概念エ⁷模型，チォㆁ³一个動作カㇷ¹伊所需要エ³輸入是アㇴ¹ツァ˜形成一貫エ³提示定義ホ⁷好。Folder構造提供一个實用エ⁷，組織テㇰエ³層次，カ³概念エ⁷模型用code實作。イ物理性カ³動詞file，項file，規則file安排ホ⁷好，反映추⁷띠³下腳エ³語言學原則，コㅗㇷ¹確保clarity，maintainability，カㇷ¹scalability。

## 詳細解說


### 提示驅動Framework（總体概念） 

提示驅動Framework是結構テㇰエ³，概念エ³方法，動作カㇷ¹指令エ³引炁一个系統エ³logicカㇷ¹流動。

* 提示ツㇴ指令：Frameworkエ³核心機制是提示直譯－高階，對人友善エ⁷指令アㇷ³シ³template。
* Flexibilityカㇷ¹Modularity：系統成長エ³時ツㇴ⁷，マ³エ³タㆁ²ホ³無㒰款エ³提示合併，適應，extend。

### 動詞エ³項構造（語言エ³設計圖） 

提示驅動手路エ³下腳是一種カ³逐个提示ロㆁ¹理解做是一个似文構造エ³idea。

* 動詞代表核心動作アㇷ³シ³處理方法。
* 項是去ツㇴ做ヒァエ動詞所定義エ⁷，需要エ³角色。

쩨有反映語言學エ³理論。逐个動詞指定伊ベㇷ¹띠³啥乜款エ³項。所以，動詞エ³項構造提供一个概念エ³ scaffolding，타ㆁ⁷確定frameworkエ³提示是一貫エ³，有意義エ⁷，有系統エ³。

### Folder構造（物理テㇰエ³組織） 

Folder構造是你アㇴ¹ツァ˜カ³你エ³codeカㇷ¹資源띠³碟仔頂高イ實体性カ⁷組織키ㇷラィㇷ。カ³概念エ⁷模型イ有形エ⁷方式做反射。伊拍算エ³カ³動詞，項，規則，templateロㆁ分ホ⁷開。

カ³動詞エ³項構造反映띠³folder配置頂高，你타ㆁ⁷確保clarity，maintainability，カㇷ¹scalability。

### 三者エ³相互作用 

* 概念エ⁷模型（動詞エ³項構造）：カ³動作カㇷ¹輸入之間エ⁷關係定義ホ⁷好，確保一个logicエ³，ホ³語言學啟發エ³系統。
* 組織テㇰエ³方法（Folder構造）：띠³物理上，カ³概念エ⁷模型提ラィㇷコㅗㇷ¹カ⁷實施ロㅗㇷ키ㇷ。逐个folderカㇷ¹fileエ³配置ロㆁエ³カ³動詞エ³項構造加強，ホ³伊卡簡單navigateカㇷ¹理解。
* Framework手路（ホ³提示驅動エ⁷）：提供一个總体哲學。提示驅動Frameworkカ³動詞エ³項構造leverage做伊エ³引炁理論，而且倚靠folder構造，イ清楚，エ³extendチッエ³樣態來カ⁷實作추ッラィㇷ。

## カㇷ¹傳統エ³framework有啥乜爭差

### 傳統framework

四常是依賴hardcodeエ³アㇷ³シ³代先compile(好)エ³構造去産生輸出。卡無flexibility，修改키ㇷラィㇷ嘛真厚工。

### 提示驅動型framework

卡親像타ッ¹카ㆁエ⁷系統，其中提示エ³引炁過程，ホ³伊卡有適應性，嘛卡好extend。

## 比較

用ChatGPT對提示驅動型frameworkカㇷ¹傳統framework做比較。ChatGPT認為提示驅動型framework띠³쩨六方面ロㆁ卡贏：

1. 行為エ³動態カㇷ¹靜態。
2. Modularityカㇷ¹再使用性。
3. Flexibilityカㇷ¹客製化。
4. 互動驅動型開發。
5. Scalibility 
6. 跨領域應用。

## 實時調整カㇷ¹使用者驅動型互動エ³特點

* 動態造句。實時調整カㇷ¹使用者輸入カ³提示エ³動的選擇カㇷ¹組合直接驅動키ㇷラィㇷ 
* 實時Feedback Loop。倚靠frameworkエ³能力去接受使用者エ³feedback，調整輸出，實時カ³イㇴ⁷refine。
* 上下文應對。使用者驅動エ⁷互動ホ³framework띠³across turnsエ³記띠ッ¹使用者エ³choice，維持連續性カㇷ¹一貫性。
* Validation。實時檢查使用者輸入，看カㇺウ³띠ㆁ⁷タ˜⁵アㇷ³シ³ラゥ²カゥ(譬喻コㆁ，項無키ㇷ)，確保即刻feedbackカㇷ¹修正。

## 使用方式有兩種

一種是整合式。framework是外部module。提示對framework動態産生出來，チァㇷ¹コㅗㇷ¹サ⁷過去AIヒァ處理。Frameworkイゥ⁷ウァㇴ⁷有獨立性，AI利用伊エ³輸出創作추ッ¹回應。

一種是嵌入式。Frameworkエ³logicカㇷ¹開講系統融合做フェ²。AI模型띠³開講session內底ホ³framework引炁カㇷ¹現現キㅗ³。提示，規則，カㇷ¹templateロㆁ深入整合띠³會話エ³流動內底。

## カㇷ¹傳統Framework共同運作 

エ³タㆁ²ホ³複數エ³提示驅動型Framework做フェ運作。マ³エ³タㆁ²カㇷ¹傳統型framework做フェ運作。

## 總結

提示驅動型Framework是타ㆁ⁷同時ツㇴ做： 
* 一个人類カㇷ¹AI之間エ³溝通介面。
* 為着ベㇷ¹反復實驗エ³一个實時調整機制。
* 使用者互動引炁系統進化エ³一个方法論。

提示驅動型Framework不是カㇴ⁷ナ⁷一个人類AI互動エ³介面，一个實時ホ³使用者驅動エ⁷調整手段，而且是互動驅動型開發エ³基石。逐方面攏建立띠³㒰款エ³基礎原則頂高。提示イ直接動態カㇷ¹使用者做中心エ³方式去引炁系統エ³行為。ホ³framework對短期エ³使用需求カㇷ¹長期エ⁷開發feedback loop做出回應。

所以チッ¹文章エ³內容大部份ロㆁ算コㆁ是AI産生エ，無問題。現子時AIイァㇷ¹無法度應對アㇷ³シ³回應台灣話エ⁷提示。我利用英語來カㇷ¹AI互動，結果産生一个算コㆁ是人カㇷ¹AIエ³共同創作추ッラィㇷエ³提示驅動型framework。台語書寫띠³處理、表達外來語チッ¹方面，イァ¹コㅗㇷ¹需要下足多精神カㇷ¹功夫ラィ⁷做改進。文章內底有用着英文エ³所在着是以外文エ³形式來表現。

## Hello World 

下腳是一个エ³印出"Hello, world."エ³提示驅動framework。伊타ㆁ⁷ツㇴ做一个起點，只要カ⁷copy過你エ³AI模型ヒァ，着エ³タㆁ²開始用ア⁷。

````markdown
# **Prompt-Driven Framework for Hello-World Outputs**

---

## **Framework Structure**

### **1. Components**
- **Verb**: The action or greeting used to initiate the phrase.
- **Argument**: The entity being addressed or referenced.
- **Punctuation**: The specific punctuation that concludes the phrase.
- **Code Format**: (Optional) Wraps the output in programming or markup syntax.

---

### **2. Rules**
The **Rules file** describes how to combine these prompts based on the grammatical structure, ensuring that the combinations form a meaningful output.

---

## **Framework Implementation**

### **Folder and File Structure**
```plaintext
/Framework/
    /Prompts/
        verb.md
        argument.md
        punctuation.md
        code_format.md
    /Logic/
        rules.md
    /Examples/
        basic_examples.md
```

---

### **1. Prompts**
Each **prompt** defines a **role** and contains relevant information for that role.

- **`verb.md`**:
  ```markdown
  # Action: Hello
  ```
  
- **`argument.md`**:
  ```markdown
  # Subject: World
  ```

- **`punctuation.md`**:
  ```markdown
  # Type: Terminal
  - Options: !, ., ?
  ```

- **`code_format.md`** (New):
  ```markdown
  - Python: `print("{{verb}} {{argument}}{{punctuation}}")`
  - C: `printf("{{verb}} {{argument}}{{punctuation}}");`
  - HTML: `<h1>{{verb}} {{argument}}{{punctuation}}</h1>`
  ```

---

### **2. Rules**
The rules define how to combine the components into valid outputs.

- **`rules.md`**:
  ```markdown
  # Message Structure
  - `{{verb}} {{argument}}{{punctuation}}`

  # Constraints
  - Ensure proper spacing and capitalization.
  - Apply style variations or code formatting when specified.
  ```

---

## **Key Concepts**

### **1. Verb as Method**
The **verb** is analogous to a method that defines the “action” and what kinds of arguments it needs.

### **2. Arguments as Objects**
The **arguments** are like objects or values passed into that method, fulfilling the roles defined by the verb.

### **3. Composition as Function Execution**
**Composition** substitutes the arguments into the verb’s “template” to produce a complete, working message.

---

## **Output Rules**
Using this framework, the following outputs are valid:
1. `Hello World!`
2. `Hello, world.`
3. `Hello World?`

---

## **Guidelines for Extension**

### **1. Adding Punctuation**
Introduce new terminal punctuation marks:

- **`punctuation.md`**:
  ```markdown
  # Role: Punctuation
  - Type: Terminal
  - Options: !, ., ?, ...
  ```
- **New Outputs**:
  - `Hello World?`
  - `Hi, world...`

---

### **2. Adding Styles**
Allow for formatting variations such as uppercase, lowercase, or title case:

- **`rules.md`** (Updated):
  ```markdown
  # Rules for Styles
  - Uppercase: HELLO WORLD!
  - Lowercase: hello world.
  - Title Case: Hello World.
  ```
- **New Outputs**:
  - `HELLO WORLD!`
  - `hello world.`

---

### **3. Programmable Outputs**
Generate outputs in programming or markup formats:

- **`code_format.md`**:
  ```markdown
  # Role: Code Format
  - Python: `print("{{verb}} {{argument}}{{punctuation}}")`
  - C: `printf("{{verb}} {{argument}}{{punctuation}}");`
  - HTML: `<h1>{{verb}} {{argument}}{{punctuation}}</h1>`
  ```
- **Examples**:
  - Python: `print("Hello World!")`
  - C: `printf("Hello World!");`
  - HTML: `<h1>Hello World!</h1>`

---

## **Examples**

### **Basic Examples**
- `Hello World!`
- `Hello, world.`
- `Hello World?`

### **Formatted Examples**
- Uppercase: `HELLO WORLD!`
- Lowercase: `hello world.`
- Title Case: `Hello World.`

### **Programmable Examples**
- Python: `print("Hello World!")`
- C: `printf("Hello World!");`
- HTML: `<h1>Hello World!</h1>`
````

### 實腹版

若想ベㇷ¹띠³一个卡實腹エ³版本，エ³タㆁ²カ³ChatGPT提示コㆁ：

"Generate a compact, fully functional version of the Hello-World framework without tutorials or guidelines—just the core folder structure, prompts, and rules for quick implementation."

### frameworkエ³執行

カ³Hello-World framework貼クェㇷ了後，用下腳エ³提示ホ³伊執行：

"Execute the Hello-World framework."

アㇷ³シ³カ⁷ムㆁ⁷コㆁ

"How can I interact with the framework?"
