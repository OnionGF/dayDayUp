
## 笛卡尔积算法

```c
    const arr =  [
            [ '高', '低'],
            [  '24G', '48G'],
            [ '红', '黄', '蓝']
        ]
        function cartesianProductOf() {
            return Array.prototype.reduce.call(arguments,    function(a, b) {
                var ret = [];
                a.forEach(function(a) {
                    b.forEach(function(b) {
                        ret.push(a.concat([b]));
                    });
                });
                return ret;
            }, [[]]);
        }
        console.log(JSON.stringify(cartesianProductOf(...arr)))
        // [
        //    ["高","24G","红"],["高","24G","黄"],
        //    ["高","24G","蓝"],["高","48G","红"],
        //    ["高","48G","黄"],["高","48G","蓝"],
        //    ["低","24G","红"],["低","24G","黄"],
        //    ["低","24G","蓝"],["低","48G","红"],
        //    ["低","48G","黄"],["低","48G","蓝"]
        // ]
        
```