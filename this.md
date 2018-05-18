### 1访问权限
			private 	default 	protected 	public
同一个类	可以     	可以		可以		可以
同一个包				可以		可以		可以
子类 								可以		可以
全局											可以
   
### this关键字
this关键字在程序中的四个常见的用法
#### 1 通过this关键字可以明确地去访问一个类的成员变量，解决与局部变量名称冲突的问题。 具体代码：
 class Person{
    ing age;
    public Person( int age ){
     this.age=age;
   }
   public int getAge(){
     retrun this.age;
  }
}
上面的代码中构造方法的参数定义为age，他是一个局部变量，在类中还定义了一个成员变量，名称也是age。 在构造方法中使用age 则访问的是局部变量，但如果使用this.age则访问的成员变量。

#### 2 this关键字调用成员方法。具体代码如下：
 class Person{
   public void eat(){
      System.out.println("吃东西");
   }
  public void speak(){
     this.eat();
  }
 在上面的speak方法中，使用this关键字条用eat（）方法，此时的this关键字可以省略不写。

#### 3 this关键字调用构造方法：构造方法是在实例化对象时被java虚拟机自动调用的，在程序中不能像调用其他方法一样去调用构造方法，但是可以使用this（[参数1][参数2]...）的形式调用其他构造方法。 代码如下：
 class Person{
    public Person(){
       System.out.println("无参的构造方法被调用...");
   }
   public person(String name){
     this();
    System.out.println("有参的构造方法被调用了...")
  }
class Demo{
    public static void main(String [] args){
      Person p=new Person("张三");
     }
 }

结果：无参的构造方法被调用...
       有参的构造方法被调用了...
**在使用this调用类的构造方法是应注意：**
  1 只能在构造方法中使用this调用其他构造方法，不能再成员方法中使用this调用构造方法；
  2 在构造方法中，使用this调用构造方法的语句必须放在第一位，且只能出现一次。
  3不能再一个类的两个构造方法是使用this相互调用，否则编译报错。
 

#### 4this最重要的特定就是表示返回类的引用，哪个对象调用this所在的方法，那么this就是哪个对象。
public class Demo8 {

   public static void main(String[] args) {
       A aa = new A();
       System.out.println(aa);
       System.out.println(aa.f()); //aa.f(), 返回aa这个对象的引用(指针)
   }   
}
 
class A { 
   public A f() {
       return this;  //返回调用f()方法的对象的A类对象的引用
   }   

}

输出的结果：A@2c1e6b
            A@2c1e6b   
			
			
### 