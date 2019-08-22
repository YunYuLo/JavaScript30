![](https://javascript30.com/images/JS3-social-share.png)

# JavaScript30

Starter Files + Completed solutions for the JavaScript 30 Day Challenge.

Grab the course at [https://JavaScript30.com](https://JavaScript30.com)

## catch mousemove with css animation

- get element's width and height
  - HTMLElement.offsetHeight
  - HTMLElement.offsetWidth
- get the position of mousemovement
  - MouseEvent.offsetX
  - MouseEvent.offsetY
- 2ways to define variables

1.
```javascript
  const width = hero.offsetWidth 
  const height = hero.offsetHeight
  let x = e.offsetX
  let y = e.offsetY
```

2.

```javascript
  const { offsetWidth: width, offsetHeight: height } = hero
  let { offsetX: x, offsetY: y } = e
```
- function

```javascript
  const hero = document.querySelector('.hero')
  const text = hero.querySelector('h1')

  function shadow(e) {
    const { offsetWidth: width, offsetHeight: height } = hero
    let { offsetX: x, offsetY: y } = e
    const walk = 100 // 100px
    if(this !== e.target) {
      x = x + e.target.offsetLeft
      y = y + e.target.offsetTop
    }

    const xWalk = Math.round((x/width*walk) - (walk/2))
    const yWalk = Math.round((y/height*walk) - (walk/2))
    
    text.style.textShadow = `${xWalk}px ${yWalk}px 0 red`
  }

  hero.addEventListener('mousemove', shadow)
```


