![](https://javascript30.com/images/JS3-social-share.png)

# JavaScript30

Starter Files + Completed solutions for the JavaScript 30 Day Challenge.

Grab the course at [https://JavaScript30.com](https://JavaScript30.com)

## Slide in on Scroll

- 取得視窗維度資料
  - window物件上可取得
    1. innerWidth、innerHeight：視埠區域的寬/高（不包括選單、工具列、捲軸）
    2. outerWidth、outerHeight：瀏覽器視窗的寬/高
    3. scrollX、scrollY：水平轴X/垂直軸Y上document已经被捲去的宽度/高度(單位像素)
    4. screenX、screenY：瀏覽器視窗在螢幕中的位置
  - DOM上可取得
    1. offsetTop：當前元素相對於其 (offsetParent)[https://developer.mozilla.org/zh-CN/docs/Web/API/HTMLElement/offsetParent] 元素的頂部的距離
    2. offsetHeight：returns the height of an element, including vertical padding and borders, as **an integer**
  -補充
    1. (javascript中与Scroll有关的知识点)[https://github.com/hehongwei44/my-blog/issues/207]

- 實務操作
```javascript
  function checkSlide(e) {
    sliderImages.forEach(sliderImage => {
      //取得距離
      const slideInAt = (window.scrollY + window.innerHeight) - sliderImage.height / 2
      const imageBotton = sliderImage.offsetTop + sliderImage.height
      //設定圖片顯示的情況
      const isHalfShown = slideInAt > sliderImage.offsetTop 
      const isNotScrolledPast = window.scrollY < imageBotton
      if (isHalfShown && isNotScrolledPast){
        sliderImage.classList.add('active')
      } else {
        sliderImage.classList.remove('active')
      }
    })
  ``` 

## (Debounce 和 Throttle)[https://mropengate.blogspot.com/2017/12/dom-debounce-throttle.html]

**網頁DOM效能優化**
```javascript
//讓一個函式在連續觸發時只執行一次
function debounce(func, wait = 20, immediate = true) {
  var timeout;
  return function() {
    var context = this, args = arguments;
    var later = function() {
      timeout = null;
      if (!immediate) func.apply(context, args);
    };
    var callNow = immediate && !timeout;
    clearTimeout(timeout);
    timeout = setTimeout(later, wait);
    if (callNow) func.apply(context, args);
  };
}

//控制函數最高呼叫頻率
function throttle(func, threshhold) {
  var last, timer;
  if (threshhold) threshhold = 250;
  return function () {
    var context = this
    var args = arguments
    var now = +new Date()
    if (last && now < last + threshhold) {
      clearTimeout(timer)
      timer = setTimeout(function () {
        last = now
        func.apply(context, args)
      }, threshhold)
    } else {
      last = now
      fn.apply(context, args)
    }
  }
}
```