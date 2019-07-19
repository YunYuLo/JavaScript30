![](https://javascript30.com/images/JS3-social-share.png)

# JavaScript30

Starter Files + Completed solutions for the JavaScript 30 Day Challenge.

Grab the course at [https://JavaScript30.com](https://JavaScript30.com)

# Array Cardio
## [Array.prototype.filter()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/filter)

method creates a new array with all elements that pass the test implemented by the provided function. 篩選出符合條件(return true)的結果。

## [Array.prototype.map()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/map)

method **creates a new array** with the results of calling a provided function on every element in the calling array. 每個元素處理後產出新的Array。

## [Array.prototype.sort()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/sort)

method sorts the elements of an array in place and returns the sorted array. 重新排列組合

The default sort order is built upon converting the elements into strings, then comparing their sequences of UTF-16 code units values.預設為根據字串中的**第一個字母**作升序排列。

## [Array.prototype.reduce()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/Reduce)

method executes a reducer function (that you provide) on each element of the array, resulting in a single output value.

Sum up the instances of each of these

    ```javascript
    const data = ['car', 'car', 'truck', 'truck', 'bike', 'walk', 'car', 'van', 'bike', 'walk', 'car', 'van', 'car', 'truck' ];
    
    const transportation = data.reduce(function(obj, item){
      if (!obj[item]) { //如果item不存在，則新增一個類別入{ }
        obj[item] = 0
      }
      obj[item]++ //如果item重複則+1
      return obj
    }, {})
    console.log(transportation)
    ```

## Array.map() && Array.filter()

由querySelectorAll()獲取到的是一個 NodeList ，而非是 Array 類型的數據，所以並不具有 map 和 filter 這樣的方法，所以如果要進行篩選操作則需要把他轉化成 Array 類型。
    
    ```javascript
    //converting NodeList to Array
    //Method 1: Array.from()
    const category = Array.from(document.querySelectorAll('.mw-category a'))

    //Method 2: [... ]
    const category = [...document.querySelectorAll('.mw-category a'))]
    ```
 利用 map 擷取資料，filter篩選
 
    ````js
    const de = category
       .map(link => link.textContent)
       .filter(streetName => streetName.includes('de'))
    ````
