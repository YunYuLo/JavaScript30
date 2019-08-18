![](https://javascript30.com/images/JS3-social-share.png)

# JavaScript30

Starter Files + Completed solutions for the JavaScript 30 Day Challenge.

Grab the course at [https://JavaScript30.com](https://JavaScript30.com)

## how to add "time"

- get time data from DOM
```javascript
const timeNodes = Array.from(document.querySelectorAll('[data-time]'))
  const seconds = timeNodes
    .map(node => node.dataset.time)
    .map(timeCode => {
      const [mins, secs] = timeCode.split(':').map(parseFloat)
      return (mins*60) + secs
    })
    .reduce ((total, vidSeconds) => total + vidSeconds)
```

  - notice that
    - querySelectorAll will return `NodeList`, so using `Array.form()` or `[...]` to convert NodeList to Array
    - following that we can use `.map()` method
    - then using `string.split()` to get mins and secs
    - but this method only reutrn `string` so attribute `.map(parseFloat)` to convert the feature to number
    - finally we got pure number of seconds of time