![image-20200427012444793](C:\Users\12855\AppData\Roaming\Typora\typora-user-images\image-20200427012444793.png)

![image-20200427014218821](C:\Users\12855\AppData\Roaming\Typora\typora-user-images\image-20200427014218821.png)



1、分析URL：

用 `indexOf` 定位 `?` 的位置，再用 `substr` 得到 `?` 后面的字符串

对于所得字符串，用两次 `split` 方法，分离出各种属性以及属性对应的名称和值，然后判断出 `name` 对应的值即可



2、函数定时触发：

```javascript
var fun = window.setInterval("timeTest()", 5000);
var date = new Date();
var limit = 60000 - date.getTime() % 60000
setTimeout(function () {
    window.clearInterval(fun);
}, limit >= 50000 ? 50000 : limit);
```

`setInterval` ：设置事件和触发间隔

`clearInterval`：事件停止触发

`setTimeOut`：传递包含 `clearInterval` 方法的函数以实现设置事件停止时间

`60000-date.getTime() % 60000` ：到达下一个整分钟需要的毫秒数

通过比较5秒和到达下一个整分钟需要的毫秒数，可以达到【每隔五秒运行一次函数直到某一整分钟停止或者运行10次，先到的为准】的效果



3、判断字符出现次数

建立一个长度为256的数组，每一位用来存ASCII码相当于数组索引的字符的数量

用 `charCodeAt` 得到字符串中某处字符的 ascii 码 ，用 `String.fromCharCode` 还原成字符

