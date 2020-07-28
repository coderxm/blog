### java中的内部类

#### 一、内部类及访问特点

1:内部类概述:把类定义在其他类的内部，这个类就被称为内部类。
	理解：内部类不需要被其他外部类调用，所以内部类定义在外部类里边，连成一块
2:内部类访问特点
	a:内部类可以直接访问外部类的成员，包括私有。
	b:外部类要访问内部类的成员，必须创建对象。

#### 二、分类

分类：
	成员位置:在成员位置定义的类，被称为成员内部类（不在方法里），又分为静态和非静态	
	局部位置:在局部位置定义的类，被称为局部内部类（在方法里）

```java
class A{
    class B { //成员内部类
    }

    public void Show(){
        class C{ //局部内部类
        }
    }
}
```

#### 三、成员内部类的修饰

成员内部类：

- 可以被static修饰(外部类不行)
- 被四种访问权限修饰(public private default protected)
- 被abstract修饰，不能被实例化


**私有成员内部类**：对于成员内部类得私有使用，**private**，只能被当前类的方法访问，所以可以在外部类创建一个方法，创建内部类对象然后使用内部类方法。

#### 四、静态和非静态成员内部类及使用

静态和非静态有什么区别呢？非静态的成员内部类，如果使用比较缸的方式创建对象的话，也是new 类名()，确实会有误解，当然我们平时实例化的时候就是这么干的，不过这里不允许。
![非静态](https://img-blog.csdnimg.cn/20200728200739425.JPG?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L0dvYnVsbGlu,size_16,color_FFFFFF,t_70#pic_center)


而静态成员内部类却依旧保持着原来的做法，像类访问成员一样，调用其构造器创建内部类对象，同样的如果采用非静态类的方法创建对象也不行，new ().new ()也会报错！所以各自只有唯一的方法来创建对象，以免混淆！

```java
public class LongTest {
	public static void main(String[] args) {
//静态static内部类测试		
		Outer.Inner1 oi1 = new  Outer.Inner1();
		oi1.say();
		
//普通内部类测试：访问内部类成员需要创建对象		
		Outer.Inner2 oi2 = new Outer().new Inner2();
		oi2.eat();	
		oi2.outereat();
	}
}	
//另一个外部类
 class Outer{
	 int num = 10;
	 public void eat() {
		System.out.println("Outer吃饭啊_内部类调用外部内方法测试");
	} 
	 
//静态static内部类	 
	 static class Inner1{
	 	public void say() {
			System.out.println("说话啊_静态static内部类测试");
		}
	}

//普通非静态成员内部类 
	 class Inner2{
		 	public void eat() {
				System.out.println("Inner3吃饭啊_普通内部类测试");
			}			 	
		 	public void outereat() {
				Outer.this.eat();
				//内部类获取外部类成员，采用 外部类名.this.外部类成员	
			}
	} 
}
```

非静态内部类获取外部类成员，采用 **外部类名.this.外部类成员**，外部类成员无论哪种修饰也能进行访问。但是静态的成员内部类就惨了点，它不能通过这种方法获取外部类成员。原因是Static在类加载时就已经存在了，但是对象是在创建时才在内存中生成，而this指代的是当前的对象。在静态类里使用this的话，那么this指向的是哪个对象呢？ 
![静态](https://img-blog.csdnimg.cn/20200728200849656.JPG?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L0dvYnVsbGlu,size_16,color_FFFFFF,t_70#pic_center)


 静态方法是存放在内存中的数据段里，this和super调用的是堆空间里的应用对象不能调用数据段区域里的数据，因此静态方法中不能用this和super关键字，否则会报错。那为什么要分静态和非静态呢？静态使用起来方便，符合原本的创建对象的逻辑：外部类.静态内部类；

![内存图](https://img-blog.csdnimg.cn/20200728200828755.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L0dvYnVsbGlu,size_16,color_FFFFFF,t_70#pic_center)


#### 五、局部内部类及使用

定义在类的**方法中的类**，局部内部类在访问他所在的方法中的局部变量时必须用finnal修饰，因为方法结束后就弹栈了，变量也弹出去了，但是类还在堆里，还要用到变量，所以加个finnal将变量放到方法区常量池里（**jdk1.8不需要加finnal了，默认添加finnal**）

**局部内部类**：（在外部类的方法里创建内部类的对象，外部类方法才能调用内部类方法）

```java
public class Test {
	public static void main(String[] args) {
		Outer out = new Outer();
		out.method();
	}
}		//另一个类
 class Outer{		
	 public void method() {	//外部类方法
		 int  num = 10;
		 class Inner{	//内部类
			 public void print() {
					System.out.println(num);
				}
		 }	 //在外部类的方法里创建内部类的对象，外部类方法才能调用内部类方法
		Inner i = new Inner();
		i.print();		  
	 }
}
```

**匿名内部类：**（特殊的局部内部类，也是局部内部类的一种，必须写在方法里，本质是一个继承了该类（一般是抽象类）或者实现了该接口的子类匿名对象）

```java
public class Test {
    public static void main(String[] args) {
        MyInterface1 myInterface1 = new  MyInterface1(){   
            @Override
            public void show() {
                System.out.println("你真秀！");
            }
        };		//注意这里的分号，new开始到这里是一个语句;
        myInterface1.show();
    }
}		//接口
interface MyInterface1{
    void show();
}
```

注意这里虽然有一个名字myInterface1，但它是接口对象名，不是类名。其中你可以改写成：

```java
 new  MyInterface1(){   
     @Override
     public void show() {
         System.out.println("你真秀！");
     }
  }.show();		//注意这里的分号，new开始到这里是一个语句;
```

就啥名字也没有了！可能会有警告，不过没关系，照样跑！但如果你还学过lamda表达式的话就更好了：

```java
((MyInterface1) () -> System.out.println("你真秀！")).show();
```

分号就不容易漏了，一句话解决！你真秀！
![独秀](https://img-blog.csdnimg.cn/20200728202620401.jpeg?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L0dvYnVsbGlu,size_16,color_FFFFFF,t_70#pic_center )

---
公众号：小码之光（文章全部首发）
[个人网站](https://index.maliaoblog.cn/)   流浪舟引导




