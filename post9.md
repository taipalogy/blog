---
title: '利用文作成framework産生單文'
description: 'sentence composing framework for sentence generation'
date: 2025-03-24
tags: ['prompt', 'framework', 'ai']
image: ""
categories: [""]
authors: ["台灣話專科"]
draft: true
---

文作成エ³意思着是sentence composing，イァ³着是作文。動詞Compose有作詩，作曲エ³意思。ラㇴベㇷ¹用文作成framework來解說提示驅動framework是アㇴ¹ツァ˜運作エ³。ラㇴ所ベㇷ¹作エ³文是英文エ⁷`"A {person} carries a {bag}."`。利用チッ¹个構文（sentence structure）
來作文，所産生エ⁷文嘛뚜¹ア¹好是例文。

提示驅動framework是以動詞エ³項構造コㅗㇷ¹加上folder構造來實現エ⁷，動詞カㇷ¹項ベㇷ¹アㇴ¹ツァ˜互動嘛寫띠³規則内底。テカㇷ¹AI互動エ³時ツㇴ⁷，若ベㇷ¹對AI做提示，他動詞需要目的語（受詞）來執行一个動作，自動詞着無需要目的語。피¹喻コㆁ，我定定對AI下エ⁷提示是英文`Show an example`，其中"show"是他動詞，"an example"是直接目的語。AI看着チッ¹句`Show an example`着エ³カ³一个例輸出ホ³使用者看。

㒰款嘛是對AI做提示。チッ¹个文作成framework利用英文`Compose a sentence`來作一个固定エ⁷構文`"A {person} carries a {bag}."`。㒰款"compose"是他動詞，"a sentence"是直接目的語。AI看着チッ¹句`Compose a sentence`，着エ³カ³一个例文輸出ホ³使用者看。피¹喻コㆁ，`"A man carries a briefcase."`，意思是一个查甫紮一个かばん。

下脚是利用ChatGPT産生エ⁷prompt:
````
---

# **Sentence Composing Framework**  

## **1. Folder Structure**  
```
/Framework/  
  ├── /Verbs/  
  │     ├── compose.md  
  ├── /Arguments/  
  │     ├── sentence.md  
  ├── /Rules/  
        ├── sentence_structure.md  
```

---

## **2. Action Verbs**  

### **compose.md**  
- **Purpose:** Composes a grammatically correct sentence by replacing placeholders and ensuring proper structure.  
- **Valency:** **1** (Transitive, requires only the object **sentence**).  
- **Usage:**  
  - **Input:** `"Compose a sentence."`  
  - **Process:**  
    - Executes the **sentence composing steps** as defined in `/Arguments/sentence.md`.  
  - **Output:** A randomly generated complete sentence (either basic or extended structure).  

---

## **3. Sentence Composing Arguments and Execution Steps**  
**File:** `/Arguments/sentence.md`  

```markdown
# Sentence Argument  

## **Allowed Action Verb**  
- **compose** (Exclusively allowed)  

## **Sentence Structures**  
1. **Basic Structure:**  
   `"A {person} carries a {bag}."`  

2. **Extended Structure (with optional item):**  
   `"A {person} carries a {bag} with {something} inside."`  

## **Arguments:**  
- `{person}` → Options: **Woman, Man, Child, Traveler, Farmer**  
- `{bag}` → Options: **Backpack, Briefcase, Handbag, Messenger bag, Shopping bag**  
- `{something}` → Options: **Documents, Laptop, Groceries, Camera, Toys**  

## **Execution Steps:**  
1. **Parse:** Identify `{person}`, `{bag}`, and `{something}` (if applicable).  
2. **Evaluate:** Retrieve values (e.g., `"traveler"`, `"messenger bag"`, `"book"`).  
3. **Generate:**  
   - Randomly select **either the Basic Structure or the Extended Structure** without depending on the availability of `{something}`.  

## **Example Sentence Outputs:**  
- **Basic:** `"A traveler carries a messenger bag."`  
- **Extended:** `"A traveler carries a messenger bag with a book inside."`  
```

---

## **4. Rules**  
**File:** `/Rules/sentence_structure.md`  

```markdown
# Sentence Structure Rules  

1. When the phrase "compose a sentence" is used, generate **one** of the following sentence structures randomly:  
   - **Basic Structure:** `"A {person} carries a {bag}."`  
   - **Extended Structure:** `"A {person} carries a {bag} with {something} inside."`  

2. `{something}` is **optional**, but the sentence structure will be chosen randomly, regardless of whether `{something}` is provided.  

3. A bag **may or may not contain items**.  
```

---
````

下脚是一クァ使用エ³例。チァエ³例ロㆁ有띠ァㇺ²ChatGPTハㇺ³Grok頂高試過。

피¹喻コㆁ，輸入
`Compose a sentence.`
得着結果:

ChatGPT:
```
A farmer carries a shopping bag.
```
Grok:
```
A traveler carries a briefcase with documents inside.
```
輸入
`Compose 3 sentences.`
得着結果:

ChatGPT:
```
1. A traveler carries a backpack.  
2. A child carries a handbag with toys inside.  
3. A farmer carries a messenger bag.
```
Grok:
```
A woman carries a handbag with a camera inside.  
A man carries a messenger bag with a laptop inside.  
A child carries a backpack with toys inside.
```
輸入
`Compose a sentence for duffle bag.`
得着結果:

ChatGTP:
```
A man carries a duffle bag.
```
Grok:
```
A traveler carries a duffle bag with a laptop inside.
```
輸入
`Compose 2 sentences for scientist.`
得着結果:

ChatGTP:
```
1. **Basic:** "A scientist carries a briefcase."  
2. **Extended:** "A scientist carries a briefcase with documents inside."  
```
Grok:
```
A scientist carries a briefcase with documents inside.  
A scientist carries a backpack with a laptop inside.
```

## Carryカㇷ¹Bag

英文carry翻做台語是짜ㇷ。Carry着是不管物件是安ヌァ짜ㇷ，不管是파ィ˜⁷エ⁷，クァ˜⁷エ⁷，モ³エ³，只要是짜ㇷ²レ身軀着是carry。

ア英文bag一般台語是コㆁ카⁷バㆁ²アㇷ³是袋仔。카⁷バㆁ²是對日本話エ³かばん（鞄）來エ⁷。英語內底各種無㒰款エ³bag是真多，若ベㇷ¹一个一个翻做台語是シゥ˜⁷クェ²フィ²키³，目前ロㆁ是直接以原文呈現。

## 排列組合

ラㇴ若想ベㇷ¹問AIコㆁ`person`カㇷ¹`bag`有グァ³多無㒰款エ³排列組合，

`What are the combining permutations of "person + bag"?`

以framework內底エ³內容來コㆁ²，`person`有5个選項，`bag`有5个選項。5乘5着是25个。

## 應用

任何一个文，一篇文，不管是長文，短文，文章，ブログ文，퍼⁷文，發文，廢文，論文，URL，只要其中有需要改變エ³語詞アㇷ³是句段，ロㆁエ³タㆁ²用チッ¹種方法來産生你需要エ³構文。像`"A {person} carries a {bag}"`チッ¹个構文，內底エ³`{person}`カㇷ¹`{bag}`是placeholder，着是需要改變エ³所在。AI圖內底若有ベㇷ¹添文字키ㇷリㇷエ³所在嘛是エ³タㆁ²用チッ¹个方法。
