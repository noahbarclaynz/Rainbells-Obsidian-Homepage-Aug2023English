---
项目名称: -
相对路径: -
文件名称: -
代码名称: Dataviewjs参考
CUID: 20220518002237
所在行: -
语言: javascript
框架: dataview
简述: 作为dataviewjs的一些参考。
tags: code_snippet
---
%%Tools: Generate [20-character UID (mix of lowercase letters and numbers)
- 1Password Strong Password Generator](https://1password.com/password-generator/)
- [LastPass Password Generator](https://www.lastpass.com/features/password-generator) %%

## Code Name
Some Reference Usages of Dataview Javascript

## Code Description

1. CTRL+SHIFT+I is your friend: You can use console.log(x) and object to view its internal structure, which will help you understand how to use it.
2. Iterating through YAML metadata fields: I find these objects challenging to work with, and the most reliable iteration methods are `for (let key of Object.keys(x)) { }` or `for (let [key, val] of Object.entries(x)) { }`.
3. Output and set data styles: Apart from the documented `dv.list()` and `dv.Table`, there isn't much guidance on how to actually output data. You can use `dv.el()` to create HTML elements, but it's limited compared to using it from the Obsidian API. `createEl()` is because this function allows you to add classes and IDs to elements, and more. Dataviewjs creates a container that you can reference as `this.container`. For example, `this.container.createEl('p', {text: "Hello", cls: ["hello-box"]})` will insert `<p class="hello-box">Hello</p>`, allowing you to set the style of that element using CSS snippets.
4. Calling other plugins: You can call other plugins within dataviewjs scripts. For example, calling Templater user functions within dataviewjs: `let tpl = this.app.plugins.plugins['templater-obsidian'].templater;` followed by `let output = await tpl.current_functions_object.user.myFunction({v1: val1, v2: val2});` will allow you to pass values for external processing and display the results in Obsidian. Being able to call any program has opened up a lot of possibilities. I was impressed by how seamlessly it worked when I first tried this and saw it correctly fetching results from my Python script and displaying them in Obsidian. Use Tip #1 to help find the functions you need.
5. Manually building tables: You can create an array of arrays `rows` and provide it to `dv.table(["Col1", "Col2", etc], rows.map(v => v));` to put any data you want into a table. (But you already knew this =P)

## Usage Notes
When using, keep the following points in mind:

## Comments
- May 18, 2022, 10:53, from [Reddit Post](https://www.reddit.com/r/ObsidianMD/comments/ur3f7d/holy_hell_dataview/) by @TSPhoenix

## Recent Code Snippets
```dataview
table
    Language,
    Framework,
    Brief Description,
    file.cday AS "Creation Time"
from #code_snippet and !"40 - Obsidian/Template"
where date(today) - file.ctime <= dur(7 days)
sort file.mtime desc
limit 10
