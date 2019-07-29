#消抖 （debounce）

> 定义： 触发高频事件后n秒内函数只会执行一次，如果n秒内高频事件再次被触发，则重新计算时间

>举个通俗的列子 当我们做输入内容自动检索的时候 如果不做节流就会导致频繁的调用搜索接口 如果用节流，我们就可以让它在用户n秒内没有在输入的时候 执行搜索事件。  

``` c
function debounce (fn, delay) {
    let timer   = null;
    return function () {
    let args = arguments;
    let context = this;
        if (timer) {
            clearTimeout(timer);
            timer = setTimeout(function () {
                fn.apply(context, args);
            }, delay);
        } else {
            timer = setTimeout(function () {
                fn.apply(context, args);
            }, delay);
        }
    }
}
```

#节流（throttle）
>高频事件触发，但在n秒内只会执行一次，所以节流会稀释函数的执行频率

>举个例子 比如点击一次按钮请求某个数据两秒内才能取回数据,那么如果我在两秒内一直点击的话 可能会导致无数个接口被调用，但是我用节流就可以控制，两秒内无论点击几次按钮 只会执行一次事件。  这也是为什么说节流会稀释函数的执行频率

```c
function throttle(fn) {
      let canRun = true; // 通过闭包保存一个标记
      return function () {
        if (!canRun) return; // 在函数开头判断标记是否为true，不为true则return
        canRun = false; // 立即设置为false
        setTimeout(() => { // 将外部传入的函数的执行放在setTimeout中
          fn.apply(this, arguments);
          // 最后在setTimeout执行完毕后再把标记设置为true(关键)表示可以执行下一次循环了。
          //当定时器没有执行的时候标记永远是false，在开头被return掉
          canRun = true;
        }, 500);
      };
    }
```