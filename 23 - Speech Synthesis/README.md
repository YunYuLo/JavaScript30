![](https://javascript30.com/images/JS3-social-share.png)

# JavaScript30

Starter Files + Completed solutions for the JavaScript 30 Day Challenge.

Grab the course at [https://JavaScript30.com](https://JavaScript30.com)

##

```javascript
  const msg = new SpeechSynthesisUtterance();
  let voices = [];
  const voicesDropdown = document.querySelector('[name="voice"]');
  const options = document.querySelectorAll('[type="range"], [name="text"]');
  const speakButton = document.querySelector('#speak');
  const stopButton = document.querySelector('#stop');
  msg.text = document.querySelector('[name="text"]').value

  function populateVoices (){
    const voices = this.getVoices() //return a SpeechSynthesisVoice array
        .filter(voice => voice.lang.includes('en'))
        .map(voice => `<option value="${voice.name}">${voice.name} (${voice.lang})</option>`)
        .join('')
    voicesDropdown.innerHTML = voiceOptions
  }
  //select voice from input
  function setVoice() {
    msg.voice = voices.find(voice => voice.name === this.value)
    toggle()
  }
  //toggle the voice true/false
  function toggle(startOver = true) {
    speechSynthesis.cancel()
    if (startOver) {
      speechSynthesis.speak(msg)
    }
  }
  // tune the rate and pitch of voice
  function setOption() {
    msg[this.name] = this.value
    toggle()
  }


  speechSynthesis.addEventListener('voiceschanged', populateVoices)
  voicesDropdown.addEventListener('change', setVoice)
  options.forEach(option => option.addEventListener('change', setOption))
  speakButton.addEventListener('click', toggle)
  stopButton.addEventListener('click', () => toggle(false))
```

[SpeechSynthesisUtterance](https://developer.mozilla.org/en-US/docs/Web/API/SpeechSynthesisUtterance):The `SpeechSynthesisUtterance` interface of the Web Speech API represents a speech request. It contains the content the speech service should read and information about how to read it (e.g. language, pitch and volume.)

[SpeechSynthesis](https://developer.mozilla.org/zh-CN/docs/Web/API/SpeechSynthesis) : interface of the Web Speech API is the controller interface for the speech service; this can be used to retrieve information about the synthesis voices available on the device, start and pause speech, and other commands besides.

- [SpeechSynthesis.speak()](https://developer.mozilla.org/en-US/docs/Web/API/SpeechSynthesis/speak)
- [SpeechSynthesis.cancel()](https://developer.mozilla.org/en-US/docs/Web/API/SpeechSynthesis/cancel)
- [SpeechSynthesis.getVoices()](https://developer.mozilla.org/en-US/docs/Web/API/SpeechSynthesis/getVoices) method of the `SpeechSynthesis` interface returns a list of `SpeechSynthesisVoice` objects representing all the available voices on the current device.

- [Function.prototype.bind()](https://developer.mozilla.org/zh-TW/docs/Web/JavaScript/Reference/Global_Objects/Function/bind)method creates a new function that, when called, has its this keyword set to the provided value, with a given sequence of arguments preceding any provided when the new function is called.
```javascript
//Three different ways express the same outcome.
stopButton.addEventListener('click', function(){
  toggle(false)
})
stopButton.addEventListener('click', () => toggle(false))
stopButton.addEventListener('click', toggle.bind(null, false))

```