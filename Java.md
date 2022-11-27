[toc]

# Concept

# 基本语法

## 嵌套类 Nested Class

在语法上，定义在另一个类中的类被成为嵌套类

[Nested Classes (The Java™ Tutorials > Learning the Java Language > Classes and Objects) (oracle.com)](https://docs.oracle.com/javase/tutorial/java/javaOO/nested.html)

> Nested classes are divided into two categories: non-static and static. Non-static nested classes are called *inner classes*. Nested classes that are declared `static` are called *static nested classes*.

### 非静态嵌套类 inner classes

不能单独存在，隐式地持有外部类的引用

```Java
OuterClass outerObject = new OuterClass();
OuterClass.InnerClass innerObject = outerObject.new InnerClass();
```

#### 	局部内部类 local classes 

#### 	匿名类 anonymous classes

匿名类定义是一个**表达式**

局部内部类和匿名内部类只能访问局部 **final** 变量

> In addition, a local class has access to local variables. However, a local class can only access local variables that are declared final. When a local class accesses a local variable or parameter of the enclosing block, it *captures* that variable or parameter. For example, the `PhoneNumber` constructor can access the local variable `numberLength` because it is declared final; `numberLength` is a *captured variable*.

局部变量会在局部内部类的外部方法执行结束后销毁，但此时局部内部类仍可能访问该局部变量，所以事实上，局部内部类使用的是局部变量的副本，修改副本是无意义的，所以局部内部类可以访问的局部变量应该是 final 类型的

```java
public class Test {
    public static void main(String[] args)  {
         
    }
    // 去掉 final 无法正常编译
    // 在 Java 1.8 之后，编译器会自动加上 final 关键字，所以即使去掉 final 还是可以通过编译，但还是无法在局部内部类中
    // 事实上，内部类使用的是局部变量的副本，所以修改该局部变量是无意义的
    public void test(final int b) {
        final int a = 10;
        new Thread(){
            public void run() {
                System.out.println(a);
                System.out.println(b);
            };
        }.start();
    }
}
```

### 静态内部类 static nested classes

### Lambda Expression

[Lambda Expressions (The Java™ Tutorials > Learning the Java Language > Classes and Objects) (oracle.com)](https://docs.oracle.com/javase/tutorial/java/javaOO/lambdaexpressions.html)

>  lambda expression does not introduce a new level of scoping.

### Functional Interfaces

[Lambda Expressions (The Java™ Tutorials > Learning the Java Language > Classes and Objects) (oracle.com)](https://docs.oracle.com/javase/tutorial/java/javaOO/lambdaexpressions.html)

> A functional interface is any interface that contains only one abstract method. (A functional interface may contain one or more default methods or static methods.) 

JDK 提供了标准函数接口 `java.util.function`

>  lambda expression does not introduce a new level of scoping.

### Method References

[Method References (The Java™ Tutorials > Learning the Java Language > Classes and Objects) (oracle.com)](https://docs.oracle.com/javase/tutorial/java/javaOO/methodreferences.html)

```java
public class InnerClass {
    class Greet implements Runnable {

        @Override
        public void run() {
            sayHello();
        }
    }

    private void sayHello() {
        System.out.println("HelloWorld");
    }

    public void main() {
        // inner class
        new Thread(new Greet()).start();

        // anonymous claas
        new Thread(new Runnable() {
            @Override
            public void run() {
                sayHello();
            }
        }).start();

        // lambda expression
        new Thread(() -> sayHello()).start();

        // Method References
        new Thread(this::sayHello).start();
    }
}
```

## Annotation

```java
// predefined annotaion
@Override @Deprecated @SuppressWarnings @SafeVarargs @FunctionalInterface

// define annotaion
@interface ClassPreamble {
   String author();
   String date();
   int currentRevision() default 1;
   String lastModified() default "N/A";
   String lastModifiedBy() default "N/A";
   // Note use of array
   String[] reviewers();
}
```

> Annotations that apply to other annotations are called *meta-annotations*. 

```java
@Retention // RetentionPolicy.SOURCE RetentionPolicy.CLASS RetentionPolicy.RUNTIME
@Documented
@Target
@Inherited @Repeatable
```

# 反射

# Stream 流

# 集合框架

# 并发编程

线程之间的共享变量要使用 `volatile` 关键字

１）**保证可见性**
２）**不保证原子性**
３）**禁止指令重排**

`Thread.stop` 方法已经废除

**守护线程**

在 JVM 中，所有**非守护线程**都执行完毕后，无论有没有守护线程，虚拟机都会自动退出

守护线程不能持有任何需要关闭的资源，虚拟机退出时，守护线程没有任何机会来关闭文件

`setDaemon(true)`把该线程标记为守护线程

`synchronized` 框中的代码为 **临界区**

### Java 锁

可重入锁

[synchronized锁定的到底是什么？ - 知乎 (zhihu.com)](https://www.zhihu.com/question/57794716?sort=created)

[synchronized详解 -l 三分恶 - 博客园 (cnblogs.com)](https://www.cnblogs.com/three-fighter/p/14396208.html)

[不可不说的Java“锁”事 - 美团技术团队 (meituan.com)](https://tech.meituan.com/2018/11/15/java-lock.html)

### Java 内存模型 JMM

[Java内存模型（JMM）总结 - 知乎 (zhihu.com)](https://zhuanlan.zhihu.com/p/29881777)

[关于Java变量的可见性问题_远离颠倒梦想的技术博客_51CTO博客](https://blog.51cto.com/u_2870645/2848480)

sleep 也可以使得一个线程对变量的修改对另一个线程可见

# 参考资料

[Trail: Learning the Java Language (The Java™ Tutorials) (oracle.com)](https://docs.oracle.com/javase/tutorial/java/index.html)

[Learn Java - Dev.java](https://dev.java/learn/)

[Home: Java Platform, Standard Edition (Java SE) 8 Release 8 (oracle.com)](https://docs.oracle.com/javase/8/)

[Java Documentation - Get Started (oracle.com)](https://docs.oracle.com/en/java/)