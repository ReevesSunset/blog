### 格式化金额

```javascript
//1. 
function toThousands(num) {
    var result = [ ], counter = 0;
    num = (num || 0).toString().split('');
    for (var i = num.length - 1; i >= 0; i--) {
        counter++;
        result.unshift(num[i]);
        if (!(counter % 3) && i != 0) { result.unshift(','); }
    }
    return result.join('');
}

console.log(toThousands(1000000)) // 1,000,000

//2.
function toThousands(num) {
    var result = '', counter = 0;
    num = (num || 0).toString();
    for (var i = num.length - 1; i >= 0; i--) {
        counter++;
        result = num.charAt(i) + result;
        if (!(counter % 3) && i != 0) { result = ',' + result; }
    }
    return result;
}

//3.
function toThousands(num) {
    var num = (num || 0).toString(), re = /\d{3}$/, result = '';
    while ( re.test(num) ) {
        result = RegExp.lastMatch + result;
        if (num !== RegExp.lastMatch) {
            result = ',' + result;
            num = RegExp.leftContext;
        } else {
            num = '';
            break;
        }
    }
    if (num) { result = num + result; }
    return result;
}

//4
function toThousands(num) {
    var num = (num || 0).toString(), result = '';
    while (num.length > 3) {
        result = ',' + num.slice(-3) + result;
        num = num.slice(0, num.length - 3);
    }
    if (num) { result = num + result; }
    return result;
}

//5
function toThousands(num) {
    var num = (num || 0).toString(), temp = num.length % 3;
    switch (temp) {
        case 1:
            num = '00' + num;
            break;
        case 2:
            num = '0' + num;
            break;
    }
    return num.match(/\d{3}/g).join(',').replace(/^0+/, '');
}

//6
function toThousands(num) {
    return (num || 0).toString().replace(/(\d)(?=(?:\d{3})+$)/g, '$1,');
}

//7
(123456789).toLocaleString('en-US')  // 1,234,567,890

//8
new Intl.NumberFormat().format(1234567890) // 1,234,567,890
```

### 时间的处理

### lazyman实现

### 防抖和节流

> 节流
```javascript
const throttle = function(fn, interval) {
  let last = 0;
  return function (...args) {
    let context = this;
    let now = +new Date();
    // 还没到时间
    if(now - last < interval) return;
    last = now;
    fn.apply(this, args)
  }
}
```

> 防抖
```javascript
function debounce(fn, delay) {
  let timer = null;
  return function (...args) {
    let context = this;
    if(timer) clearTimeout(timer);
    timer = setTimeout(function() {
      fn.apply(context, args);
    }, delay);
  }
}

```

> 结合
```javascript
function throttle(fn, delay) {
  let last = 0, timer = null;
  return function (...args) {
    let context = this;
    let now = new Date();
    if(now - last < delay){
      clearTimeout(timer);
      setTimeout(function() {
        last = now;
        fn.apply(context, args);
      }, delay);
    } else {
      // 这个时候表示时间到了，必须给响应
      last = now;
      fn.apply(context, args);
    }
  }
}
```