![](https://javascript30.com/images/JS3-social-share.png)

# JavaScript30

Starter Files + Completed solutions for the JavaScript 30 Day Challenge.

Grab the course at [https://JavaScript30.com](https://JavaScript30.com)

## Follow Along Link Highlighter

```javascript
    const trigger = document.querySelectorAll('a')
    const highlight = document.createElement('span')
    highlight.classList.add('highlight')
    document.body.append(highlight)

    function highlightLink() {
      const linkCoords = this.getBoundingClientRect()
      const coords = {
        width: linkCoords.width,
        height: linkCoords.height,
        top: linkCoords.top + window.scrollY,
        left: linkCoords.left + window.scrollX,
      }
      highlight.style.width = `${coords.width}px`
      highlight.style.height = `${coords.height}px`
      highlight.style.transform = `translate(${coords.left}px, ${coords.top}px)`


      console.log(linkCoords)
    }

    trigger.forEach(a => a.addEventListener('mouseenter', highlightLink))
```

### further reading
[Element.getBoundingClientRect()](https://developer.mozilla.org/zh-CN/docs/Web/API/Element/getBoundingClientRect)

[transform](https://developer.mozilla.org/zh-TW/docs/Web/CSS/transform)