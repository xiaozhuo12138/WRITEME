# chinese-xinhua

中华新华字典数据库和 API 。收录包括 14032 条歇后语，16142 个汉字，264434 个词语，31648 个成语。

## Project Structure

```
chinese-xinhua/
|
+- data/ <-- 数据文件夹
|  |
|  +- idiom.json <-- 成语
|  |
|  +- word.json <-- 汉字
|  |
|  +- xiehouyu.json <-- 歇后语
|  |
|  +- ci.json <-- 词语
```

## Database Introduction

### 成语 (idiom.json)

```json
[
    {
        "derivation": "语出《法华经·法师功德品》下至阿鼻地狱。”",
        "example": "但也有少数意志薄弱的……逐步上当，终至堕入～。★《上饶集中营·炼狱杂记》",
        "explanation": "阿鼻梵语的译音，意译为无间”，即痛苦无有间断之意。常用来比喻黑暗的社会和严酷的牢狱。又比喻无法摆脱的极其痛苦的境地。",
        "pinyin": "ā bí dì yù",
        "word": "阿鼻地狱",
        "abbreviation": "abdy"
    },
    ...
]
```

### 词语 (ci.json)

```json
[
    { 
        "ci": "宸纶", 
        "explanation": "1.帝王的诏书﹑制令。" 
    },
    ...
]
```

### 汉字 (word.json)

```json
[
    {
        "word": "嗄",
        "oldword": "嗄",
        "strokes": "13",
        "pinyin": "á",
        "radicals": "口",
        "explanation": "嗄〈叹〉\n\n 同啊”。表示省悟或惊奇\n\n 嗄!难道这里是没有地方官的么?--宋·佚名《新编五代史平话》\n\n 嗄á叹词。在句首，〈表〉疑问或反问～，这是什么？～，你想干什么？\"嗄\"另见shà㈠。\n\n 嗄shà\n\n ⒈声音嘶哑～声。\n\n 嗄a 1.助词。表示强调﹑肯定或辩解。 2.助词。方言。表示疑问或反诘。\n\n 嗄xià 1.见\"嗄饭\"。 2.见\"嗄程\"。",
        "more": "嗄 ga、a 部首 口 部首笔画 03 总笔画 13  嗄2\nshà\n〈形〉\n(1)\n声音嘶哑的 [hoarse]\n终日嚎而嗌不嗄。--《老子》\n(2)\n又如嗄哑,嗄嘶(嗓音嘶哑)\n嗄\nshà\n〈叹〉\n(1)\n什么 [what]--表示否定\n我要丢个干干净,看你嗄法把我治。--清·蒲松龄《聊斋俚曲集》\n(2)\n旧时仆役对主人、下级对上级的应诺声 [yes]\n带进来”。两边军士应一声嗄”,即将牛皋推至面前。--《说岳全传》\n另见á\n嗄1\ná\n〈叹〉\n同啊”(á)。表示省悟或惊奇 [ah]\n嗄!难道这里是没有地方官的么?--宋·佚名《新编五代史平话》\n另见shà\n嗄1\nshà　ㄕㄚ╝\n嗓音嘶哑。\n郑码janr，u55c4，gbke0c4\n笔画数13，部首口，笔顺编号2511325111354\n嗄2\ná　ㄚˊ\n同啊2”。\n郑码janr，u55c4，gbke0c4\n笔画数13，部首口，笔顺编号2511325111354"
    },
    ... 
]
```

### 歇后语 (xiehouyu.json)

```json
[
    {
        "riddle": "飞机上聊天",
        "answer": "高谈阔论"
    },
    ...
]
```

## Changelog

<details><summary>查看更新日志  </summary> 

- 20181216: 成语数据集去重
- 20181216: API 功能下线
- 20180803: 添加词语数据集
- 20180206: 添加成语，歇后语，汉字数据集

</details>


## Copyright

本仓库的所有的数据都是我从网上收集整理的。仓库本来的目的是因为我以前想做一个成语接龙的东西，但是苦于没有现成可用的数据库，自己就从各个网站抓取整理了一份。放在 Github 是为了方便自己的使用，同时也能方便有类似需求的人不用去做这些 trival 的工作。所有抓取数据的[脚本](./scripts/README.md)都在仓库里。

**本仓库无任何商业目的！如果有侵权行为将及时删除！**