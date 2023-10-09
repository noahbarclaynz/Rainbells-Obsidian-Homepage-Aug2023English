---
category: 鹦鹉
name: 小灰灰
aliases: xiaohuihui, little gray
gender: 男
birthday: 2020-05-19
tags: parrot cockatiel bird
photo: https://s2.loli.net/2022/05/12/7PMoQTl81n9GXFu.jpg
---
Name: `=(this.name)`
Age: `$= let date = moment(dv.current().birthday.toString(),"yyyy-MM-DD"); let today = moment().startOf('day'); today.diff(date,"days")` days
Gender: `=(this.gender)`
Category: `=(this.category)`
Former Spouse: [[Chubby]] (Pang Pang)

Memo: [小灰灰 (Shortcut)](shortcuts://run-shortcut?name=NoteURL&input=1634282208)

```tracker
searchType: text
searchTarget: '\[\[Little Gray\]\][\n\r\s]+(?<value>[\-]?[0-9]+[\.][0-9]+|[\-]?[0-9]+)'
folder: 00 - Daily Journal/Weekly Notes
dateFormat: 'YYYY Week WW Records'
line:
    title: "Little Gray's Weight"
    xAxisLabel: Time
    yAxisLabel: Weight
    fillGap: true
    lineColor: gray

```dataviewjs
let folderChoicePath = "00 - Daily Journal/Daily Notes"
const files = app.vault.getMarkdownFiles().filter(file => file.path.includes(folderChoicePath))

let arr = files.map(async(file) => {
    const content = await app.vault.cachedRead(file)
    let lines = await content.split("\n").filter(line => line.includes("Little Gray"))
    //console.log(lines)
    return ["[["+file.name.split(".")[0]+"]]", lines]
})

Promise.all(arr).then(values => {
    const beautify = values.map(value => {
        const temp = value[1].map(line => { return line }) // Rewrite for beautification
        return [value[0], temp]
    })
    const exists = beautify.filter(value => value[1][0] && value[0] != "[[Unnamed 10]]").sort(value => value[0],'desc')
    dv.table(["Date", "Pet Records"], exists)
})
```
