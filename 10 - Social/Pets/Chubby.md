---
category: 鹦鹉
name: 胖胖
aliases: pangpang
gender: 女
birthday: 2020-11-01
tags: parrot cockatiel bird
photo: https://s2.loli.net/2022/05/12/SbedxM2L4ilWNw5.jpg
---
Name: `=(this.name)`
Age: `$= let date = moment(dv.current().birthday.toString(),"yyyy-MM-DD"); let today = moment().startOf('day'); today.diff(date,"days")` days
Gender: `=(this.gender)`
Species: `=(this.category)`
Former Spouse: [[Little Gray]]

``` tracker
searchType: text  
searchTarget: '\[\[Little Gray\]\][\n\r\s]+(?<value>[\-]?[0-9]+[\.][0-9]+|[\-]?[0-9]+)'
folder: 00 - Daily Journal/Weekly Notes
dateFormat: 'YYYYWWDD'
line:
    title: "Little Gray's Weight"
    xAxisLabel: Time
    yAxisLabel: Weight
    fillGap: true
    lineColor: gray
```

```dataviewjs
let folderChoicePath = "00 - Daily Diary/DailyNote"
const files = app.vault.getMarkdownFiles().filter(file => file.path.includes(folderChoicePath))

let arr = files.map(async(file) => { 
    const content = await app.vault.cachedRead(file) 
    let lines = await content.split("\n").filter(line => line.includes("Little Gray") && !line.includes("White Chubby")) 
    return ["[["+file.name.split(".")[0]+"]]", lines] 
}) 

Promise.all(arr).then(values => { 
    const beautify = values.map(value => { 
        const temp = value[1].map(line => { return line }) // Beautify needs to be rewritten
        return [value[0],temp] 
    }) 
    const exists = beautify.filter(value => value[1][0] && value[0] != "[[Unnamed 10]]") .sort(value => value[0],'desc') 
    dv.table(["Date", "Pet Records"], exists) 
})
```