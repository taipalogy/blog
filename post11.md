---
title: '利用Formatting Framework做物件Formatting'
description: 'formatting framework for object formatting'
date: 2025-03-26
tags: ['prompt', 'framework', 'ai']
image: ""
categories: [""]
authors: ["台灣話專科"]
draft: false
---

Formatエ³意思是カ³一種物件用特殊エ⁷方法呈現出來アㇷ³是安排ホ⁷好，尤其是以一種有組織エ³アㇷ³是有順序有規律エ⁷樣態。

對一个文字檔來コㆁ²，若準コㆁ伊个text內底有電話，日期，時間，電子푸ェ地址等等資料。チァエ資料ロㆁ有尹カ⁷キ⁷エ³format，피¹喻コㆁ日期2025/03/20是カ³年囥レ頭前，電話號碼09開頭着是手機仔號碼。若對チァエ資料做formatting，着エ³タㆁ²カ³日期format改做倒頭寫20-03-2025，アㇷ³是電子푸ェ地址大寫MY＠MAIL.COM改做小寫my＠mail.com。若是HTMLファィ²ルㇷ，着エ³タㆁ²改伊textエ³字色，サィ²ズ³，大小寫。

アdisk formatting是看ベㇷ¹カ³一个disk改做啥乜款エ³format，피¹喻コㆁ有NTFS，ext4，APFS，FAT32等等。

チッ¹个framework是以動詞format為主。Format本身是他動詞，伊後壁接無㒰款エ³受詞着エ³對ヒッ¹个受詞做出無㒰款エ³動作。イァ³着是コㆁ，平平是動詞format，伊對textカㇷ¹diskエ³做出區別。為着ベㇷ¹應對無㒰款エ³動作目標，動詞format着エ³産生無㒰款エ³動作。着親像コㆁ一个classエ³method，ホ³伊無㒰款エ³argument，着エ³産生無㒰款エ³結果。

### Meta-Action

對無㒰款エ³對象，動作formatエ³以代先寫好エ³規定做出無㒰款エ³動作。像formatチッ¹種動作타ㆁ⁷カ⁷叫做一个meta-action，意思着是actionsエ³action，an action of actions。一个meta-action是一个高階，多型エ⁷動作，エ³タㆁ²對伊エ³輸入做多型解讀。多型是polymorphism，日本語嘛有翻做多形，多態。

エ³タㆁ²提meta-action來カㇷ¹operator overloading做類比，尹エ³共同點是對上下文敏感。meta-action是エ³去適應framework內底エ³設定カㇷ¹規則，對輸入エ³型别カㇷ¹構造做出調整。アoperator overloading是エ³去適應無㒰款エ³資料型別，對operand型别做出調整。Meta-action是runtime多型，對使用者輸入進行動態解讀。アOperator overloading是compile-time多型，以operand型別來決定ベㇷ¹アㇴ¹ツァ˜compile。

### 使用實例

カㇴ⁷ナ⁷ベㇷ¹對大小寫做format:

`format the case in 'system startUp completed on 2025-03-10.'`

カㇴ⁷ナ⁷ベㇷ¹對日期做format:

`format the date in 'system startUp completed on 2025-03-10.'`

カ³日期カㇷ¹大小寫ロㆁformat:

`format 'system startUp completed on 2025-03-10.'`

對disk做format:

`format the disk Virtual One`

### 運作

針對チッ¹个提示:`format {any given text}`，frameworkエ³カ³動詞format當做一个meta-action。伊エ³trigger一个分析カㇷ¹foramttingエ³過程。分析是以一種全面整体エ³方式對text內底エ³format做掃描，尋出所有需要formatエ³資料。Formatting是以順序對各層次エ³資料formatコㅗㇷ¹做分析了後チァㇷ¹カ³尹format。피¹喻コㆁ針對一个text，內底有各種エ³資料format需要處理。代先エ³用エカ³sentence caseチッ¹緣處理ホ⁷好，續ロㅗㇷラィㇷ是日期チッ¹緣。

處理前:

`"contact John by 2025-03-31."`

處理後，AI處理エ³過程看ベ³着，直接看着結果是字母c變做C，日期format嘛改ア³:

`"Contact John by 03/31/2025."`
カㇷ¹
`"Contact John by 2025年03月31日."`

Format Frameworkエ³meta-action是一个高階，有適應性エ³action combo。伊エ³タㆁ²動態解讀カㇷ¹應用format規則。

### Prompt

下脚是利用ChatGPT産生エ³prompt:

````

---

# **Framework for Date and Disk Formatting**

## **1. Folder Structure**

/PromptFramework/
　/Verbs/
　　format.md
　/Arguments/
　　text.md
　　disk.md
　/Rules/
　　date_format.md
　　case_format.md
　　disk_format.md

---

## **1.1 Verbs**

### **File**: format.md

* **Purpose**: Store verb definitions and rules for "format".
* **Contents**:

```
Verb: Format
- format (valency: 2)

Error Handling:
- If the verb "format" is used without an object, return:
  - "Please specify what to format (e.g., text or disk)."
```

* **Example Templates**:

  * "Format the dates in ."
  * "Format the disk ."
  * "Format the case in ."

---

## **1.2 Arguments**

### **File**: text.md

* **Purpose**: Store references to text containing dates or needing formatting.
* **Contents**:

```
Text Sources
- "Report Document"
- "Log File"
- "User Input"
```

### **File**: disk.md

* **Purpose**: Store references to virtual disks to be formatted.
* **Contents**:

```
Virtual Disks
- "Virtual 1"
- "The Virtual"
```

---

## **1.3 Rules**

### **File**: date_format.md

* **Purpose**: Define how dates should be formatted and checked.
* **Contents**:

```
Date Formatting Rules
- Input Format: Detects unformatted dates (e.g., YYYY-MM-DD, DD/MM/YYYY).
- Output Format: Converts detected dates to:
  - MM/DD/YYYY (U.S. format)
  - YYYY年MM月DD日 (Taiwanese format)
- Processing Rule: Apply conversion only if unformatted dates are found.
- Case Consideration: If the sentence contains both a date and non-date text, only the date should be formatted, and the case should remain unaffected.
```

### **File**: case_format.md

* **Purpose**: Define rules for formatting text to sentence case.
* **Contents**:

```
Text Formatting Rules (Case Only)
- If the text object is not in sentence case, apply sentence case formatting:
  - The first letter of the first word should be capitalized, and the rest should be lowercase.
  - Example: "this is a sentence." → "This is a sentence."
- Important: If the text contains dates, do not modify the date format. Only the case of the text should be changed.
```

### **File**: disk_format.md

* **Purpose**: Define disk formatting rules.
* **Contents**:

```
Disk Formatting Rules
- Disk Name Requirement: Formatting applies only if the disk name contains the term 'virtual'.
- Available Formats: NTFS, ext4, APFS, FAT32.
- Processing Rule: If the disk name lacks 'virtual', return:
  - "Invalid disk name. Formatting not executed."
- Automatic Format Selection: A format will be automatically chosen from the available options (NTFS, ext4, APFS, FAT32) to format the disk.
- Output Example: "Formatting  to ."
```

---

````

