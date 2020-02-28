---
title: Java两个线程之间共享数据
time: 2019-07-01 00:00:00
tags:
- Java
- Thread
---
-------------
Java里面进行多线程通信的主要方式就是共享内存的方式，共享内存主要的关注点有两个：**可见性**和**有序性原子性**。

Java 内存模型（JMM）解决了可见性和有序性的问题，而锁解决了原子性的问题，理想情况下我们希望做到“同步”和“互斥”。

<!-- more -->
有以下常规实现方法：

 一、数据抽象成一个类，对数据操作的方法封装在类里

```java
public class MyData1 {
    private int j = 0;

    public static void main(String[] args) {
        MyData1 data = new MyData1();
        AddRunnable addRunnable = new AddRunnable(data);
        DecRunnable decRunnable = new DecRunnable(data);

        new Thread(addRunnable).start();
        new Thread(decRunnable).start();

    }

    public synchronized void add() {
        j++;
        System.out.println("线程：" + Thread.currentThread().getName() + " j为：" + j);
    }

    public synchronized void dec() {
        j--;
        System.out.println("线程：" + Thread.currentThread().getName() + " j为：" + j);
    }

    public int getData() {
        return j;
    }
}

class AddRunnable implements Runnable {

    MyData1 data1 = new MyData1();

    public AddRunnable(MyData1 data1) {
        this.data1 = data1;
    }

    @Override
    public void run() {
        data1.add();
    }
}

class DecRunnable implements Runnable {

    MyData1 data1 = new MyData1();

    public DecRunnable(MyData1 data1) {
        this.data1 = data1;
    }

    @Override
    public void run() {
        data1.dec();
    }
}
```

二、Runnable对象作为一个类的内部类，共享数据作为这个类的内部变量，每个线程对类的操作封装在外部类中，从而实现各个数据之间的互斥和同步，内部类的各个Runnable对象都可以调用外部方法
```java
public class MyData2 {
    private int j = 0;

    public synchronized void add() {
        j++;
        System.out.println("线程：" + Thread.currentThread().getName() + " j为：" + j);
    }

    public synchronized void dec() {
        j--;
        System.out.println("线程：" + Thread.currentThread().getName() + " j为：" + j);
    }

    public int getData() {
        return j;
    }
}

class TestThread {
    public static void main(String[] args) {
        final MyData2 data = new MyData2();
        for (int i = 0; i < 2; i++) {
            new Thread(new Runnable() {
                @Override
                public void run() {
                    data.add();
                }
            }).start();

            new Thread(new Runnable() {
                @Override
                public void run() {
                    data.dec();
                }
            }).start();
        }
    }
}
```