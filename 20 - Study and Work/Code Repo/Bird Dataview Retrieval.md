---
项目名称: 示例库
相对路径: -
文件名称: -
代码名称: 小鸟dataview检索
CUID: 20220518002237
所在行: -
语言: javascript
框架: dataview
简述: 简化对应js代码。
tags: code_snippet
---
## Code Name
Dataview Bird Retrieval

## Code Description
- Countdowns
- Anniversaries


```dataview
TABLE WITHOUT ID
    ("![](" + photo + ")") as Photo,
    file.link as Name,
    "Birthday: " + dateformat(birthday, "yyyy-MM-dd") AS Birthday,
    "Age: " + split(string((date(today) - birthday).year), "\.", 1) + " years" AS Age,
    "Anniversary: " + dateformat(choice(BD < date(today), BD + dur(1 year), BD), "yyyy-MM-dd") AS Anniversary,
    "Countdowns: " + (choice(BD < date(today), BD + dur(1 year), BD) - date(today)).days + " days" AS Countdowns
FROM #parrot
WHERE photo
FLATTEN date(date(today).year + "-" + dateformat(birthday, "MM-dd")) AS BD
SORT choice(BD < date(today), BD + dur(1 year), BD) ASC
```

## Usage Notes
- You can add `cssclass: zettelkasten` or `cssclass: cards` to create card views on the usage page.

## Comments
- On 2022-05-20 at 13:19:00, with the help of @mnvwvnm on Discord, the corresponding code was created. The effect:

```dataview
TABLE WITHOUT ID
    ("![](" + photo + ")") as Photo,
    file.link as Name,
    "Birthday: " + dateformat(birthday, "yyyy-MM-dd") AS Birthday,
    "Age: " + split(string((date(today) - birthday).year), "\.", 1) + " years" AS Age,
    "Anniversary: " + dateformat(choice(BD < date(today), BD + dur(1 year), BD), "yyyy-MM-dd") AS Anniversary,
    "Countdowns: " + (choice(BD < date(today), BD + dur(1 year), BD) - date(today)).days + " days" AS Countdowns
FROM #parrot
WHERE photo
FLATTEN date(date(today).year + "-" + dateformat(birthday, "MM-dd")) AS BD
SORT choice(BD < date(today), BD + dur(1 year), BD) ASC
```

## Recent Code Snippets
```dataview
table
    Language,
    Framework,
    BriefDescription,
    file.cday AS "CreationTime"
from #code_snippet and !"40 - Obsidian/Template"
where date(today) - file.ctime <= dur(7 days)
sort file.mtime desc
limit 10
```

[[00. Code Repository|Code Management Main Page]]

---

Note: Thanks to @咖啡豆 for providing the template!