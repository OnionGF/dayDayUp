
# js运行机制和事件循环
## 要先说几个概念：

- 任务队列分为macro-task（宏任务）与micro-task（微任务），在最新的标准中，分别被称为task和jobs。

- 事件循环顺序：
事件循环的顺序，决定js代码的执行顺序。一段代码块就是一个宏任务。进入整体代码(宏任务)后，开始第一次循环。接着执行所有的微任务。然后再次从宏任务开始，找到其中一个任务队列执行完毕，再执行所有的微任务。

- 主线程（宏任务） => 微任务 => 宏任务 => 主线程
从上往下  碰到宏任务执行宏任务 碰到微任务执行微任务

#### 宏任务
- setTimeout
- setInterval
- I/O
- script代码块

#### 微任务
- nextTick
- callback
- Promise
- process.nextTick
- Object.observe
- MutationObserver

### 一、何为js运行机制呢？
js主线程拥有一个执行栈和一个任务队列，主线程会依次执代码，
1、当遇到函数（同步）时，会先将函数入栈，函数执行结束再将该函数出栈
2、当函数遇到异步任务时（promise，setTimeout等）时，这些任务会返回一个值，让主线程不在此阻塞，是主线程继续执行下去，而真正的异步任务交给浏览器内核执行，浏览器内核执行结束后，会将该任务事先定好的回调函数加入到相应的任务队列中，任务队列中亦有对应的执行顺序、下面会详说。
3、当主线程清空执行栈后，会按先入先出的顺序读取任务队列中的回调函数(异步任务)，并将该函数入栈，继续运行执行栈，直到清空执行栈，再去读取任务队列，这个也称js的event loop（事件循环机制）


```js

async function async1() {
            console.log('1');
            await async2();
            console.log('2');
        }
        async function async2() {
            console.log('3');
        }
        console.log('4');
        setTimeout(function() {
            console.log('5');
        }, 200);
        setTimeout(function() {
            console.log('6');
            new Promise(function(resolve) {
                resolve();
            }).then(function() {
                console.log('7')
            })
            new Promise(function(resolve) {
                console.log('8');
                resolve();
            }).then(function() {
                console.log('9')
            })
        },0)
        async1();
        new Promise(function(resolve) {
            console.log('10');
            resolve();
        }).then(function() {
            console.log('11');
        });
        console.log('12');

        // console.log(4,1,3,10,12,2,11,6,8, 7,9,5)
```