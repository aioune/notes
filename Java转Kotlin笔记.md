# Kotlin

### 第一阶段

### Kotlin语言声明变量与内置数据类型

``` Kotlin
package main.kotlin

//声明变量与内置数据类型
fun main() {
    println("hello World");

    //  TODO ========声明变量
    /*
        可读可改    变量名     类型      值
        var        name  ： String = "Derry"
    * */
    var name:String ="Derry";

    //  name = "Lance"
    name="Lance";
    println(name);

    // TODO ========内置数据类型
    /*
        String              字符串
        Char                单字符
        Boolean             true/false
        Int                 整形
        Double              小数
        Set                 无重复的元素集合
        Map                 键值对的集合

        Int     --->    java int
        Float   --->    java float
    * */

    
}
```

### Kotlin语言的只读变量

* var：可读可写
* val：只读

### Kotlin的类型推断

``` kotlin
fun main(){
    //Kotlin可以根据变量值智能推导变量类型
    var info:String = "dsaf";
    var info1="dsfas";
}
```

### Kotlin语言的编译时常量

``` kotlin
const val PI=3.1415 //定义编译时常量
fun main(){

    //TODO Kotlin语言的编译时常量
    //编译时常量只能是常用的基本数据类型（包含String）

    //const不适用于局部变量，因为如果在函数内定义，就必须在运行时才能调用函数赋值。
    //const val PI=3.1415   //报错

}
```

### Kotlin语言的regin表达式

#### if

``` kotlin
fun main(){
   var number=148
    // range 范围 从哪里 到哪里
    if(number in 0..59){
        println("不及格");
    }else if(number in 60..100){
        println("及格");
    }else if(number !in 0..100){
        println("不在范围内");
    }
}
```

#### when

``` kotlin
val week=5
    //类似与java的switch
    //当When中返回类型不统一时，info为Any类型（Any相当于java中的Object类型）
    val info=when(week){
        1->"今天是周一"
        2->"今天是周二"
        3->"今天是周三"
        4->"今天是周四"
        5->"今天是周五"
        6->"今天是周六"
        7->"今天是周日"
        else ->{
            println("星期错误")
        }
    }
```

### Kotlin语言的String模板

``` kotlin
val garden="黄石公园"
val time = 6
//如果需要和字符串紧挨着需要：${garden}，否则$time 空格
println("今天天清气朗，去${garden}玩，完了$time 小时")

val isLogin=true
println("Server Response result：${if(isLogin) "恭喜你，登录成功" else "不共享，登录失败，请检查Request信息"}")
```

### Kotlin语言的函数头

![image-20220418135627983](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220418135627983.png)

### Kotlin语言的具名函数参数

``` kotlin
fun main(){
    loginAction(age=19, userpwd = "1243", username = "dasf")
}
private fun loginAction(username:String ,userpwd:String,age : Int){
    println("$username,$userpwd,$age")
}
```

#### Kotlin语言的Unit函数特点

**Unit==void**

**Unit**不写默认也有

#### Kotlin语言的Nothing类型特点

``` kotlin
fun main(){
    show(-1)
}
private fun show(number:Int){
    when(number){
        //类似于抛出异常,如果不是注释提示，会终止程序的
        -1-> TODO("没有这种分数")
        in 0..59 -> println("分数不及格")
        in 60..70 -> println("分数及格")
        in 71..100 -> println("分数优秀")
    }
}
```

### Kotlin语言的反引号中函数名特点

``` kotlin
fun main(){
    //第一种情况，当函数名使用
    `登录功能 2022年测试环境下 测试登录功能`("123","213")
    //第二种情况，in is 在kt中为关键字，可用 ` ` 包裹
    KtBase21.`is`()
    //第三种情况，与第一种类似。对函数名加密
}
private fun `登录功能 2022年测试环境下 测试登录功能`(password:String,username:String){
    println("$password,$username")
}
```

## 第二阶段（匿名函数&Lambda）

### Kotlin语言的匿名函数学习

``` kotlin
package two
// TODO 匿名函数学习
fun main(){
    val len="Derry".count()
    println(len)

    val len2="Derry".count{
        //it等价于 D e r r y 的字符 Char
        //返回字符中等价于'r'的个数
        it=='r'
    }
}
```

### Kotlin语言的函数类型&隐式返回

``` kotlin
package two
// TODO 匿名函数学习
fun main(){
    //我们现在在写函数
    //第一步：函数输入输出的声明
    val methodAction:()->String
    //第二步：对上面函数的实现
    methodAction={
        val inputValue=99999
         //返回最后一行String语句
        "$inputValue Derry"
    }
    //第三步：调用此函数
    println(methodAction())
}
```

### Kotlin语言的函数参数学习

``` kotlin
package two
// TODO 匿名函数参数学习
fun main(){
    //我们现在在写函数
    //第一步：函数输入输出的声明
    val methodAction:(Int,Int,Int) -> String={
        number1,number2,number3->
        val inputValue=99999
        //返回最后一行String语句
        "$inputValue Derry,number1:$number1,number2:$number2,number3:$number3"

    }
    //第二步：调用此函数
    println(methodAction(1,2,3))
}
```

### Kotlin的it关键字

``` kotlin
package two
// TODO it关键字
fun main(){
    //第一步：函数输入输出的声明
    val methodAction:(Int) -> String={
        //用it自动识别替代只有一个参数的函数形参
        "$it"
    }
    //第二步：调用此函数
    println(methodAction(1))
}
```

### Kotlin语言的匿名函数的类型推断

``` kotlin
package two
// TODO 匿名函数的参数推断
fun main(){
    //匿名函数，类型推断为String
    //方法名：必须指定 参数类型 和 返回类型
    //方法名 = 类型推断返回类型
    val methodAction ={
        number1:Int,number2:Int,number3:Int->
        val inputValue=99999
        //返回最后一行String语句
        "$inputValue Derry,number1:$number1,number2:$number2,number3:$number3"
    }//method1 函数：（Double,Float,Int) -> String

    println(methodAction(1,2,3))

    val method2={
        3432.213
    }
    println(method2())

    val method3={
        number:Int->
        number
    }
    println(method3(9))
}
```

### Kotlin语言的lambda学习

``` kotlin
package two
// TODO lambda学习
fun main(){
    val addResultMethod={number:Int,number1:Int->
        "${number+number1}"
    }
    println(addResultMethod(6,9))

}
```

### 定义参数是函数的函数

```kotlin
package two
// TODO lambda学习
fun main(){
    loginAPI("Derry","12346"){
        msg:String,code:Int->
        println("information:msg:$msg,code:$code")
    }
}
//模拟：数据库SQLServer
const val USER_NAME_SAVE_DB = "Derry"
const val USER_PWD_SAVE_DB = "123456"

//登录API 模仿 前端
fun loginAPI(username:String,userpwd:String,resposeResult:(String,Int)->Unit){
    if(username==null||userpwd==null){
        TODO("用户名或者密码为null")//出现问题，终止程序
    }
    //做很多的校验 前端校验
    if(username.length>3&&userpwd.length>3){
        if(wbeServiceLoginAPI(username,userpwd)){
            //登录成功
            resposeResult("login success",200)
        }else{
            resposeResult("login fail",400)
        }

    }else{
        TODO("用户名或者密码不合格")//出现问题，终止程序
    }
}
//登录的API暴露者 服务器
private fun wbeServiceLoginAPI(name:String,pwd:String):Boolean{
    //在kotlin中if是表达式，可以前置return
    return if(name== USER_NAME_SAVE_DB && pwd== USER_PWD_SAVE_DB) true else false

}
```

### Kotlin语言的简略写法

``` kotlin
package two
// TODO Kotlin语言的简略写法演变过程
fun main(){
    //第一种方式
    loginAPI("Derry","123456",{msg:String,code:Int->
        println("information:msg:$msg,code:$code")
    })
    //第二种方式
    loginAPI("Derry","12346",resposeResult={
            msg:String,code:Int->
        println("information:msg:$msg,code:$code")
    })
    //第三种方式
    loginAPI("Derry","12346"){
        msg:String,code:Int->
        println("information:msg:$msg,code:$code")
    }
}
//模拟：数据库SQLServer
const val USER_NAME_SAVE_DB = "Derry"
const val USER_PWD_SAVE_DB = "123456"

//登录API 模仿 前端
fun loginAPI(username:String,userpwd:String,resposeResult:(String,Int)->Unit){
    if(username==null||userpwd==null){
        TODO("用户名或者密码为null")//出现问题，终止程序
    }
    //做很多的校验 前端校验
    if(username.length>3&&userpwd.length>3){
        if(wbeServiceLoginAPI(username,userpwd)){
            //登录成功
            resposeResult("login success",200)
        }else{
            resposeResult("login fail",400)
        }

    }else{
        TODO("用户名或者密码不合格")//出现问题，终止程序
    }
}
//登录的API暴露者 服务器
private fun wbeServiceLoginAPI(name:String,pwd:String):Boolean{
    //在kotlin中if是表达式，可以前置return
    return if(name== USER_NAME_SAVE_DB && pwd== USER_PWD_SAVE_DB) true else false

}
```

## 运算符

### in与contains

``` kotlin
val list =listof(1,2,3,4)

2 in list
//list.contains(2)
```

### []与get

``` kotlin
val map=mapOf(
    "Hello" to 2
    "World" to 3
)
val value = map["Hello"]
// val value = map.get("Hello")
```

### []与get

``` kotlin
val map=mapOf(
    "Hello" to 2
    "World" to 3
)
map["World"] = 4
// map.set("World",4)
```

### >与compareTo

``` kotlin
2>3
//2.compareTo(3)>0
```

### ()与invoke

``` kotlin
val func = fun(){
    println("hello")
}

func()
//func.invoke()
```

## 中缀表达式

### 2 to 3

``` kotlin
fun main(){
    book on desk
    //book.on(desk)
}
class Book
class Desk
//开头以infix修饰才可以使用中缀表达式
infix fun Book.on(desk:Desk){
    
}
```

## 内联函数

如果此函数， 不使用内联，在调用端，会生成多个对象来完成lambda的调用（会造成性能损耗）

如果此函数，使用内联，相当于C++ #define 宏定义 宏替换，会把代码替换到调用处 没有任何函数开辟 对象开辟 的损耗

所以 如果函数参数有lambda，尽量使用inline（内联函数）

#### crossinline

禁止 non-local return

#### inline

内联函数标识

#### noinline

禁止函数参数被内联

### 内联属性

没有backing-field的属性的getter/setter可以被内联

### 内联函数的限制

public/protected的内联方法只能访问对于类的public成员

内联函数的内联函数参数不能被存储

内联函数的内联函数参数只能传递给其他内联函数参数

## 第二阶段

### 函数引用

lambda属于函数类型的对象，需要把methodResponseResult普通函数变成 函数类型的对象（函数引用）

``` kotlin
package three

fun main() {
    // TODO ::符号可以将函数转变为函数类型进行传参
    val obj=::methodResponseResult;
    loginAPI("Derry","123456",obj)
    loginAPI("Derry","123456",::methodResponseResult)
}

fun  methodResponseResult(msg:String,code:Int){
    println("msg=$msg,code=$code")
}
//模拟：数据库SQLServer
const val USER_NAME_SAVE_DB = "Derry"
const val USER_PWD_SAVE_DB = "123456"

//登录API 模仿 前端
fun loginAPI(username:String,userpwd:String,resposeResult:(String,Int)->Unit){
    //做很多的校验 前端校验
    if(username.length>3&&userpwd.length>3){
        if(USER_NAME_SAVE_DB==username&&userpwd== USER_PWD_SAVE_DB){
            //登录成功
            resposeResult("login success",200)
        }else{
            resposeResult("login fail",400)
        }

    }else{
        TODO("用户名或者密码不合格")//出现问题，终止程序
    }
}
```

### 将函数类型作为返回类型

``` kotlin
fun mian(){
    val result = showAction()
    println(result(33,130.0))
}

private fun showAction():(Int,Double) ->String{
    val name="Derry"
    return {
        age:Int,weight:Double->
        val thisInfo="(今年是2021年)"
        "我的名字是：$name.${thisInfo},我的年龄是:$age,我的体重是:${weight}斤"
    }
}
```

``` kotlin
package three

fun main() {
    val showMethod = showMethod("Derry")
    //返回接受的函数变量一样可以当函数正常使用
    println(showMethod("Array",14))
}

fun showMethod(info : String):(String,Int)->String{
    println("info=$info")
    //返回匿名函数
    return {name:String,age:Int->
       "name=$name,age=$age"
    }
}
```

### Kotlin语法中异常处理与自定义异常特点

``` kotlin
fun main(){
    try{
        var info:String?=null
        checkException(info)
        println(info!!.length)
    }catch(e:Exception){
        println("啊呀：$e")
    }
}
fun checkException(info:String){
    info?:thirow CustomException()
}
class CustomException :IllegalArgumentException("你的代码太不严谨了")
```



## Kotlin语言对空值相关操作

### Kotlin语言的安全调用操作符（?）

``` kotlin
fun main(){
    //var name:String		//普通声明变量，变量不能为空值
    var name:String?
    name="zhangsan"
    name=null
    name?.capitalize()//name是可空类型的 如果真的是null，？后面这段代码不执行
}
```

### Kotlin中使用带let的安全调用（?.let）

``` kotlin
fun main(){
    var name:String?=null
    val r=name?.let{
        //it==name本身
        //如果能执行到这里的，it一定不为null
       if(it.isBlank()){//如果name是空值 "" 没有内容
           "Default"
       }else{
           "[$it]"
       }
    }
    println(r)
}
```

### Kotlin语言中的非空断言操作符特点（!!）

```kotlin
fun main(){
    var name:String?=null
    val r=name!!.capitalize()	//!!断言 不管那么是不是null，都执行，这个和java一样
    println(r)
    //结论：如果百分百能够保证name是有值的，那么才能使用断言!!，否则有java空指针风险
}
```

### Kotlin空合并操作符（?:）

``` kotlin
fun main(){
    var info:String?="李小龙"
    info=null
    //空合并操作符，变量为空时执行后续操作
    println(info ?: "原来你是null啊")
    //let函数 + 空合并操作符
    println(info?.let{"[$it]"}?:"原来你是null啊2")
}
```

## 内置函数介绍

### SubString函数（字符串拼接）

``` kotlin
const val INFO = "Derry is Success Result"
fun mian(){
    val indexof=INFO.indexof('i')
    //平常写法
    println(Info.substring(0,indexof))
    //Kotlin常用写法 0 - indexof
    println(Info.substring(0 until indexof))
}
```

### split操作（字符串截取）

``` kotlin
fun main(){
    val jsonText="Derry,leo,lance,Alvin"
    //list 自动推断乘 list==List<String>
    val list = jsonText.split(",")
    
    //直接输出 list 集合，不解构
    println("分割后的list里面的元素有:$list")
    
    //C++解构 Kt也有解构
    val (v1,v2,v3,v4)=list
    println("v1:$v1,v2:$v2,v3:$v3,v4:$v4")
}

/*
控制台输出结果：
分割后的list里面的元素有:[Derry, leo, lance, Alvin]
v1:Derry,v2:leo,v3:lance,v4:Alvin
*/
```

### 字符串遍历操作

``` kotlin
fun main(){
    cal str="sdafasdfasdgrghjgfhsdf"
    str.forEach{
        //it==str的每一个字符
        print("所有的字符是:$it ")
    }
}
```

### Kotlin语言中数字类型的安全转换函数

``` kotlin
fun main(){
    //val number="666"
    val number:Int="666".toInt()
    //字符串里面放入了Double类型，无法转换成Int，会崩溃
    //val numbe2r:Int="666.6".toInt()
    //解决了奔溃的问题，当转换不成功时自动返回空值
    val number2:Int?="666.6".toIntOrNull()
    println(number2)
    val number3:Int?="666".toIntOrNull()
    println(number3)
}
```

#### Kotlin语言中Double转Int与类型格式化

``` kotlin
fun main(){
    println(65.2345.toInt())	//65 四舍五入
    println(65.4444.roundToInt())	//65 四舍五入
    println(65.8888.roundToInt())	//66 四舍五入
    //用roundToInt()函数，保证Double->转Int持有四舍五入的效果
    val r = "%.3f".format(65.8343433)		//65.834
}
```

### Kotlin语言中apply的使用

``` kotlin
package three

fun main(){
    val info="Derry you hao"

    //普通的方式
    println("info字符串的长度是：${info.length}")
    println("info最后一个字符是：${info[info.length-1]}") //拿到最后一个字符
    println("info全部转成小写是：${info.toLowerCase()}")

    //apply内置函数的方式
    //apply特点：apply始终返回info本身
    val infoNew:String = info.apply {
        //一般大部分情况下，匿名函数都会持有一个it，但是apply函数不会持有it，却会持有当前this
        println("info字符串的长度是：${this.length}")
        println("info最后一个字符是：${this[this.length-1]}") //拿到最后一个字符
        println("info全部转成小写是：${this.toLowerCase()}")
    }
    println("apply返回的值：$infoNew")
    
    //apply的正确用法
    val infoNew:String = info.apply {
        //一般大部分情况下，匿名函数都会持有一个it，但是apply函数不会持有it，却会持有当前this
        println("info字符串的长度是：${this.length}")
    }.apply{
        println("info最后一个字符是：${this[this.length-1]}") //拿到最后一个字符
    }.apply{
        println("info全部转成小写是：${this.toLowerCase()}")
    }
   //由于apply一定会返回调用者本身，所以apply常用于链式调用
}
```

### Kotlin语言中let的使用

``` kotlin
fun main(){
    //普通方式,对集合中第一个元素相加
    val list=listof(6,5,2,3,5,7)
    val value1=list.first()
    val result1=value1+value1
    println(result1)
    
    //let方式 对集合第一个元素相加
    listof(6,5,2,3,5,7).let{
        it.first()+it.first()	//集合的最后一行作为返回值，let的特点，但是前面学的apply永远是返回info本身
    }
    
    //let方式+空合并操作符 对值判null，并返回
    fun getMethod3(value:String?):String{
        return value?.let{
            "欢迎回来${it}非常欢迎"
        }?:"你传递的内容是null"
    }
    
}
```

### Kotlin语言中run内置函数的使用

* run函数的特点 字符串延时
* 具名函数判断长度 isLong
* 具名函数检测合格 showText
* 具名函数增加一个括号 mapText
* 具名函数输出内容

``` kotlin
package three

fun main(){
    val str="Derry is Ok"
    val r1:Float=str.run {
        true
        324.3f
    }
    //run函数以最后返回的一行值类型为准
    println(r1)

    //下面是 具名函数 配合 run函数
    //2. 具名函数判断长度 isLong
    //这个是属于 匿名函数 配合 run
    str.run{
        //this==str本身
    }

    //这个是属于具名函数
    //str.run(具名函数)
    var run = str.run(::isLong)
    println(run)
}
fun isLong(str:String):String{
    return "str:$str"
}
```

### Kotlin语言的with内置函数

* with函数返回类型，是根据匿名函数最后一行的变化而变化
* with函数的 匿名函数里面持有的是this==str本身
* with和run基本上一样，只不过就是使用时候不同

``` kotlin
fun main (){
    val str="李元霸"
    val r1=with(str,::getStrlen)
    val r2=with(r1,::getLenInfo)
    println()
    
    //匿名操作
    with(with(str){
        length
    }){
        "[$this]"
    }
}
fun getStrLen(str:String) str.length
fun getLenInfo(len:Int)="你的字符串长度是:$len"
```

### Kotlin语言的also内置函数

* also函数返回类型，永远都是str本身
* also函数的匿名函数里面持有的是 it == str

``` kotlin

```

### Kotlin语言中的takeIf内置函数

``` kotlin
val name=takeIf{	true/false	}
//true:直接返回name本身
//false:直接返回null
```

### Kotlin语言中的takeUnless内置函数

``` kotlin
val name=takeUnless{	true/false	}
//true:直接返回null
//false:直接返回name本身

```

## 集合框架相关

### List创建与元素获取

``` kotlin
package gather

fun main(){
    val list= listOf("Derry","zhangsan","lisi")

    //普通取值方式
    println(list[0])
    println(list[1])
    println(list[2])

    //KT代码可以防止，空指针,下表越界异常
    //防止崩溃取值方式：getOrElse getOrNull
    println(list.getOrElse(3){"越界"})
    println(list.getOrElse(4){"越界"})
    //getOrNull+空合并操作符
    println(list.getOrNull(222)?:"越界了")
}
```

### 可变List集合

``` kotlin
package gather

fun main(){
    //可变的集合
    val list= mutableListOf("Derry","Zhangsan","wangwu")

    //可变的集合可以对数据进行增删操作
    list.add("lisi")
    list.remove("wangwu")

    //不可变集合
    val list1= listOf("Derry","Zhangsan","wangwu")
    //无法对数据进行增删操作

    //不可变集合转化为可变集合
    val list2:MutableList<String> = list1.toMutableList()
}
```

#### mutator函数

``` kotlin
package gather

fun main() {
    val list:MutableList<String> = mutableListOf("Derry","DerryAll","DerryStr")
    //1. mutator的特性 += -= 其实背后就是运算符重载
    list+="lisi"
    list+="wangwu"
    list-="Derry"
    println(list)
    //[DerryAll, DerryStr, lisi, wangwu]

    //2.removeIf
    //list.removeIf{true}   //如果是true 自动变量整个可变集合，进行元素一个一个的删除
    list.removeIf{
        it.contains("Derr")
    }
    println(list)
    //[lisi, wangwu]
}
```

### List集合遍历学习

``` kotlin
package gather

fun main() {
    val list= listOf(1,2,3,4,5,6,7)
    println(list)//输出list详情而已，这个不是遍历集合

    //第一种 遍历方式：
    for (i in list){
        println(i)
    }
    //第二种
    list.forEach{
        println(it)
    }
    //第三种
    list.forEachIndexed{
        index,item->
        println("下标：$index,元素:$item")
    }
}
```

#### 解构语法过滤元素学习

``` kotlin
package gather

//TODO 解构语法过滤元素学习

fun main(){
    val list :List<String> = listOf("A","B","C","D","E")

    val(value1,value2,value3,value4,value5)=list
    //value1=""

    var(v1,v2,v3,v4,v5)=list
    //使用_（下划线）可以跳过赋值
    var(_,_,_,_,v51)=list
}
```

### Set创建与元素获取

* Set 定义：不允许重复
* 普通方式elementAt 会越界异常
* elementAtOrElse elementAtOrNull

elementAtOrElse：提示越界

elementAtOrNull：异常返回空值

#### 可变的Set

``` kotlin
fun main(){
    val set:MutableSet<String> = mutableSetOf("a","b")
    set+="c"
    set.add("d")
    set.remove("a")
    println(set)
}
```

#### 集合转换与快捷函数

``` kotlin
package gather

fun main() {
    val list:MutableList<String> = mutableListOf("a","a","a","b","c")
    println(list)
    //list转Set去重
    val set = list.toSet()
    println(set)

    val list1=set.toList()
    println(list1)
    //distinct()    去重函数
    list.distinct()
}
```

### 数组类型/集合数组转换

``` kotlin
package gather

fun main() {
    val intArray= intArrayOf(1,2,3,4,5)
    println(intArray[4])

    println(intArray)
    //在数组中，elementAtOrElse{}中只能传递int数值
    println(intArray.elementAtOrElse(9){-1})
    println(intArray.elementAtOrNull(9))
    //OrNull + 空合并操作符
    println(intArray.elementAtOrNull(9)?:"yuejie")

    //List集合转数组
    var toCharArray = listOf('a', 'b', 'c').toCharArray()
}
```

### Map的创建

``` kotlin
fun main(){
    val mMap1:Map<String , Int > = mapOf("Derry" to (59),"ke" to 45)
    val mMap2:Map<String , Int > = mapOf(Pair("Derry",54),Pair("Ke",65))
}
```

#### 读取Map的值

1. [ ]找不到会返回null
2. getOrDefault
3. getOrElse

#### 遍历Map

``` kotlin
package gather

fun main() {
    val map1:Map<String,Int> = mapOf(Pair("Derry",54),Pair("Ke",65))
    map1.forEach{
        //it 内容 每一个元素（K和V）  每一个元素（K和V）
        //it 类型 Map.Entry<String,Int>
        println("K:${it.key} V:${it.value}")
    }
    println()
    //第二种方式
    map1.forEach {
        key:String,value:Int->  //默认的it给覆盖了
        println("key:$key,value:$value")
    }
    println()

    //第三种方式
    map1.forEach{
        (k,v)->
        println("key:$k,value:$v")
    }

    //第四种方式：
    for (item :Map.Entry<String,Int> in map1){
        println("key:${item.key},value:${item.value}")
    }
}
```

#### 可变Map集合

``` kotlin
fun main(){
    //MutableMap 可变集合
    val map:MutableMap<String,Int> = mutableMapOf(Pair("Derry",54),Pair("Ke",65))
    
    //getOrPut 没有的情况
    //如果整个map集合里面没有FFF的Key元素，我就帮你先添加到map集合中去，然后再从集合中获取
    val r:Int=map.getOrPut("FFF"){555}
    
    //getOrPut 有的情况,可以直接获取
     val r1:Int=map.getOrPut("FFF"){555}
}
```

#### field关键字

``` kotlin

```

#### 计算属性与防范竞态条件

``` kotlin
package gather
//TODO 计算属性 与 防范竟态条件

class KtBase71{
    var info:String?=""
    //防范竟态条件 当你调用成员，这个成员可能为NULL或空值的时候，就必须采用 防范竞态条件，这个是KT编程的规范化
    fun fetShowInfo():String{

        //这个成员，可能为null，可能为空值，就启用 防范竟态条件
        return info?.let {
            if(it.isBlank()){
                "nonono"
            }else{
                "it=$it"
            }
        } ?: "info is null"
    }
}
fun main() {
    val kt:KtBase71= KtBase71()

    println(kt.fetShowInfo())

}
```

## 构造函数

#### 主构造函数学习

``` kotlin
package gather

class KtBase72 (_name:String,_age:Int){
    var name:String=_name
        get() = field   //get不允许私有化
        private set(value){
            field=value
        }
    var age:Int=_age
        get() = field
        set(value){
            field=value
        }
}
fun main() {
    var kt:KtBase72= KtBase72("zhangsan",98)
    kt.age=83
    println(kt.age)
}
```

#### 构造函数内定义属性

``` kotlin
package gather

class KtBase72 (var _name:String,var _age:Int){
    var name:String=_name
        get() = field   //get不允许私有化
        private set(value){
            field=value
        }
    var age:Int=_age
        get() = field
        set(value){
            field=value
        }
}
fun main() {
    var kt:KtBase72= KtBase72("zhangsan",98)
    kt.age=83
    println(kt.age)
}
```

#### 次构造函数

constructor()为次构造函数，可重载

``` kotlin
package gather


class KtBase74 (var _name:String){
    constructor(_name:String,sex:Char):this(_name){
        print("name:$_name,sex:$sex")
    }
    constructor(_name:String,sex:Char,age:Int):this(_name){
        print("name:$_name,sex:$sex,age=$age")
    }
}

fun main() {
    var kt:KtBase72= KtBase72("zhangsan",98)
    kt.age=83
    println(kt.age)
}
```

#### 初始化代码块

``` kotlin
class KT{
    init{
        //初始化代码块
    }
}
```

#### 延迟初始化

``` kotlin
package gather

class Kt78{
    //lateinit 懒加载关键字
    lateinit var responseResultInfo:String

    //模拟服务器加载
    fun loadRequest(){
        responseResultInfo="yes"
    }
    fun showResponseResult(){
        if(::responseResultInfo.isInitialized){
            println("responseResultInfo:$responseResultInfo")
        }else{
            println("no")
        }
    }
}

fun main() {
    var kt:Kt78= Kt78()
    kt.loadRequest()
    kt.showResponseResult()
}
```

#### 惰性初始化

``` kotlin
package gather
class Kt79{
    //lateinit 懒加载关键字
    val responseResultInfo by lazy{
        loadRequest()
    }
    //模拟服务器加载
    fun loadRequest():String{
        return "yes"
    }
    fun showResponseResult(){
            println("responseResultInfo:$responseResultInfo")
    }
}
fun main() {
    var kt:Kt79= Kt79()
    kt.showResponseResult()
}
```

#### 继承与重载

与java 相反，所有方法和类默认是不能被重写/继承的。用open修饰符修饰可以打开继承与重载

#### 对象的声明

``` kotlin
//object修饰后，即是单例的实例也是类名
object Kt{
    //.....
}
fun main(){
    
}
```

##### 对象表达式

``` kotlin
package gather

open class Kt88{
    open fun add(info:String)= println("KtBase88 add:$info")
    open fun del(info:String)= println("KtBase88 del:$info")
}

fun main() {
    //对象类型的变量
    val kt88:Kt88=object:Kt88(){
        override fun add(info: String){
            println("add:$info")
        }
        override fun del(info: String){
            println("del:$info")
        }
    }
    kt88.add("???")
    //..........................
    
    //KT接口只有一种方式（object:对象表达式）
    
    /*
    object:RunnableKT{
        override fun run(){
            println("RunnableKT")
        }
    }.run()
    */
    
}
```

#### 嵌套类和内部类

* 嵌套外部类可以访问嵌套内部类，嵌套内部类不可以访问嵌套外部类
* 内部类可以访问外部类，外部类也可以访问内部类

#### 伴生对象

* 伴生对象的由来：在KT中是没有Java的这种static静态，伴生很大程度上和Java的这种static静态 差不多
* 无论  KtBase89() 构建对象多少次，我们的伴生对象，只有一次加载
* 无论被调用多少次，伴生对象只有一次加载
* 伴生对象只会初始化一次

#### 数据类学习(data class)

``` kotlin
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
```

