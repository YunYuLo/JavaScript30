![](https://javascript30.com/images/JS3-social-share.png)

# JavaScript30

Starter Files + Completed solutions for the JavaScript 30 Day Challenge.

Grab the course at [https://JavaScript30.com](https://JavaScript30.com)

#HTML
- [HTML <input> type](https://www.w3schools.com/tags/att_input_type.asp)

#css
- 在css的:root設定variable，並且對img設定樣式的參數來自root variable
- [:root](https://developer.mozilla.org/zh-CN/docs/Web/CSS/:root) can be useful for declaring global CSS variables
- [CSS Variables](https://www.w3schools.com/css/css3_variables.asp)
    ```css
    :root {
    --main-bg-color: coral; 
    }

    #div1 {
    background-color: var(--main-bg-color); 
    }
    ```
- [filter](https://developer.mozilla.org/zh-CN/docs/Web/CSS/filter) CSS property applies graphical effects like blur or color shift to an element. Filters are commonly used to adjust the rendering of images, backgrounds, and borders.

#JS
- DOM selector 挑出所有input > addEventListener to every movement of input > function handleUpdate()
- document.querySelector('.class tags') which returns prototype as *NodeList*
- [NodeList.prototype.forEach()](https://developer.mozilla.org/en-US/docs/Web/API/NodeList/forEach)
    - more methods: entries(), item(), keys(), values()
- [CSSStyleDeclaration.setProperty()](https://developer.mozilla.org/en-US/docs/Web/API/CSSStyleDeclaration/setProperty)method interface sets a new value for a property on a CSS style declaration object.
- [Document.documentElement](https://developer.mozilla.org/zh-TW/docs/Web/API/Document/documentElement)returns the Element that is the root element of the document (for example, the <html> element for HTML documents).