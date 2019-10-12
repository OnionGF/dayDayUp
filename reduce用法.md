# reduce用法

```
var numbers = [65, 44, 12, 4];
 
function getSum(total, num) {
    return total + num;
}
function myFunction(item) {
    document.getElementById("demo").innerHTML = numbers.reduce(getSum);
}
```

```
let arr = [1,2,3,4,5,6,7]
let sum = arr.reduce((total, num)=>{
    return total+num
})
console.log('sum',sum)

```

123