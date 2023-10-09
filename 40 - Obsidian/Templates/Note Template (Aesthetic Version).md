---
creation date: 2022-03-21 12:30
modification date: <%+ tp.file.last_modified_date("dddd Do MMMM YYYY HH:mm:ss") %>
tags: DailyNote 日记模板 1

banner: "40 - Obsidian/Attachments/banners/daily-note-banner.gif"
cssclass: noyaml
banner_icon: 💌
banner_x: 0.5
banner_y: 0.38

week:: 2022-12
---

# Daily Note Template 1

<< [[December 31, 0000]] | [[January 02, 0001]] >>

## Summary
```ad-flex

<div>

**Habits**

[Birds :: ]
[Emails :: ]
[Exercise :: ]
[Skincare :: ]

**Health**

[No Takeout :: ]
[No Snacking :: ]

</div>

<div>

**Life**

[Mood :: ]
[Anxiety :: ]
[Expenses :: ]
[Weight :: ]
[Menstruation :: ]
[Exercise :: ]

</div>

<div>

**Overall**

[Plans :: ]
[Plan Completion :: ]

[Summary :: ]

</div>

```
## Diary
Nanjing, China: 🌧   +6°C


## Schedule




## Birds
**[[March 21, 2022]]**
^1

This week's record: [[Week 12, 2022 Parrot Records]]

## Tasks

<p class="stickies";>
<b>COUNTDOWN</b><br>
Little Yellow has been taking <%-* let edate = moment("2022-02-07", "yyyy-MM-DD"); let from = moment().startOf('day'); tR += from.diff(edate, "days") %> days of Xihuan su
Little Yellow has been using eye drops for <%-* let edate = moment("2022-02-05", "yyyy-MM-DD"); let from = moment().startOf('day'); tR += from.diff(edate, "days") %> days
Little Yellow and Kongkong have been taking Gu-Guang-Gan-Gao for <%-* let edate = moment("2022-02-06", "yyyy-MM-DD"); let from = moment().startOf('day'); tR += from.diff(edate, "days") %> days
Bai Pangpang and the bird flock have been taking Xihuan su for <%-* let edate = moment("2022-02-08", "yyyy-MM-DD"); let from = moment().startOf('day'); tR += from.diff(edate, "days") %> days
Bai Pangpang has been using eye drops for <%-* let edate = moment("2022-02-08", "yyyy-MM-DD"); let from = moment().startOf('day'); tR += from.diff(edate, "days") %> days
	<font color="red">Note: The above statistics do not include today</font>
<!-- --- -->
</p>


#### Expired Tasks

```tasks

not done
hide edit button
hide due date
due before 2022-03-21

```

#### Next Week's Tasks

```tasks
not done
due after {{date:YYYY-MM-DD}}
due before {{date+7d:YYYY-MM-DD}}
path does not include Bird Flock
```

#### Must-Do Today

```tasks

not done

due on 2022-03-21

hide backlink
hide due date

```

#### Long-Term Tasks
```tasks
no due date
path includes Year
path does not include Template
path does not include Bird Flock
path does not include March 21, 2022
heading does not include Group Check-in
path does not include 2021 Annual Planning
exclude sub-items
hide edit button
not done
short mode
```

#### Next Year's Schedule
```tasks
due after 2022-03-21
due before 2025-01-01
path includes Year
path does not include Template
path does not include Bird Flock
path does not include December 09, 2021
exclude sub-items
not done
hide backlink
hide edit button
```

#### Today's Accomplishments

```tasks

done on 2022-03-21
short mode
heading does not include Group Check-in
hide done date
hide backlink
hide edit button
limit to 10

```


---
```dataviewjs

let ftMd = dv.pages("").file.sort(t => t.cday)[0]
let total = parseInt([new Date() - ftMd.ctime] / (60*60*24*1000))
let totalDays = "You've been using *Obsidian* for "+total+" days, "
let nofold = '!"misc/templates"'
let allFile = dv.pages(nofold).file
let totalMd = "and have created "+
	allFile.length+" documents."
let totalTag = "You have "+allFile.etags.distinct().length+" unique tags, "
let totalTask = "and "+allFile.tasks.length+" tasks in total. <br><br>"
dv.paragraph(
	totalDays+totalMd+" "+totalTag+" "+totalTask
)

```
