---
defines-react-components: true
---
```jsx:component:MusicPlayer

const fs = require('fs');
const path = require('path');

function getAudioDataURL(filePath) {
    const audioData = fs.readFileSync(filePath);
    return 'data:audio/mpeg;base64,' + audioData.toString('base64');
}

function extractFileName(filePath) {
    return path.basename(filePath);
}

const vaultPath = app.vault.adapter.basePath;
const relativeMusicFolderPath = '40 - Obsidian/Music';
const folderPath = path.join(vaultPath, relativeMusicFolderPath);

const audioFilePaths = fs.readdirSync(folderPath)
    .filter(file => path.extname(file) === '.mp3')
    .map(file => path.join(folderPath, file));

const audioDataUrls = audioFilePaths.map(getAudioDataURL);

const [selectedAudioIndex, setSelectedAudioIndex] = useState(0);
const audioRef = useRef(null);

function handleAudioEnd() {
    if (selectedAudioIndex < audioDataUrls.length - 1) {
        setSelectedAudioIndex(selectedAudioIndex + 1);
    } else {
        setSelectedAudioIndex(0);
    }
    audioRef.current.play();
}

// useEffect(() => { if (audioRef.current) { audioRef.current.play(); } }, [selectedAudioIndex]);

const [isFirstMount, setIsFirstMount] = useState(true);


useEffect(() => {
    setIsFirstMount(false);
}, []);

useEffect(() => {
    if (audioRef.current && !isFirstMount) {
        audioRef.current.play();
    }
}, [selectedAudioIndex]);




return (
    <div className="audio-container">
        <select className="audio-dropdown"
            value={selectedAudioIndex}
            onChange={(e) => {
                setSelectedAudioIndex(Number(e.target.value));
                setTimeout(() => audioRef.current.play(), 100);
            }}
        >
            {audioDataUrls.map((dataUrl, index) => (
                <option key={index} value={index}>
                    {extractFileName(audioFilePaths[index])}
                </option>
            ))}
        </select>
        <div className="audio-section">
            <audio ref={audioRef} controls onEnded={handleAudioEnd} src={audioDataUrls[selectedAudioIndex]} type="audio/mpeg">
                Your browser does not support the audio element.
            </audio>
        </div>
    </div>
);




```



```jsx:
<MusicPlayer></MusicPlayer>
```