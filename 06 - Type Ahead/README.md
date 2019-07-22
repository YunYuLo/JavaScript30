![](https://javascript30.com/images/JS3-social-share.png)

# JavaScript30

Starter Files + Completed solutions for the JavaScript 30 Day Challenge.

Grab the course at [https://JavaScript30.com](https://JavaScript30.com)

# Search bar
## javascript
    - get data from API
    ```
    fetch(endpoint) //endpoint = API URL
    .then(blob => blob.json()) //response a unreadable obj so need to use '.json' 
    .then(data => cities.push(...data)) //notice the different between const and let , add (...) means the obj spread into cities

    ```

    - RegExp to match the input data
    ```
    function findMatches(wordToMatch, array) { //input two parameter: input word and array
        return array.filter(item => { // using filter to search the match word
            const regex = new RegExp(wordToMatch, 'gi') // *** 'i' uppercase or lowercase
            return item.innerContent.match(regex) || return the data
        })
    }
    ```
    - template：數字格式添加comma
    ```
    function numberWithCommas(x) {
        return x.toString().replace(/\B(?=(\d{3})+(?!\d))/g, ',')
    }
    ```

