# apply-call
JS的apply和call方法
<pre>
1.apply示例: 
/*定义一个人类*/   
function Person(name,age) {   
    this.name=name; this.age=age;   
}   
 /*定义一个学生类*/   
functionStudent(name,age,grade) {   
    Person.apply(this,arguments); this.grade=grade;   
}   
//创建一个学生类   
var student=new Student("qian",21,"一年级"); 

分析: Person.apply(this,arguments); 
this:在创建对象在这个时候代表的是student  
arguments:是一个数组,也就是[“qian”,”21”,”一年级”]; 
也就是通俗一点讲就是:
用student去执行Person这个类里面的内容,在Person这个类里面存在this.name等之类的语句,这样就将属性创建到了student对象里面  

2.call示例  
在Studen函数里面可以将apply中修改成如下: 
Person.call(this,name,age);  

什么情况下用apply,什么情况下用call ？
在给对象参数的情况下,如果参数的形式是数组的时候,比如apply示例里面传递了参数arguments,这个参数是数组类型,并且在调用Person的时候参数的列表是对应一致的(也就是Person和Student的参数列表前两位是一致的) 就可以采用 apply ,
如果我的Person的参数列表是这样的(age,name),而Student的参数列表是(name,age,grade),这样就可以用call来实现了,
在使用call方法时参数必须逐个写出来如：Person.call(this,name,age,grade);

他们真正强大的地方是扩充函数赖以运作的作用域。
window.color='red';
var o={color:'blue'}
function sayColor(){
    alert(this.color);
}
sayColor();  //red
sayColor.call(this); //red
sayColor.call(window); //red
sayColor.call(o) //blue

要找到数组中最大或最小值，可以使用apply()
Math.min.apply(Math,['22',11,44])  //11
Math.max.apply(Math,['22',11,44])  //44
这个技巧是把Math作为第一个参数，从而正确地设置this的值
</pre>
