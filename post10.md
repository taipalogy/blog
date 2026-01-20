---
title: '利用影像編輯Framework産生編輯提示'
description: 'image editing framework for editing prompt generation'
date: 2025-03-25
tags: ['prompt', 'framework', 'ai']
image: ""
categories: [""]
authors: ["台灣話專科"]
draft: false
---

Image editing是一種電腦軟體エ³應用。日本話是コㆁ畫像編集，ア中國話是コㆁ影像編輯。Image着是像，畫像，影像，形像等等。치ゥ˜³コㆁ添文字，改色，畫圓箍仔，畫箭頭，改背景等等，ロㆁ是image編輯エ³功能。AI時代エ³image編輯是看ベㇷ¹叫AI做啥乜代志着對AI下提示。피¹喻コㆁ`Add a white flower next to the bottle`，`Remove the watermarks`，`Create an image of a horse.`等等。チッ¹款提示嘛타ㆁ⁷コㆁ是對AIエ³命令。

ラㇴエ³タㆁ²利用提示驅動framework來産生編輯命令。編輯命令エ³文構造基本上着是動詞タゥ²目的語，若有需要コㅗㇷ¹ケ⁷タゥ²一个前置詞エ⁷語組。提示驅動framework嘛是利用動詞カㇷ¹名詞エ³組合來驅動framework，framework着イ動詞차ㇺ³名詞エ³實作カㇷ¹所設定エ⁷規則來産生編輯命令。嘛타ㆁ⁷利用形容詞カㇷ¹副詞來産生コㅗㇷ¹卡詳細エ³文構造ハㇺ³コㅗㇷ¹卡幼路エ³動作。

チッ¹个framework是イ受詞flower為主，所以カ³名詞flower囥띠³動詞add頂高。띠³Framework內底有名詞語組構成規則。イ規則來看，Flowerエ³頭前타ㆁ⁷囥冠詞カㇷ¹形容詞。受詞flower是カㇴ⁷ナ⁷接受動作add做伊エ³動詞。動詞add本身カㇴ⁷ナ⁷是命令形(imperative)，其它屈折形無允准使用。

下脚是利用ChatGPT産生エ⁷prompt。コㅗㇷ¹利用チッ¹个prompt産生編輯命令。影像編輯是用Grokカㇷ¹Gemini來做試驗，現主時カㇴ⁷ナ⁷有簡單エ⁷功能타ㆁ⁷用。


````
---

# Framework for Flower as an Object


```
/PromptFramework/
    /Arguments/
        flower.md
    /Verbs/
        add.md
    /Modifiers/
        article.md
        adjective.md
    /Rules/
        noun_structure.md
        add_flower.md
```

---

### 1. Arguments Folder

- **File**: `flower.md`  
  - **Purpose**: Store options for the noun **flower** and its role as the object in imperative sentences.  
  - **Contents**:  
    ```markdown
    # Flowers
    - flower
    - flowers

    # Object Role
    - The noun **flower** is always used as an object with the verb **add** in the imperative.
    ```

---

### 2. Verbs Folder

- **File**: `add.md`  
  - **Purpose**: Centralized file for the verb **add**.  
  - **Contents**:  
    ```markdown
    # Verb: Add
    - add (valency: 1, imperative)
    ```
  - **Example Templates**:  
    - Imperative: "Add {{object}}."
  
---

### 3. Modifiers Folder

- **File**: `article.md`  
  - **Purpose**: Store indefinite articles **a** and **an**, for singular countable nouns.  
  - **Contents**:  
    ```markdown
    # Articles
    - a (for consonant sounds)
    - an (for vowel sounds)
    ```

- **File**: `adjective.md`  
  - **Purpose**: Store adjectives that can modify the noun **flower**.  
  - **Contents**:  
    ```markdown
    # Adjectives
    - white
    - fragrant
    - beautiful
    - delicate
    ```

---

### 4. Rules Folder

- **File**: `noun_structure.md`  
  - **Purpose**: Define noun phrase construction rules for **flower** and its modifiers.  
  - **Contents**:  
    ```markdown
    # Noun Phrase Construction Rules
    - A noun phrase for flower can consist of:
      - an article + an adjective + a noun (e.g., "a white flower")
      - an article + a noun (e.g., "a flower")
      - a noun (e.g., "flowers")
    ```

- **File**: `add_flower.md`  
  - **Purpose**: Define the rule for using the verb **add** with the noun **flower**.  
  - **Contents**:  
    ```markdown
    # Add Flower Rule
    - **Add** is used imperatively to instruct the addition of a **flower**.
    - It takes **flower** (in singular or plural) as its object.
    - Example: "Add a white flower."
    ```

---
````

直接問AI，看チッ¹个frameworkベㇷ¹アㇴ¹ツァ˜使用:

`How should I prompt to bring up example phrases? Can I just prompt "add"?`

AI着以frameworkエ³内容舉3个例:

```
"Add a flower."
"Add a white flower."
"Add flowers."
```

伊コㅗㇷ¹建議一个撇步:

```
"add + flower" — to focus on singular and plural uses
"add + adjective + flower" — to bring in more descriptive examples
```

リァㇺ⁷ミ⁷カ⁷用看マィ⁷:

`"add + adjective + flower"`

伊隨コㅗㇷ¹舉一クァ例。我コㅗㇷ¹追加一个提問，"add + adjective + flower"是不是一个操作式(operation formula)？我ベㇷ¹アㇴ¹ヌァ指定修飾語カㇴ⁷ナ⁷是花色？:

`Is "add + adjective + flower" an operation formula? How can I specify the modifier to be color only?`

AI産生エ⁷回應有舉二个例:

```
"add + color adjective + flower"
"add + color + flower"
```

頭一个是卡詳細，第二个是卡簡明エ⁷操作式。所以利用操作式`add + color + flower`着得着下脚エ³結果:

```
"Add a white flower."
"Add a red flower."
"Add a yellow flower."
```

## 應用

一个toolbox內底エ³用エ囥足多家私，像摃搥仔，ロ⁷ラィ²バㇷ，피ェㇴ²チㇷ。利用無㒰款エ³動詞，コㅗㇷ¹加上無㒰款エ³受詞，着エ³タㆁ²製造カ⁷キ⁷想ベㇷ¹用エ⁷家私。若是有一个叫做toolboxエ³framework，內底有囥一クァ卡捷用エ⁷家私，隨時ベㇷ¹カ³家私對toolbox內底提出來用着真方便。

像Remove, make, change, replace, create等等動詞，ロㆁエ³用エ對受詞花施加動作。피¹喻コㆁ，カ³花移除，改變花色，カ³花换掉，創一張花エ³影像。コㅗㇷ¹進一步エ³タㆁ²用一个合体動作?來代表幾ナ³个個別エ⁷動作。피¹喻コㆁ用editチッ¹个動作來表示幾ナ³个個別エ⁷動作ロㆁ對受詞花施加一改，可能同時アㇷ³是連續。Editチッ¹个動作着是一个action combo，嘛타ㆁ⁷カ⁷叫做一个macro命令。
