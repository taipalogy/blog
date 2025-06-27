---
title: '英語文解析'
description: 'English sentence parsing'
date: 2025-1-29
tags: ['english', 'ai']
image: ""
categories: [""]
authors: ["台灣話專科"]
draft: false
---

Tree-based parsing是以樹構造為主エ³解析，基於樹エ⁷解析。若是照字面來翻着是樹基解析，伊是一種構文解析エ³技術。Build是起造、構築、構建、建構、建造エ³意思。若ベㇷ¹カ³一个文轉換做解析樹，エ³タㆁ²叫AIカ³ヒッ¹エ⁷文解析做單語アㇷ³是語組，イァコㅗㇷ¹ウ³主語、目的語、動詞、名詞、形容詞、前置詞、副詞等等エ³構文單位（syntactic units）。ラㇴベㇷ¹使用エ⁷提示エ³用得カ³文轉換做構文單位，コㅗㇷ¹利用構文單位來起構文樹（syntax tree）カㇷ¹依存graph（dependency graph）。アナ³Parsingカㇷ¹起樹エ³過程着無ベㇷ¹詳細解說，イㇴ⁷ㆬ³不是本文エ³重點。使用者需要做エ³カㇴ⁷ナ⁷是輸入一个文，AI着エ³カ³構文樹エ³diagram畫추ッラィㇷ。

利用ChatGPTカ³提示추ァㇴ⁷ホ⁷好，像下腳アㇴ¹ネ：

````
---
## Examples

### Sentence Example 1

**Input**: *"The combination of a pencil and imagination resulted in a story."*

1. **Tree-Based Parsing**:
```
ROOT: resulted  
  ├── SUBJECT: combination  
  │   ├── MODIFIER: the  
  │   ├── MODIFIER: of a pencil and imagination  
  ├── PREPOSITIONAL_PHRASE: in a story
```

2. **Stanza (Dependency Parsing)**:
```
- *resulted*: root  
- *combination*: nsubj (subject of *resulted*)  
- *the*: det (determiner of *combination*)  
- *pencil*: nmod (modifier of *combination*)  
- *imagination*: conj (conjunct of *pencil*)  
- *story*: pobj (object of *in*)  
- *a*: det (determiner of *story*)  
- *in*: case (preposition)
```
---
````

ラㇴ先來看頭一个文，"Take it." 翻做台語着是提키ㇷ。AIエ³産生下腳エ³解析結果：

---
### 1. **Tree-Based Parsing**  
```
ROOT: Take  
  ├── OBJECT: it  
```

### 2. **Stanza (Dependency Parsing)**  
```
- *Take*: root  
- *it*: obj (object of *Take*)  
```  
---

續ロㅗㇷラィㇷ又コㅗㇷ¹是一个命令文，マ³是一个語組動詞（phrasal verb），"Sit down."：

---
### 1. **Tree-Based Parsing**  
```
ROOT: Sit  
  ├── ADVERBIAL: down  
```

### 2. **Stanza (Dependency Parsing)**  
```
- *Sit*: root  
- *down*: advmod (adverbial modifier of *Sit*)  
```  
---

續ロㅗㇷラィㇷ是一个複合名詞，"Team Taiwan"：

---
### 1. **Tree-Based Parsing**  
```
ROOT: Team  
  ├── MODIFIER: Taiwan  
```

### 2. **Stanza (Dependency Parsing)**  
```
- *Team*: root  
- *Taiwan*: nmod (modifier of *Team*)  
```  
---

"Taiwan"是"Team"エ³修飾語。

續ロㅗㇷラィㇷ是一个複合動詞，"習い始めました"，翻做台語是開始學エ³意思，翻做英語是"I began to learn."，アㇷ³是"I have started to learn."：

---
### **1. Tree-Based Parsing**  
```
ROOT: 始めました  
  ├── OBJECT: 習い  
```

### **2. Stanza (Dependency Parsing)**  
```
- *始めました*: root  
- *習い*: obj (object of *始めました*)  
```
---

伊産生エ³解析結果是カ³始めました當做ROOT。我カ⁷キ⁷키Stanzaエ³網站查，用㒰一句"習い始めました"做輸入，結果伊スァㇷ¹コㆁ習いチァㇷ¹是ROOT。所以對AI産生エ⁷解析結果コㅗㇷ¹有需要チㇺ⁷チォㇰエ³所在。

續ロㅗㇷラィㇷ是一个文，"I wrote a mail to her." 翻做台語是我寫一張푸ェホ⁷イ⁷：

---
### **1. Tree-Based Parsing**  
```
ROOT: wrote  
  ├── SUBJECT: I  
  ├── OBJECT: a mail  
  │   ├── MODIFIER: a  
  ├── PREPOSITIONAL_PHRASE: to her  
```

### **2. Stanza (Dependency Parsing)**  
```
- *wrote*: root  
- *I*: nsubj (subject of *wrote*)  
- *mail*: obj (object of *wrote*)  
- *a*: det (determiner of *mail*)  
- *her*: obl (oblique object of *wrote*)  
- *to*: case (preposition for *her*)  
```  
---

續ロㅗㇷラィㇷ是一个敘述文，"I am John."：

---
### **1. Tree-Based Parsing**  
```
ROOT: am  
  ├── SUBJECT: I  
  ├── COMPLEMENT: John  
```

### **2. Stanza (Dependency Parsing)**  
```
- *am*: root  
- *I*: nsubj (subject of *am*)  
- *John*: xcomp (complement of *am*)  
```  
---

其中"am"是一个連繫動詞。

續ロㅗㇷラィㇷマ³是一个敘述文，"He is coming."，翻做台語是伊ベㇷ¹來エ³意思：

---
### **1. Tree-Based Parsing**  
```
ROOT: coming  
  ├── SUBJECT: He  
  ├── AUXILIARY: is  
```

### **2. Stanza (Dependency Parsing)**  
```
- *coming*: root  
- *He*: nsubj (subject of *coming*)  
- *is*: aux (auxiliary verb for *coming*)  
```  
---

其中"is"是一个助動詞。我叫AIカ³チッ¹エ⁷文做變形，"Can you transform the sentence?"。伊有一クァ形態變化타ㆁ⁷揀。我カ⁷コㆁ我ベㇷ¹띠³否定形，伊無ベㇷ¹來，像下腳アㇴ¹ネ：

---
### 1. **Negative Form**:
   - **Input**: *"He is not coming."*

   **Tree-Based Parsing**:
   ```
   ROOT: coming  
     ├── SUBJECT: He  
     ├── AUXILIARY: is  
     ├── NEGATION: not
   ```

   **Stanza (Dependency Parsing)**:
   ```
   - *coming*: root  
   - *He*: nsubj (subject of *coming*)  
   - *is*: aux (auxiliary verb for *coming*)  
   - *not*: neg (negation of *coming*)
   ```
---

續ロㅗㇷラィㇷマ³是一个有歧義性(ambiguity，曖昧性)エ³敘述文，"The man saw the woman with the telescope."。翻做台語是，ヒッ¹エ⁷查甫用ヒッ¹エ⁷望遠鏡看ヒッ¹エ⁷查某，アㇷ³是ヒッ¹エ⁷查甫看着一个查某有ヒッ¹エ⁷望遠鏡：

---
### 1. **Interpretation 1: The man used the telescope to see the woman.**

1. **Tree-Based Parsing**:
```
ROOT: saw  
  ├── SUBJECT: man  
  │   ├── MODIFIER: the  
  ├── OBJECT: woman  
  │   ├── MODIFIER: the  
  ├── PREPOSITIONAL_PHRASE: with the telescope
```

2. **Stanza (Dependency Parsing)**:
```
- *saw*: root  
- *man*: nsubj (subject of *saw*)  
- *woman*: dobj (direct object of *saw*)  
- *the*: det (determiner of *woman*)  
- *telescope*: pobj (object of *with*)  
- *with*: prep (preposition introducing the phrase)
```
---
### 2. **Interpretation 2: The man saw a woman who had the telescope.**

1. **Tree-Based Parsing**:
```
ROOT: saw  
  ├── SUBJECT: man  
  │   ├── MODIFIER: the  
  ├── OBJECT: woman  
  │   ├── MODIFIER: the  
  ├── PREPOSITIONAL_PHRASE: with the telescope
```

2. **Stanza (Dependency Parsing)**:
```
- *saw*: root  
- *man*: nsubj (subject of *saw*)  
- *woman*: dobj (direct object of *saw*)  
- *the*: det (determiner of *woman*)  
- *telescope*: nmod (modifier of *woman*)  
- *with*: prep (preposition introducing the phrase)
```
---

續ロㅗㇷラィㇷマ³是一个有受動態エ³文，"The cake was eaten by the child."，翻做台語是雞卵糕ホ³ギㇴ¹仔食키ㇷ：

---
1. **Tree-Based Parsing**:
```
ROOT: eaten  
  ├── AUXILIARY: was  
  ├── SUBJECT: cake  
  │   ├── MODIFIER: the  
  ├── AGENT: child  
  │   ├── MODIFIER: the  
  ├── PREPOSITIONAL_PHRASE: by
```

2. **Stanza (Dependency Parsing)**:
```
- *eaten*: root  
- *cake*: nsubj (subject of *eaten*)  
- *was*: aux (auxiliary verb for *eaten*)  
- *child*: agent (agent performing the action)  
- *the*: det (determiner of *cake* and *child*)  
- *by*: prep (preposition introducing the agent)
```
---

雞卵糕是主語，ㆬ³コㅗㇷ¹チッ¹エ⁷食エ⁷動作是ギㇴ¹仔做エ³。
