
## 笛卡尔积算法

> 后台生成sku算法
```c
// 超简单的笛卡尔积算法
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

> 项目需要：升级版

```c

    <script>

        // 笛卡尔积的实现
        const arr =  [
            {
                "id": 35,
                "name": "颜色",
                "chooseValue": [
                    {
                        "id": "1145225013440352258",
                        "text": "红"
                    },
                    {
                        "id": "1145225013440352259",
                        "text": "黄"
                    }
                ]
            },
            {
                "id": 40,
                "name": "尺码",
                "chooseValue": [
                    {
                        "id": "1145225014644117506",
                        "text": "34"
                    },
                    {
                        "id": "1145225014635728898",
                        "text": "32"
                    }
                ]
            },
            {
                "id": 68,
                "name": "宽度",
                "chooseValue": [
                    {
                        "id": "1145225016594468865",
                        "text": "dm"
                    }
                ]
            }
        ]
        function descartes(...args) {
            if (args.length < 2) {
                return args[0] || [];
            }
            return [].reduce.call(args, (col, set) => {
                let res = [];
                if(col instanceof Array){
                    col.forEach(c => {
                        set.chooseValue.forEach(s => {
                            let t = [].concat(Array.isArray(c) ? c : [{[set.id]:s,"text":set.name}]);
                            let S = {}
                            S[set.id] = s
                            S.test = set.name
                            t.push(S);
                            res.push(t);
                        });
                    }); 
                }else{
                    col.chooseValue.forEach(c => {
                        set.chooseValue.forEach(s => {
                            let t = [].concat(Array.isArray(c) ? c : [{[set.id]:s,"text":set.name}]);
                            let S = {}
                            S[col.id] = c
                            S.test = col.name
                            t.push(S);
                            res.push(t);
                        });
                    }); 
                }
                return res;
            });
        }

        console.log(JSON.stringify(descartes(...arr)))
        // 输出生成的sku：
        // [
            // [
            //     {
            //         "40": {
            //             "id": "1145225014644117506",
            //             "text": "34"
            //         },
            //         "text": "尺码"
            //     },
            //     {
            //         "35": {
            //             "id": "1145225013440352258",
            //             "text": "红"
            //         },
            //         "test": "颜色"
            //     },
            //     {
            //         "68": {
            //             "id": "1145225016594468865",
            //             "text": "dm"
            //         },
            //         "test": "宽度"
            //     }
            // ],
            // [
            //     {
            //         "40": {
            //             "id": "1145225014635728898",
            //             "text": "32"
            //         },
            //         "text": "尺码"
            //     },
            //     {
            //         "35": {
            //             "id": "1145225013440352258",
            //             "text": "红"
            //         },
            //         "test": "颜色"
            //     },
            //     {
            //         "68": {
            //             "id": "1145225016594468865",
            //             "text": "dm"
            //         },
            //         "test": "宽度"
            //     }
            // ],
            // [
            //     {
            //         "40": {
            //             "id": "1145225014644117506",
            //             "text": "34"
            //         },
            //         "text": "尺码"
            //     },
            //     {
            //         "35": {
            //             "id": "1145225013440352259",
            //             "text": "黄"
            //         },
            //         "test": "颜色"
            //     },
            //     {
            //         "68": {
            //             "id": "1145225016594468865",
            //             "text": "dm"
            //         },
            //         "test": "宽度"
            //     }
            // ],
            // [
            //     {
            //         "40": {
            //             "id": "1145225014635728898",
            //             "text": "32"
            //         },
            //         "text": "尺码"
            //     },
            //     {
            //         "35": {
            //             "id": "1145225013440352259",
            //             "text": "黄"
            //         },
            //         "test": "颜色"
            //     },
            //     {
            //         "68": {
            //             "id": "1145225016594468865",
            //             "text": "dm"
            //         },
            //         "test": "宽度"
            //     }
            // ]
            // ]

    </script>
  

```