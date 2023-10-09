```dataviewjs
function isWithinWeek(page) {
	let fileMoment = moment(page.file.name, 'YYYY年MM月DD日');
	let today = moment().startOf('day');
	let tomorrow = today.clone().add(1, 'days').startOf('day');
	let weekAgo = today.clone().subtract(7, 'days').startOf('day');

	// If it's within this week and has a summary
	if (fileMoment.isAfter(weekAgo) && fileMoment.isBefore(tomorrow)) {
		if (page.Summary) {
			return true;
		}
	} else {
		return false;
	}
}

dv.table(["Date", "Summary"], dv.pages('"00 - 每日日记/DailyNote"')
	.filter(isWithinWeek)
	.sort(b => b.file.name, 'desc')
	.map(b => [dv.fileLink(b.file.name, false, moment(b.file.name, 'YYYY年MM月DD日').format("ddd")), "<span id='summary1'>" + b.Summary + "</span>"])
)
```