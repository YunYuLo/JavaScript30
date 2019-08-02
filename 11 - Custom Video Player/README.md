![](https://javascript30.com/images/JS3-social-share.png)

# JavaScript30

Starter Files + Completed solutions for the JavaScript 30 Day Challenge.

Grab the course at [https://JavaScript30.com](https://JavaScript30.com)

## basic function of video player

### btn: play or pause the video
- Method 1 : Noticed that `video.pasued` (return true/false) and the event `video.pause()` are different.
```javascript
function togglePlay() {
    if (video.paused) {
        video.play()
    } else {
        video.pause()
    }
}
video.addEventListener('click', togglePlay)
toggle.addEventListener('click', togglePlay)
```

- Method 2
```javascript
function togglePlay() {
    const method = video.paused ? 'play' : 'pause'
    video[method]() //call the method
}
//eventlistener same as above
```

- auto change btn when video play or pause
```javascript
function updateButton() {
    const icon = this.paused ? '►' : '❚ ❚'
    toggle.textContent = icon
}
video.addEventListener('play', updateButton)
video.addEventListener('pause', updateButton)
``` 

### skip button
- 取得當前影片進度的時間 `video.currentTime`
- return *number*: `parseFloat(str)` or `parseInt(str [, radix])` or `Number()`(MDN)[https://developer.mozilla.org/zh-TW/docs/Web/JavaScript/Obsolete_Pages/Obsolete_Pages/Obsolete_Pages/預先定義的函數/parseInt_和_parseFloat_函數]

```javascript
function skip() {
    video.currentTime += Number(this.dataset.skip)
}
skipButtons.forEach(btn => btn.addEventListener('click',skip))
```

### control range bar
```javascript
function handleRangeUpdate () {
    video[this.name] = this.value
}
ranges.forEach(range => range.addEventListener('change', handleRangeUpdate))
ranges.forEach(range => range.addEventListener('mousemove', handleRangeUpdate))
```

### update progress bar
- 取得影片時間總長度 `video.duration`
```javascript
function handleProgress() {
    const percent = (video.currentTime/ video.duration) *100
    progressBar.style.flexBasis = `${percent}%`
}
video.addEventListener('timeupdate', handleProgress)
```

- click to control the progress
```javascript
function scrub(e) {
    const scrubTime=  (e.offsetX / progress.offsetWidth) * video.duration
    video.currentTime = scrubTime
}
progress.addEventListener('click', scrub)
```
- control progress bar: mousedown move and mouseup stop
```javascript
let mousedown = false
progress.addEventListener('mousemove', (e) => mousedown && scrub(e))
progress.addEventListener('mousedown', () => mousedown = true)
progress.addEventListener('mouseup', () => mousedown = false)

```

### challeng : full screen

