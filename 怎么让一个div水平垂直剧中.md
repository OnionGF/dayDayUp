# 怎么让一个div水平垂直居中？

```c
    <div class="parent">
        <div class="child"></div>
    </div>

    // 1、弹性盒
    div.parent {
        display: flex;
        justify-content: center;
        align-items: center;
    }

    // 2、定位
    div.parent {
        position: relative; 
    }
    div.child {
        position: absolute; 
        top: 50%;
        left: 50%;
        transform: translate(-50%, -50%);  
    }

    // 3、
    div.child {
        width: 50px;
        height: 10px;
        position: absolute;
        top: 50%;
        left: 50%;
        margin-left: -25px;
        margin-top: -5px;
    }
    //4、
    div.child {
        width: 50px;
        height: 10px;
        position: absolute;
        left: 0;
        top: 0;
        right: 0;
        bottom: 0;
        margin: auto;
    }

    //5、
    div.parent {
        display: grid;
    }
    div.child {
        justify-self: center;
        align-self: center;
    }

    // 6、
    div.parent {
        font-size: 0;
        text-align: center;
        &::before {
            content: "";
            display: inline-block;
            width: 0;
            height: 100%;
            vertical-align: middle;
        }
    }
    div.child{
        display: inline-block;
        vertical-align: middle;
    }

    // 7、 
    div.parent{
        display:flex;
    }
    div.child{
        margin:auto;
    }
```