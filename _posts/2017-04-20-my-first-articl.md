---
layout: post_layout
title: Java并发
time: 2012年03月05日 星期五
location: 北京
pulished: true
excerpt_separator: "<!---more--->"
---
java实现并发通过多线程或者多进程来实现，首先我们来看怎么在java中实现多线程
java中实现线程的方式有两种方式，Thread或者Runnable。

### Thread还是Runnable？
<!---more--->

#### 1.Thread

 通过继承Thread，实现Run方法：
``` java
public class MyThread extends Thread{
	public void run(){
		System.out.println("This is my thread!")``;
	}
}
```
启动线程时使用myThread.start(); 
> * 注意不要使用myThread.run(). 
> * run和start的区别在于，start会启动子线程，而run只是在父线程中执行

#### 2.Runnable

Runnable是一个接口，通过实现Runnable，并且配合Thread使用：
``` java
public class MyRunnable implements Runnable{
	@Override
	public void run() {	
		System.out.println("This is my runnable!");	
	}
}

public static void main(String args[]){
	Thread test = new Thread(new MyRunnable());
	test.start();
}
```
#### 3.Thread or Runnable

使用Thread还是Runnable需要看具体的需求，Thread是一个类，Runnable是一个接口，当需要多继承的时候，你只能选择Runnable。由于Runnable的使用特性，它更利于资源的共享。

