---
defines-react-components: true
tags: code_snippet
项目名称: MoodTracker
相对路径: -
文件名称: -
代码名称: Moodtracker
CUID: -
所在行: -
语言: javascript
框架: react
简述: 呈现情绪记录小面板。
---

```jsx:component:MoodTracker
  const [selectedMood, setSelectedMood] = useState(null);
  const [moodLog, setMoodLog] = useState([]);

  const moods = [
    { icon: "😀", label: "Great!" },
    { icon: "😊", label: "Pleasant" },
    { icon: "😐", label: "Alright" },
    { icon: "😔", label: "Sad" },
    { icon: "😠", label: "Angry" },
    { icon: "🤯", label: "Explosion" },
  ];

  useEffect(() => {
    const savedMoodLog = localStorage.getItem("moodLog");
    if (savedMoodLog) {
      setMoodLog(JSON.parse(savedMoodLog));
    }
  }, []);

  const handleMoodClick = (mood) => {
    setSelectedMood(mood);
  };

  const addMoodLog = () => {
    if (selectedMood) {
      const newMoodLog = [...moodLog, { mood: selectedMood, date: new Date() }];
      setMoodLog(newMoodLog);
      localStorage.setItem("moodLog", JSON.stringify(newMoodLog));
      setSelectedMood(null);
    }
  };

  return (
    <div className="mood-tracker">
      <h3>Mood Tracker</h3>
      <div className="mood-icons">
        {moods.map((mood, index) => (
          <span
            key={index}
            className={`mood-icon ${selectedMood === mood ? "selected" : ""}`}
            onClick={() => handleMoodClick(mood)}
          >
            {mood.icon}
          </span>
        ))}
      </div>
      <button onClick={addMoodLog} disabled={!selectedMood}>
        Submit
      </button>
      <div className="mood-log">
        {moodLog.map((entry, index) => (
          <div key={index} className="mood-entry">
            <span>{entry.mood.icon}</span>
            <span>{entry.mood.label}</span>
            <span>{new Date(entry.date).toLocaleDateString()}</span>
          </div>
        ))}
      </div>
    </div>
  );


```
```jsx:
<MoodTracker></MoodTracker>
```
