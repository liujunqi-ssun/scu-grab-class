# scu抢课脚本（js版）
2024/03/13更新
之前有过一个python版[link](https://github.com/liujunqi-ssun/URPHelper.git)，但是教务处的接口变更较大，那个维护起来就有些复杂了。

就对照接口更改了另一个版本的js脚本

```javascript
const kch = '你想抢的课的课程号'
const kxh = '你想抢的课序号（如：03）'
const d = document.getElementById("ifra").contentWindow.document
d.getElementById("kch").value = kch
const interval = setInterval(() => {
    d.getElementById("queryButton").click()
    Array.from(d.getElementById("xirxkxkbody").children).forEach(e => {
        // 确定e下的label元素存在，并且该label包含一个input元素
        const inputElement = e.querySelector('td label input[type="checkbox"]');
        if (inputElement) {
            // 检查input元素的id属性是否以特定的字符串开始
            if (inputElement.id.startsWith(kch + "_" + kxh)) {
                inputElement.click(); // 点击该checkbox
                clearInterval(interval); // 停止interval
                document.getElementById("submitButton").click(); // 点击提交按钮
            }
        }
    });
}, 1000)

```

使用方式就是在自由选课界面，**选中有余量的课程选项！！**然后控制台输入脚本。



想抢多个课就多开几个浏览器标签页！


~~最后一次和选课系统作斗争了，和scu的土豆服务器说再见了！~~
