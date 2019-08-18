![](https://javascript30.com/images/JS3-social-share.png)

# JavaScript30

Starter Files + Completed solutions for the JavaScript 30 Day Challenge.

Grab the course at [https://JavaScript30.com](https://JavaScript30.com)

## regular expression and array.sort


按字母順序排列字串，並忽略an/ a/ the.

- further study about regular expression
  - (正規表示式 Regular Expression)[https://poychang.github.io/note-regular-expression/]
  - (MDN正規表達式)[https://developer.mozilla.org/zh-TW/docs/Web/JavaScript/Guide/Regular_Expressions]
  - (用 Regular Expression 做字串比對)[https://larry850806.github.io/2016/06/23/regex/]
  - (JavaScript Regular Expression Visualizer)[https://jex.im/regulex/#!flags=&re=%5E(a%7Cb)*%3F%24]
- what we use here
  - `^`: where we start
  - `i`: ignore case
  - `|`: or
- what we do here
```javascript
function strip(bandName) {
  return bandName.replace(/^(a |an |the )/i, '').trim()
}

const sortedBands = bands.sort((a, b) => strip(a) > strip(b)? 1 : -1)

document.querySelector('#bands').innerHTML = 
  sortedBands.map(band => `<li>${band}</li>`).join('')

console.log(sortedBands)
```


