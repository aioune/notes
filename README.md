package gather

//数据类一般用于JavaBean的形势下，用数据类
data class ResponseResultBean2(var msg:String,var code:Int,var data:String):Any()
//set get 构造函数 解构操作 copy toString hashCode equals 数据类生成更丰富

//数据类的toString方法默认是已经重写的

/*
一、使用限制
    1. data class 必须要有带参数的构造方法
    2. data class 不能被继承
二、实现区别
普通class
    class ResponseResultBean2(val position :Int)

数据类class
    data class ResponseResultBean2(val position :Int)

两相对比，data class 比 class多实现了toString()、hashCode()、equals()、copy()、component()方法。
hashCode()、equals()是用来比较对象内容是否相同，多用于HashMap等容器中；
toString()是用来打印对象内容；
copy()实现了复制功能；
componentN()提供了快速访问元素的功能。
从上面看data class的功能 class都能实现，data class只是是kotlin提供的具有常用数据model功能的类，用于提升开发效率。

 */
