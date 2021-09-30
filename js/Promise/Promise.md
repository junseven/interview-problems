## Promise的立即执行性
## Promise 三种状态
pending:刚创建完 fufilled  rejected
## Promise 状态的不可逆性
## 链式调用
## Promise then() 回调异步性
* Promise接收的函数参数是同步执行的，但then方法中的回调函数执行则是异步的，因此，"success"会在后面输出。

## Promise的异常
* Promise中的异常由then参数中第二个回调函数（Promise执行失败的回调）处理，异常信息将作为Promise的值。异常一旦得到处理，then返回的后续Promise对象将恢复正常，并会被Promise执行成功的回调函数处理。另外，需要注意p1、p2 多级then的回调函数是交替执行的 ，这正是由Promise then回调的异步性决定的。

## Promise.resolve()
* Promise.resolve(...)可以接收一个值或者是一个Promise对象作为参数。当参数是普通值时，它返回一个resolved状态的Promise对象，对象的值就是这个参数；当参数是一个Promise对象时，它直接返回这个Promise参数。因此，p1 === p2。但通过new的方式创建的Promise对象都是一个新的对象，因此后面的三个比较结果都是false。另外，为什么p4的then最先调用，但在控制台上是最后输出结果的呢？因为p4的resolve中接收的参数是一个Promise对象p1，resolve会对p1”拆箱“，获取p1的状态和值，但这个过程是异步的，可参考下一节。


## resolve vs reject
* Promise回调函数中的第一个参数resolve，会对Promise执行"拆箱"动作。即当resolve的参数是一个Promise对象时，resolve会"拆箱"获取这个Promise对象的状态和值，但这个过程是异步的。p1"拆箱"后，获取到Promise对象的状态是resolved，因此fulfilled回调被执行；p2"拆箱"后，获取到Promise对象的状态是rejected，因此rejected回调被执行。但Promise回调函数中的第二个参数reject不具备”拆箱“的能力，reject的参数会直接传递给then方法中的rejected回调。因此，即使p3 reject接收了一个resolved状态的Promise，then方法中被调用的依然是rejected，并且参数就是reject接收到的Promise对象。

作者：艾特老干部
链接：https://juejin.cn/post/6844903488695042062
来源：掘金
著作权归作者所有。商业转载请联系作者获得授权，非商业转载请注明出处。