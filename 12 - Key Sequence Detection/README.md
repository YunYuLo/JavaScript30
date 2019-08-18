![](https://javascript30.com/images/JS3-social-share.png)

# JavaScript30

Starter Files + Completed solutions for the JavaScript 30 Day Challenge.

Grab the course at [https://JavaScript30.com](https://JavaScript30.com)

## 當系統偵測到隱藏的鍵盤順序，就跳出獨角獸～

```javascript
const pressed = []
  const secretCode = 'wesbos'
  window.addEventListener('keyup', (e) => {
    pressed.push(e.key)
    pressed.splice(-secretCode.length - 1, pressed.length-secretCode.length)

    if(pressed.join('').includes(secretCode)) {
      console.log('DING DING')
      cornify_add()
    }
  })
```