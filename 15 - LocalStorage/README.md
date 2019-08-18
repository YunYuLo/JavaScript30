![](https://javascript30.com/images/JS3-social-share.png)

# JavaScript30

Starter Files + Completed solutions for the JavaScript 30 Day Challenge.

Grab the course at [https://JavaScript30.com](https://JavaScript30.com)

## local storage

- about: localStorage
  - localStorage.setItem('Key', Value)
  - localStorage.getItem(Value)
  - localStorage.removeItem
- JSON
  - (JSON.parse())[https://www.w3schools.com/js/js_json_parse.asp] : When we request JSON from the server by using an AJAX request. As long as the response from the server is written in **JSON format**, we can **parse the string into a JavaScript object**.
  - (JSON.stringify())[https://www.w3schools.com/js/js_json_stringify.asp] : When sending data to a web server, the data has to be a string. **Convert a JavaScript object into a string with JSON.stringify()**.


- set variable
```javascript
  const addItems = document.querySelector('.add-items');
  const itemsList = document.querySelector('.plates');
  const items = JSON.parse(localStorage.getItem('items')) || [];
```

- addItem
```javascript
function addItem(e) {
    e.preventDefault() 
    const text = this.querySelector('[name="item"]').value
    const item = {
      text,
      done : false,
    }
    items.push(item)
    localStorage.setItem('items', JSON.stringify(items))
    populateList(items, itemsList)
    this.reset()
  }
  addItems.addEventListener('submit', addItem)

```

- populateList
```javascript
function populateList(plates = [], plateList) {
    // console.log(plates) //items -array
    // console.log(plateList) //itemsList -html elements
    plateList.innerHTML = plates.map((plate, i) => {
      return`
      <li>
        <input type="checkbox" data-index=${i} id="item${i}" ${plate.done ? 'checked' : ''}/>
        <label for="item${i}">${plate.text}</label>
      </li>
      `
    }).join('')
  }
```
  - hook `<input>` and `<label>` with `id="item${i}"` and `for="item${i}"` 
  - whether the item should be checked? `${plate.done ? 'checked' : ''}`

- toggleDone
```javascript
function toggleDone(e) {
    if (!e.target.matches('input')) return
    const index = e.target.dataset.index
    items[index].done = !items[index].done
    localStorage.setItem('items', JSON.stringify(items))
    populateList(items, itemsList)
  }
  itemsList.addEventListener('click', toggleDone)  
```


## Challenge
- check them all
- uncheck them all
- remove each item
- clear all
- (press shift to select multiple items)[https://stackoverflow.com/questions/659508/how-can-i-shift-select-multiple-checkboxes-like-gmail/659571#659571]