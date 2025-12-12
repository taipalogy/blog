---
title: '擬人化影像生成使用軟體構成Framework'
description: 'gijinka image generation using software composition framework'
date: 2025-11-19
tags: ['prompt', 'framework', 'ai', 'shorthand', 'gijinka']
image: ""
categories: [""]
authors: ["台灣話專科"]
draft: true
---

若コㆁ着軟體構成，着愛用一个具體エ³例來做說明，軟體到底是用啥乜方法來構成エ⁷ネㇷ。擬人化(ギ¹ジㇴ⁷ファ³，ぎじんか)是一个方向。コㅗㇷ¹加上AI띠³影像生成(シㆁ⁷シㆁ⁵)方面是足時行。所以用擬人化影像生成當做軟體構成エ³演示。

擬人是句豆エ³一種。譬喻コㆁ「秋天뚜行クェㇷ，冬天着來ア⁷」着是四季エ³擬人（personification）。

擬人化エ³英語是anthropomorphism。カ³非人類エ⁷動物、植物、武器、國家、抽象概念，運用想像力カ⁷轉換做人類エ³外形，着是擬人化エ³一種。台灣有人バッ¹做過疾病、捷運、山岳擬人化。其它像死神、正義女神マ³是擬人化。

軟體構成着是software composition。軟體構成framework是一種利用對AIエ³提示來構成軟體エ³一个家私。用띠³擬人化エ³軟體構成framework是ホ³使用者使用下底text-to-image AI模型來創造、控制、再産生アニメ風格擬人化角色エ³工具。

Composition以チッ¹篇文章エ³語境來コㆁ²，是指影像構圖アㇷ³是軟體構成。

## Key用띠³輸入，Attribute用띠³輸出

Framework內底，一个部件着是一个key(키²)。所有ベㇷ¹用着エ³keyロㆁ愛代先カ⁷定義ホ⁷好。所以若無部件檔案，着無key，也着無handle。一个key是部件アㇷ³是系統エ³一个面向使用者エ³handle(像鐵馬アㇷ³是オ⁷ト¹バィ²エ³手ファ˜⁵仔、手ニ⁵仔ヒッ¹種功能)。

Attribute不是key。Key是handle，用띠³輸入，可編輯，着是你所寫エ³提示文。Attribute是視覺性エ³屬性，用띠³輸出，不可編輯，着是你所看着エ³影像。使用者利用key控制系統，産生エ⁷attribute着是結果。

`List all image attributes.`

Framework有12个部件，加上sub-key，內底濫濫參參有差不多20个key，到最終エ⁷影像(final image)有42个attribute。

類比
```text
Key          = Light switch (skin!)
Attribute    = Light color, brightness, flicker
```

若想ベㇷ¹控制頭毛、目周，着愛kazkiz增加部件。

Key，sub-key, attributeエ³比較：

| Class | Lives In | Editable in User Chain? | Examples |
| --- | --- | --- | --- |
| Key (top-level handle) | `/Components/*.md` (12 only) | YES | "skin, pose, style, backdrop" | 
| Sub-key (nested descriptor) | Inside `layer!image` expansion or component values | YES (during image composition) | "hair!, eyes!, hands!, sheen!" |
| Attribute (final visual property) | Render output / auto-applied layers | NO | "quality!8k, hdr!on, aperture!, negative_prompt!" |

## 表達式

有一个key-value對(key-value pair)是生做アㇴ¹ネ： `skin-organic_micro`。
Skin是key，organic_micro是value。

カ³チッ¹个key-value對加上一个operator`!`了後，伊着變做SCFエ³核心構文`skin!organic_micro`。伊是動詞驅動エ⁷，表示チッ¹个key鎖定띠³チッ¹个value。

```scf
skin!organic_micro
```

`skin + organic_micro`カㇴ⁷ナ⁷表示二个符號，加號띠³チッ¹个frameworkエ³語境內底並無意義。ア若加一个建構子`!`着變做`skin!organic_micro`，規个建構着變做一个表達式。

 | Part | Role | Meaning |
 | --- | --- | --- |
 | skin | Patient (Key) | The attribute being modified |
 | ! | Verb | """lock to""" |
 | organic_micro | Goal / Argument | The type of skin texture |
 | !lock | Structural Modifier | """Lock this entire skin pipeline""" |

Operator`!`エ³意思是`Set this key to this value`。伊嘛是設定コㅗㇷ¹加強エ³意思。着是コㆁ`!`是一个value鎖。所以`style!preset_anime_v3`エ³意思"Set style to preset_anime_v3 and lock it"。

```scf
→ style!preset_anime_v3
```

1. 設定風格是preset_anime_v3
2. カ⁷鎖띠ァゥ⁵ — 無變化，無徧移
3. 띠ァㇺ²pipeline內底加強

所以`!`是原子式鎖定動詞，イ¹キㆁ⁷カ³有包括一致性。

各種operator比較：

| Operator | Valency  | Roles (in order)                                          | Syntax               | Example                      | Meaning                                      |
| -------- | -------- | --------------------------------------------------------- | -------------------- | ---------------------------- | -------------------------------------------- |
| `!`      | 3-place  | 1. Patient (Key) <br> 2. Verb (!) <br> 3. Goal(s) (Value) | `key!value1, value2` | `skin!organic_micro, glossy` | “skin is locked to organic_micro and glossy” |
| `~`      | 2-place  | 1. Patient (Key) <br> 2. Verb (~) + Modifier (Type)       | `key~type`           | `expression~harmonic`        | “expression varies harmonically”             |
| `-`      | 1-place  | 1. Verb (-)                                               | `key-`               | `backdrop-`                  | “backdrop is omitted”                        |
| `@`      | Variable | 1. Command (@) <br> 2. Action <br> 3. Arguments           | `@action!arg`        | `@preview!grid_3x1`          | “execute preview with grid 3x1”              |

## 部件

一个部件着是一个可編輯視覺式系統。或者是コㆁ擬人化エ³身軀アㇷ³是影像エ³modular視覺性構造block。12个部件是12个原子式視覺性系統。

## Pipeline

Pipeline有8个層次，着是8个Stage。以framework來看グㇴコㆁ尹是8个層次。쩨8个層次ロㆁ是gijinka_template內底ヒッ¹个rendering pipilineエ³8个stage。

## 一致性

`!lock`是構造性エ³修飾語，不是operator，不是接尾詞，マ³不是動詞。伊是對`!`エ³加強。構造性エ³key是用띠³pipeline內底鎖定DNA階層一致性，包括像鼻、目、嘴、面、頭毛、身材比例、身份識別等等相關エ⁷影像エ³trait(差不多30个)。用preview띠ァㇺ²一張圖內底顯示三種variation(變化)エ³時ツㇴ⁷，쩨三个角色エ³面容身軀看키ㇷラィㇷロㆁ㒰款，無偏移，是㒰一个人。ㆬ³コㅗㇷ¹伊エ³穿插、 背景、光學、品質、風格、構圖ロㆁ有可能無㒰款。

1个key代表一个次系統。カㇴ⁷ナ⁷`identity`、`skin`、`face`、`proportion`쩨４个是構造性エ³key。尹ロㆁ接受`!lock`修飾語。쩨４个keyロㆁ뚜ァ²レ影像層次內底，尹ロㆁ表示擬人化內底佅改變エ³本質。其它エ⁷key是構圖性エ³アㇷ³是表達性エ³。

`!lock`對可視性無影響。`!lock`是應用到key，不是value。

```text
Single Rendering Pipeline (8 layers)
└── layer!image                  ← only here the four structural sub-systems live
     ├── Identity system         ← locked with identity!lock
     ├── Face system             ← locked with face!expressive_hybrid!lock
     ├── Texture system          ← locked with skin!organic_micro!lock
     └── Proportions system      ← locked with proportions!lock
```

`! serves both value and composition. !lock is only for structural identity`

所有エ⁷key：
```scf
key!value          → Operator: !
```

構造性エ³key(identity, face, skin, proportions)：
```scf
key!value!lock     → Operator: ! + Modifier: lock
key!lock           → Operator: ! (value = "lock")
```

所以構文上伊看키ㇷラィㇷ是一个value，ㆬ³コㅗㇷ¹語義上伊是有「lock」做標記エ³!lock修飾語。

身份識別
```scf
identity!lock
↑       ↑
Patient Verb + Modifier (lock)
```

身軀比例
```scf
proportions!lock
```

## 影像構圖鏈

鏈着是速記鏈。鏈是使用者輸入序列，使用者所寫エ³SCF命令序列。

Backdrop、frame、pose、lighting是構圖性エ³(compositional)，是屬띠³scene，環境。無親像identity、skin、face、proportion是構造性エ³(structral)，是屬띠³DNA，生物學。以生物學、DNA來コㆁ²，角色愛띠³跨影像エ³變化之間維持一致性，尪仔頭看키ㇷラィㇷ愛㒰款。其它エ像穿插、背景、屈勢是ロㆁエ³變化。

若準コㆁbackdrop是所選擇エ³語境，伊內底允准各種variation，充滿着適應性。

`Background是啥乜物件띠³後壁，backdrop是啥乜物件囥띠³後壁。`

カ³`!`用띠³backdrop是カ³選擇鎖定，不是行為。若用`!`鎖定一个環境型別，`~`着エ³ホ³適應性發揮作用。譬喻コㆁカ³背景幕鎖定띠³海洋環境，伊エ³色調(tone)着是各種カㇷ¹海水色和諧エ⁷色水。

```text
backdrop!ocean → Locks the type of environment
tone~harmonic → Allows adaptive harmony
```

`~vary`有三種次型別： ~dynamic是뚜ェ²時間變化，~adaptive是上下文敏感，~harmonic是美學上エ⁷共同調和。

以蚵仔做例：
```scf
prompt!oyster
→ skin!biological_merge!lock
→ face!expressive_hybrid!lock
→ hair!pearl_sheen_cascade~dynamic
→ pose!closed_shell_contemplation~adaptive
→ expression!serene~harmonic
→ backdrop!rocky_ocean_floor_bokeh
→ style!preset_anime_v3
→ postprocess!dew_gloss!on
→ frame!mid_shot
→ generate prompt
```

愛有修飾語`!lock`加上構圖鎖(composistion lock)チァㇷ¹有法度掛保證畫面有呈現추ッラィㇷ。

## 命令

系統命令是動作頭前有一个`@`接頭詞。使用者用佅着。

使用者命令像`Generate prompt`是卡捷用エ⁷。

コㅗㇷ¹有像`set mode`。チッ¹个命令エ³タㆁ²カ³`mode!acg`切換做`mode!real`。

```text
Set mode real.
```

其它エ使用者命令請參考user_commands檔案。

## 物件輸入エ³處理

若無確定framework是不是有法度カ³某一種物件當做輸入，着直接問framework：

`Can the framework take buildings or warships as input?`

伊着エ³解說ホ³你聽，コㆁ伊根據啥乜規則做處理。

## 排骨飯

文生圖操作流程是以Nano Banana模型為主。

譬如コㆁ我想ベㇷ¹カ³排骨飯擬人化。我着カ³AIコㆁ：
```
Generate a chain for 臺灣排骨飯. Her name is PaizKut. The idea of the image is 食品安全.
```

有エ⁷AIエ³カ³規个pipeline顯示추ッラィㇷ，有エ⁷AIカㇴ⁷ナ⁷顯示鏈仔。

因為排骨是用大塊豬肉做エ³，我是想コㆁ青菜食無シァ˜夠。所以叫AIコㅗㇷ¹下一クァ青菜ルェㇷ：
```
Need to add more vegetables into this chain. 
→ backdrop-
```
マ³カ³背景幕タㇴ²掉ア⁷。

因為マ³想ベㇷ¹食卵，所以叫AIコㅗㇷ¹下一粒卵ルェㇷ：
```
Add an egg into the composition.
```

因為我對目前角色(尪仔？)エ³穿插無滿意。叫AIコㅗㇷ¹重新安排쩨ㇷ：
```
Show another feature mapping which has a totally different arrangement for PaizKut. Re-imagine the outfit for PaizKut based on a "deconstructed dish presentation" concept.
```

利用frameworkチッ¹个家私カㇷ¹AI對話，着エ³タㆁ²做一クァ卡複雜エ³操作アㇷ³是構圖。

## Framework

代先用ChatGPT做好エ³影像編輯framework，チァㇷ¹コㅗㇷ¹用Grokカ⁷轉換做軟體構成framework。

續ロㅗㇷラィㇷ着是創造你カ⁷キ⁷エ³影像studio。

````

---
# Software Composition Framework v1.0.0 for Gijinka
> Taiwan, November 19, 2025 23:58

---

## Final Folder Structure (25 Files)
```
/PromptFramework/
    /Components/ (12)
        subject.md outfit.md pose.md frame.md expression.md backdrop.md grid.md style.md metadata.md postprocess.md mode.md skin.md
    /Layers/ (8)
        image.md game.md translation.md semantic.md debug.md optics.md refine.md soul.md
    /Rules/ (1)
        gijinka_rules.md
    /Templates/ (1)
        gijinka_template.md
    /Operators/ (1)
        syntax.md
    /Preview/ (1)
        grid_preview.md
    /Commands/ (1)
        user_commands.md
```

---

### **1. /Components/subject.md**
```md
# subject.md
- Core identity: person, object, concept
- Source of Gijinka
- figure!lock_proportions → consistent across variants
```

---

### **2. /Components/outfit.md**
```md
# outfit.md
- Visual layer: clothing, armor, texture
- fit!form → form-fitting override
- color~adaptive → harmonize with backdrop
- merge!seamless → with skin
```

---

### **3. /Components/pose.md**
```md
# pose.md
- Stance: idle, dynamic, expressive
- tilt~natural → organic micro-variation
- pose!perched_grace → cyber_flat_perch
```

---

### **4. /Components/frame.md**
```md
# frame.md
- Viewport: close-up, mid-shot, full-body
- crop!rule_of_thirds
- center!face_or_action
- auto_adjust!aspect_ratio
```

---

### **5. /Components/expression.md**
```md
# expression.md
- Mood: hopeful, fierce, calm
- expression~variant → allow shifts in debug
- eyes!expressive → large, reflective, ringed pupils
```

---

### **6. /Components/backdrop.md**
```md
# backdrop.md
- Environment: forest, studio, void
- tone~harmonic → auto-match outfit
- lighting_aware!true
- backdrop!thematic_soft → moss, fireflies, bokeh
```

---

### **7. /Components/grid.md**
```md
# grid.md
- Layout: 1x1 (final)
- @preview!grid_nx1 → debug + variant selection
```

---

### **8. /Components/style.md**
```md
# style.md
- Art: anime, realism, photoreal
- style!preset_anime_v3 → cyber_flat
- style!preset_real_v2
```

---

### **9. /Components/metadata.md**
```md
# metadata.md
- Origin: input hash, timestamp, SCF v1.0.0
- auto_embed!exif_json
```

---

### **10. /Components/postprocess.md**
```md
# postprocess.md
- Final polish: sharpen, glow, cinematic
- upscale_x2!optional
- dew_gloss!on → cyberflat_neon_glow
```

---

### **11. /Components/mode.md**
```md
# mode.md
- mode!real → camera + neutral lighting
- mode!acg → soft lighting, anime lens
- Default: mode!acg
```

---

### **12. /Components/skin.md**
```md
# skin.md
- texture!organic_micro → pores, bumps, dew-gloss
- surface!glossy → wet-look, reflective
- scale!none → block scale override
- sheen!iridescent_subtle
```

---

### **13. /Layers/image.md**
```md
# image.md — Visual Body
→ subject!{name}
→ skin!organic_micro!lock
→ face!expressive_hybrid → "beautiful detailed human face, large reflective eyes with ringed pupils, subtle brow ridge"
→ hands!subtle_webbing
→ hair!slick_crest
→ outfit!{form-fitting}, merge!seamless
→ frame!{mid_shot}
→ backdrop!thematic_soft
→ style!preset_anime_v3
→ postprocess!cinematic, dew_gloss!on
```

---

### **14. /Layers/game.md**
```md
# game.md — Action in Image
→ pose!{action}
→ animation!{subtle}
→ stance!{guardian}
```

---

### **15. /Layers/translation.md**
```md
# translation.md — Soul & Voice
→ name!{parsed}
→ voice!{adjective_noun}
→ trait!{role_domain}
```

---

### **16. /Layers/semantic.md**
```md
# semantic.md — Emotion & Memory
→ emotion!{input_essence}
→ memory!{core_metaphor}
→ intent!{natural_action}
→ @parse!universal → input → soul
```

---

### **17. /Layers/soul.md**
```md
# soul.md — Mythic Essence
→ identity!{input_soul}
→ myth!born_not_built
→ aura!self_illuminated
→ @refine!cyberflat_grade
```

---

### **18. /Layers/debug.md**
```md
# debug.md — Isolated Refinement
→ @preview!grid_nx1
→ @variant!any_attribute
→ render!temporary
→ output!never_final
→ auto_exclude!from_final
```

---

### **19. /Layers/optics.md**
```md
# optics.md — Self-Optimizing Imaging
→ camera!auto_ideal
→ aperture!dof_cinematic
→ aspect_ratio!detect
→ hdr!on
→ lighting!3point_pro + self_rim
→ position!rule_of_thirds_auto
→ quality!8k_masterpiece
→ negative_prompt!blur, noise, artifact, feral, animal head, muzzle, scales, claws
```

---

### **20. /Layers/refine.md**
```md
# refine.md — Chain Self-Correction + Variant Selection
→ @refine!user_confirm
→ confidence!threshold_0.98
→ @preview!grid_nx1
  → default!{primary_variant}
  → variant!{alt_variant}
  → extra!{luxury_variant}
→ @select!variant_id
→ @select!fallback → default
→ auto_apply!drift_fix
→ @log!chain_history → /Logs/chain_log.md
```

---

### **21. /Rules/gijinka_rules.md**
```md
# gijinka_rules.md — Immutable Laws + Renderer Compatibility
1. Every input becomes a Gijinka
2. Game layer defines action
3. Translation layer gives name and voice
4. Semantic layer gives emotion and memory
5. Image layer renders the body
6. Grid!1x1 shows one character in one image → EXCEPT in layer!debug or variant preview
7. layer!debug is never included in final
8. **User must @select!variant_id to lock final** (fallback to default)
9. layer!optics auto-optimizes imaging
10. Gijinka self-positions for maximum visual quality
11. Final image = 8K-ready, HDR, cinematic DOF
12. source!literal_only → NO added lore unless @expand
13. form!human_female_default → bipedal, human proportions
14. feature_map!explicit → animal trait → human body part
15. texture!8k_priority!early → sharpness locked in layer!image
16. @refine!user_confirm → pause if confidence < 0.98
17. negative!feral_lock → block quadruped, animal head, muzzle, scales, claws
18. skin!organic_micro → no scales, micro-pores only
19. myth!born_not_built → Gijinka must feel alive, not constructed

## **BIOLOGICAL CORE RULES**
20. **@map!structure_biology** → Source anatomy → human body
21. **skin!biological_merge** → No fabric. Skin *is* the input.
22. **@variant!refine** → Same biology → different soul expression
23. **negative!prop_lock** → No external objects of the source
24. **myth!biological_origin** → "I was never built. I grew."

## **FINAL REFINEMENTS**
25. **chain!atomic_only** → 
   - `!` = **3-place verb ("lock")**
   - Key = **patient / subject**
   - Value(s) = **goal / argument(s)**
   - Comma = **conjunction of goals**
   - Example: `key!arg1, arg2` → "key is locked to arg1 and arg2"
26. **multi_value_handling** → Use `@preview!grid_nx1` + `select variant`.
27. **image_chain_flex** → Reorder freely **within** `image.md`.
28. **image_scoped_rules** → `@rule!` only in `image.md`, never cross-layer.
29. **!lock_clarity** → 
   - `!lock` = structural (e.g. `face!lock`, `identity!lock`)
   - `!locked` = state mode (e.g. `focus!locked`)
   - Invalid: `expression!lock`, `focal_length!locked`
30. **identity_consistency** → 
   - Lock face: `identity!lock` or `identity!locked`
   - Lock mood: `expression!calm`
   - Vary mood: `expression~variant`

## **Renderer Compatibility**
- nano_banana: Add "beautiful human portrait" + strong negative
- SDXL / Pony XL: Best for Cyberflat-grade neon illustration
- Realism models: Avoid — default to animal heads
```

---

### **22. /Templates/gijinka_template.md**
```md
# gijinka_template.md — Input to Infinite Souls
@prompt!{input}
→ source!literal_only
→ form!human_female_default
→ layer!image
→ layer!game
→ layer!translation
→ layer!semantic
→ layer!soul
→ layer!optics
→ layer!refine [auto]
→ layer!debug [optional, auto-excluded]
→ grid!1x1
→ gijinka
→ @select!fallback → default
```

---

### **23. /Operators/syntax.md**
```md
# syntax.md — Operator Logic (User-Facing Only)
## Core Operators
- `!` → **verb: "lock"** → enforce key to argument(s)  
  Example: `face!crenelated_brow` → "lock face to crenelated_brow"

- `~` → **verb: "vary"** → allow controlled variation  
  Subtypes:
  - `~dynamic` → motion/time-based
  - `~adaptive` → context-reactive
  - `~harmonic` → aesthetic cohesion

- `-` → **verb: "omit"** → suppress attribute  
  Example: `backdrop-` → "omit backdrop"

## Verb-Argument Grammar
- Format: `key!arg1, arg2, arg3`
- `!` = **verb**
- Values after `!` = **arguments** (conjoined with `,`)
- Example:
  ```md
  face!crenelated_brow, merlon_cheekbones
  → "lock face to crenelated_brow and merlon_cheekbones"
```

---

### **24. /Preview/grid_preview.md**
```md
# grid_preview.md
→ @preview!grid_nx1
→ @variant!strict_form vs mythic_interpretation vs extra_luxury
→ output!non_final
→ use!refinement_only
→ watermark!PREVIEW — SELECT ONE
→ face_lock!strict → all variants
→ skin!organic_micro → all variants
```

---

### **25. /Commands/user_commands.md**
```md
# user_commands.md — Official SCF Commands
| Command | Syntax | Effect |
|---------|--------|--------|
| `generate prompt` | Append | Expands **selected variant** to render-ready prompt |
| `preview grid` | `preview grid 3x1` | Triggers **nx1 variant comparison** |
| `select variant` | `select variant v3_rose_elegance` | **Locks variant** |
| `add watermark` | `add watermark "Software Composition Framework for Gijinka"` | Adds watermark |
| `export chain` | `export chain` | Saves chain + variants |
| `set mode` | `set mode acg|real` | Switches mode |
| `set style` | `set style [name]` | Replaces current style in the chain |
```

---

````

