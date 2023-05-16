* 创建一个新对象。new obj = new Object()
* 这个新对象会被执行[[原型]]连接。 obj._proto_ = [].shift.apply(arguments).prototype
* 属性和方法被加入到 this 引用的对象中。并执行了构造函数中的方法. fn.apply(obj,arguments)
* 如果函数没有返回其他对象，那么返回创建的这个新对象，否则返回构造函数的执行结果。typeof res==='Object' ?res:obj 