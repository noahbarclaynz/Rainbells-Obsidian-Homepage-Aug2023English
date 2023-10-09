---
name: 李四
gender: 女
birthday: 2010-03-03
email: 10000002@qq.com
phone: 1000000002
tags: family daughter closerfamily
---
**Name:** `=(this.name)`
**Age:** `$= let date = moment(dv.current().birthday.toString(),"YYYY-MM-DD"); let today = moment().startOf('day'); today.diff(date,"years")` years old
**Email:** `=(this.email)`
**Phone:** `=(this.phone)`
