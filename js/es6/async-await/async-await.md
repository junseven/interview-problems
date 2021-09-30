#async/await的知识点

* await只能在async函数中使用，不然会报错
* async函数返回的是一个状态为fuifilled的Promise对象，有无值看有无return值
* await后面只有接了Promise才能实现排队效果
* async/await作用是用同步方式，执行异步操作
