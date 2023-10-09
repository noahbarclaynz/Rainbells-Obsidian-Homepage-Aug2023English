---
created: 2021-10-13 09:24
modified: NaN
category: parrot
name: 白胖球球
aliases: baipangqiuqiu, 白胖球
gender: male
birthday: 2021-08-23
tags: parrot budgie bird
photo: file:///Users/Riddle/Library/Mobile%20Documents/iCloud~md~obsidian/Documents/%E5%85%AB%E5%96%9C/80%20-%20Obsidian/%E9%99%84%E4%BB%B6/%E9%B8%9F%E7%85%A7/%E7%99%BD%E8%83%96%E7%90%83%E7%90%830.JPG
---
Memo: [White Fat Ball](shortcuts://run-shortcut?name=NoteURL&input=1634282360)

``` tracker
searchType: text  
searchTarget: '\[\[White Fat Ball(\|White Fat Ball)?\]\][\n\r\s]+(?<value>[\-]?[0-9]+[\.][0-9]+|[\-]?[0-9]+)'
folder: 20 - Parrots/Macaw Weekly Notes
dateFormat: 'YYYY Week WW Parrot Records'
line:
    title: "White Fat Ball Weight"
    xAxisLabel: Time
    yAxisLabel: Weight
    fillGap: true
    lineColor: gray
```

```dataviewjs
let folderChoicePath = "00 - Daily Journal"
const files = app.vault.getMarkdownFiles().filter(file => file.path.includes(folderChoicePath))

let arr = files.map(async(file) => { 
    const content = await app.vault.cachedRead(file) 
    let lines = await content.split("\n").filter(line => line.includes("White Fat Ball")) 
    //console.log(lines) 
    return ["[["+file.name.split(".")[0]+"]]", lines] 
}) 

Promise.all(arr).then(values => { 
    const beautify = values.map(value => { 
        const temp = value[1].map(line => { return line }) // To beautify, rewrite as needed
        return [value[0],temp] 
    }) 
    const exists = beautify.filter(value => value[1][0] && value[0] != "[[未命名 10]]") .sort(value => value[0],'desc') 
    dv.table(["Date", "Birdling Record"], exists) 
})
```