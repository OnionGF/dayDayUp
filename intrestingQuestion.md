>1、编程题，找出字符串中连续出现最多的字符和个数（蘑菇街）
``` c
const str = 'abdfgh*777633&&^^%%@^^^^jk'
const arr = str.match(/(.)\1*/g);// 将字符串通过正则分组为数组 
const maxLen = Math.max(...arr.map(s => s.length));// 返回最大长度的数值
const result = arr.reduce((pre, curr) => {
    console.log('pre',pre,curr)
    if (curr.length === maxLen) {
        pre[curr[0]] = curr.length;
    }
    return pre;
}, {});
console.log(result);

// 这个解法使用了正则、数组的一些方法

```