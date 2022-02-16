# 🚀 Music-Engine
Search and Get the Music that you like from anywhere!

## Table of Contents
- [What is music-engine?](#what-is-music-engine)
- [Why music-engine?](#why-music-engine)
- [Features](#features)
- [Platforms](#platforms)
- [Documents](#documents)
- [Examples](#examples)
    - [YouTube Downloader](#youTube-downloader)
    - [Discord Bot](#discord-bot)
- [Credits](#credits)

### What is music-engine?
music-engine is a package to fetch a music/artist/album or even playlist from the platform you choose,
there multi platforms that are supported in this package, so there is no need for any others....

### Why music-engine?
music-engine currently Supports **4** biggest platform that we all know all-in-one package and access to the Audio buffers directly from the platform API, so we are **all-in-one** and we have **download feature**

### Features
- [x] Custom Data Wrapper
- [x] No Token Required
- [x] Music Buffers (sometimes FFMPEG or Opus)

### Platforms
- [x] YouTube
- [x] SoundCloud
- [x] Spotify
- [x] Deezer
- [] Radio Javan (Maybe, maybe not)

### Documents
at the time you are reading this, i'm probably working on it...

### Examples

#### YouTube Downloader
```js
const { YouTube } = require("music-engine");
const myEngine = new YouTube();

myEngine.use('https://www.youtube.com/watch?v=KQlyGYCKGGA', { format: true })
.then(resultArray => {
    const track = resultArray[0];
    track.stream()
    .then(audioBuffer => {
        audioBuffer.pipe(fs.createWritestream("music.mp3"))
    })
    .catch(console.error)
})
.catch(console.error)
```

#### Discord Bot
```js
const { YouTube } = require("music-engine");
const myEngine = new YouTube();

myEngine.use('https://www.youtube.com/watch?v=KQlyGYCKGGA', { format: true })
.then(resultArray => {
    const track = resultArray[0];

    // Disabling chunking is recommended in Discord bots
    track.stream({ filter: 'audioonly', dlChunkSize: 0 })
    .then(async audioBuffer => {
        // Discord.js Stuff....
        const connection = await voiceChannel.join();
        const dipatcher = connection.play(audioBuffer)
        
        // Enjoy the Music
    })
    .catch(console.error);
})
.catch(console.error)
```
- More Examples would be added soon (PR's are welcome)

### Credits
- Thanks to [Hooman](https://github.com/Scrip7) for all the helps on the package and Future PR's