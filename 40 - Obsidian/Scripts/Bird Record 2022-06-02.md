```dataviewjs
// Define the folder path to choose
let folderChoicePath = "00 - Daily Journal";
const files = app.vault.getMarkdownFiles().filter(file => file.path.includes(folderChoicePath));

// Map over the files in the specified folder
let arr = files.map(async (file) => {
    // Read the content of each file
    const content = await app.vault.cachedRead(file);
    
    // Split the content into lines and filter for lines containing "#"
    let lines = await content.split("\n").filter(line => line.includes("#BirdLog"));

    // Create a formatted link for each file and extract relevant lines
    return [dv.fileLink(file.name.split(".")[0], false, moment(file.name.split(".")[0], "YYYY-MM-DD").format("M/D")), lines];
});

// Process the data
Promise.all(arr).then(values => {
    // Beautify the data by removing the first 8 characters from each line
    const beautify = values.map(value => {
        const temp = value[1].map(line => { return line.slice(8,) }); // More beautification can be done here
        return [value[0], temp];
    });

    // Filter out entries with empty content and select the first 7 entries for display
    const exists = beautify.filter(value => value[1][0] && value[0] != "[[Unnamed 10]]").slice(0, 7).sort().reverse();

    // Create a table with the data
    dv.table(["Date", "Bird Log"], exists);
});

```