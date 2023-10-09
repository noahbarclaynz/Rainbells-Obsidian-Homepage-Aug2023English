---
> October 10th 2023
> 
> Hello, this is Noah. I've taken the time to translate everything into English, and it has been an insightful journey. Rainbell's work has been impressive, and I gained a lot of knowledge while relinking the JavaScript and dissecting the organizational structure. Please note that everything remains largely original, with exceptions for translations and a few components I deemed excessive to recode and translate without added value. I've also translated all the CSS files and appended comments to some code sections for clarity. Now, let's delve back into the original FAQ. Many thanks to Rainbell!

Hello, I am Rainbell, also known as 雨铃 in Chinese.

This instance library has been officially used for two years! During these two years, I have been continuously using Obsidian to manage various aspects of my life, whether it's academics, work, career planning, health management, or even raising little parrots! It's been a year since the last major update, and this time I have added many commonly used features for myself, which are also included in this update!

If you have any questions about the sample library, please feel free to add Rainbell0129 on WeChat for inquiries, or you can join the Rainbell Library Q&A group on WeChat. Questions that are frequently asked in the group will be summarized and written here.

== Contact Information ==

QQ: Lavi
WeChat: Rainbell0129
QQ Channel: Bird Brother
Discord: Rainbell
GitHub: Rainbell129
E-mail: njuwyl@gmail.com

```toc
```


# Warning

1. Please do not update the icon-folder plugin. Keep it at version 1.0.61, as updating it may cause various issues, such as search functionality not working.
2. Icon Folder has now been removed.

# Which themes can I use?
The sample library supports the minimal and blue topaz themes and has been specially optimized for them. However, theoretically, you can use any theme.

# After upgrading to Obsidian v15, clicking on links in the sidebar opens them directly in the sidebar. What should I do?
![[1658115786245751.mp4]]
- You can follow the video to reconfigure:
1. Right-click on the sidebar icon.
2. Click "pin."
3. Now, open the command palette and select the "Manage Workspace Layouts" command.
4. Re-save the main workspace.
5. Once set up, it's done for good.

# How can I change the icons for MD documents in the sidebar?

1. Open the `sidepane.css` file in the CSS snippet folder.
2. Change the text in the red box to the name of the MD document for which you want to change the icon.
![[50021653820977_.jpg.jpg]]
3. You can also download SVG code from the internet to replace the code here.

# How can I create split-screen views?

## 1. Using ad-flex

Use the div tag to create columns.

`````

```ad-flex

<div>
111
</div>


<div>
222
</div>

<div>
333
</div>

```
`````
## 2. Using ad-col2

Create columns using empty lines.

`````

```ad-col2

111

222

```

`````

Result:
```ad-col2

111

222

```

## 3. Using ad-col3

Create columns using empty lines.

````
```ad-col3

111

111

111

```
`````

Result:
```ad-col3

111

111

111

```
## 4. Using ad-flex to wrap dataview code

Create columns using div tags.

`````
````ad-flex
<div>

### Recently Modified
```dataview
table WITHOUT ID file.link AS "Title", file.mtime AS "Time"
from !"Template" and !"Kanban"
sort file.mtime desc
limit 10
```
</div>

<div>

### Recently Created
```dataview
table file.ctime AS "Created Time"
where date(today) - file.ctime <= dur(3 days)
sort file.ctime desc
limit 10
```
</div>
````
`````

(Notice that there are four backticks surrounding "ad-flex" on the outermost lines.)

# How can I create a link to the daily note?

1. You need to download an advanced URI plugin.
2. The link behind the "Today's Note" in the sample library is created in this way. It's based on binding a command to the link: "Open Daily Note." If you haven't created a daily note, it will help you create one, and if you've already created one, it will open it directly.
3. Generating it is quite simple. Just go to the command palette and select "Copy URI for Daily Note." If you want to use other commands, you can customize it slightly using "Copy URI for Command" (e.g., to open a weekly note, find the "Open Weekly Note" command).
![[100911654141903_.pic.jpg]]
4. Open the homepage in preview mode by using syntax like "&viewmode=preview." For more, you can refer to the advanced URI documentation, link available in [[00. Reference Summary#Obsidian]]. Example: [Homepage](obsidian://advanced-uri?vault=Rainbell&filepath=40%2520-%2520Obsidian%252F%25E4%25B8%25BB%25E9%25A1%25B5%252F00.%2520%25E4%25B8%25BB%25E9%25A1%25B5.md&viewmode=preview)
5. If you encounter a "vault not found" issue when clicking the link, it's probably because you changed the vault name. Regenerate the URI to fix it.
Note: Links generated through quick commands usually specify the vault name. If you want to remove this specification, you can delete the vault name part. This way, the plugin will automatically open the last used vault.
- [Daily note link with specified vault

](obsidian://advanced-uri?vault=Rainbell&daily=true)
- [Daily note link without specifying a vault](obsidian://advanced-uri?daily=true)

# How can I change the calendar icon at the top of the homepage?

1. Open the `homepage settings.css` file in the CSS snippet folder. ![[Screen Shot 2022-06-02 at 15.08.21.png]]
2. Find this section and comment it out or delete it to remove the calendar icon (you can also change the color inside it, refer to the wolai icon usage guide: https://notioner.notion.site/Notion-5b20acf443244b04885f7717c97d8702). ![[Screen Shot 2022-06-02 at 15.08.45.png]]
3. If you want to adjust the position of the banner icon, open the banner settings and find the "Vertical Alignment" section. Choose "above" or "center." ![[Screen Shot 2022-06-02 at 15.10.29.png]]

# How to use the project statistics on the homepage?

To use project tracking, you need a YAML section in a single-note project with the following structure:
```
target: 10000
status: In Progress
tags: project
```
It is based on https://gist.github.com/chrisgrieser/ac16a80cdd9e8e0e84606cc24e35ad99. You can find more information there.

If you want to use "Completed Tasks/Total Tasks" for project progress tracking, use the following YAML:
```
target: tasks
status: In Progress
tags: project
```

If you need tag effects, enable the `sharetype.css` CSS snippet.

# How to exclude a certain tag or folder when using Dataview for retrieval?

## Dataview JavaScript
### Exclude a certain tag
For excluding tags, you can use the following approach:
````

```dataviewjs
dv.table(["Card", "Description"],
dv.pages("#zettelkasten and -#生词 and -#计算机")
	.map(b => [b.file.link, b.description]))

```

````

The main idea is to "subtract" the tags you want to exclude after `dv.pages`, connected with "and."

### Exclude a certain folder
Refer to the retrieval method in [[00. Code Library]]:
````

```dataviewjs
let excludeFolderChoicePath = "40 - Obsidian/模板"

dv.table(["Name", "Language", "Framework", "Description", "Creation Time"], dv.pages('#code_snippet')
	.filter(b => !b.file.path.includes(excludeFolderChoicePath))
	.sort(b => b.file.ctime,'desc')
	.map(b =>[dv.fileLink(b.file.name, false, b.代码名称), b.语言, b.框架, b.简述, b.file.cday])
	)
```

````

1. First, define the path to be excluded: `let excludeFolderChoicePath = "40 - Obsidian/模板"`.
2. Then, right after `dv.pages(...)`, add an additional filter: `.filter(b => !b.file.path.includes(excludeFolderChoicePath))`.

# What if I don't know how to use Templater or Quickadd?
I recommend watching these two videos:
- [How to Use the Templater Feature](https://www.bilibili.com/video/BV1tv411h75N?spm_id_from=333.999.0.0)
- [Quickly Add Anything with the Quickadd Plugin](https://www.bilibili.com/video/BV1fw411f7xy?spm_id_from=333.999.0.0)

In the sample library, I have limited templates, and only one of them, [[Create Code Template]], is configured with Quickadd. However, when I use Obsidian myself, I use Quickadd to add more things, such as daily memos, the weight of my birds, diaries, weekly reports, monthly summaries, and more.

You can try setting up more Quickadd options on your own if you want, as using my settings alone may not be sufficient.
