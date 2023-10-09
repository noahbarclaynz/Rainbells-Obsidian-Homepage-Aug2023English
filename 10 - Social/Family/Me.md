---
name: 秦某
gender: 男
birthday: 1999-06-20
email: 10000007@qq.com
phone: 1000000007
tags: family closerfamily
---
## Basic Information

Name: `=(this.name)`
Age: `$= let date = moment(dv.current().birthday.toString(),"yyyy-MM-DD"); let today = moment().startOf('day'); today.diff(date,"years")` years old
Email: `=(this.email)`
Phone: `=(this.phone)`

## Habit Tracking

```dataview
TABLE WITHOUT ID
    link(file.name) as "Date",
    Excerpt AS "🌄",
    BirdNest AS "🐥",
    Exercise AS "🏃‍♂️",
    Email AS "💌",
    Writing AS "📝",
    Mood AS "👾",
    Summary
FROM "00 - Daily Journal/Daily Notes" 
SORT file.name DESC
LIMIT 7
