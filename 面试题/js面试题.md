# 闭包
闭包是由函数以及声明该函数所在词法环境组合而成，在闭包场景下，存在一个函数有权访问另一个函数作用域中的变量。
优点
* 闭包中的变量常驻内存，对于实现某些业务很有帮助，比如计数器之类的。
* 架起了一座桥梁，让函数外部访问函数内部变量成为可能。
* 私有化，一定程序上解决命名冲突问题，可以实现私有变量。

# 原型
每当定义一个对象，对象都会包含一些预定义的属性，其中每个函数对象都有个prototype，这个属性指向函数的原型对象。使用原型对象的好处是 所有对象实例共享它包含的属性和方法。

# 原型链
每个对象都有一个原型对象，通过蛋对的proto属性指向器原型对象，并从中继承方法和属性，原型对象也有原型，这样一层一层最终指向null。这种关系称为原型链，通过原型链一个对象可以拥有定义在其他对象中的属性和方法
