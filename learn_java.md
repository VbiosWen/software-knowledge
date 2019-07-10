- ### 1. 线程间通信方式

```java
  package com.vbiso.thread;

import com.google.common.collect.Lists;
import java.util.List;
import java.util.concurrent.TimeUnit;

/\*\*

- @Author: wenliujie
- @Description: 线程间通信方式
- @Date: Created in 20:57 2019-07-10
- @Modified By:
  \*/
  public class ThreadSignaling {

/\*\*

- 第一种,通过 synchronized 进行通信,同一个对象只能有一个方法持有对象锁,所以同时只有一个方法能执行
  \*/

public synchronized void methodA() {
System.out.println("method A");
}

public synchronized void methodB() {
System.out.println("method B");
}

private static class ThreadA extends Thread {

    private final ThreadSignaling myLock;

    public ThreadA(ThreadSignaling myLock) {
      this.myLock = myLock;
    }

    @Override
    public void run() {
      super.run();
      myLock.methodA();
    }

}

private static class ThreadB extends Thread {

    private final ThreadSignaling myLock;

    public ThreadB(ThreadSignaling myLock) {
      this.myLock = myLock;
    }

    public void run() {
      super.run();
      myLock.methodB();
    }

}

/\*\*

- 第二种方式通过 while 轮询,但是要保证轮询字段被 volatile 修饰
  \*/

private volatile List<String> list = Lists.newArrayList();

public void add() {
list.add("elements");
}

public int size() {
return list.size();
}

private static class ThreadC extends Thread {

    private final ThreadSignaling threadSignaling;

    public ThreadC(ThreadSignaling threadSignaling) {
      super();
      this.threadSignaling = threadSignaling;
    }

    @Override
    public void run() {
      try {
        for (int i = 0; i < 100; i++) {
          threadSignaling.add();
          System.out.println("add " + i + " element");
          TimeUnit.SECONDS.sleep(1);
        }
      } catch (InterruptedException e) {
        e.printStackTrace();
      }
    }

}

private static class ThreadD extends Thread {

    private final ThreadSignaling threadSignaling;

    public ThreadD(ThreadSignaling threadSignaling) {
      super();
      this.threadSignaling = threadSignaling;
    }

    @Override
    public void run() {
      try {
        while (true) {
          if (threadSignaling.size() >= 5) {
            System.out.println("== 5 线程 B准备退出了");
            throw new InterruptedException();
          }
        }
      } catch (InterruptedException e) {
        e.printStackTrace();
      }
    }

}

/\*\*

- 线程间通信方式 3 wait 和 notify
  \*/

private static class ThreadE extends Thread {

    private final ThreadSignaling lock;

    public ThreadE(ThreadSignaling lock) {
      this.lock = lock;
    }

    @Override
    public void run() {
      try {
        synchronized (lock) {
          for (int i = 0; i < 100; i++) {
            if (i == 5) {
              lock.notify();
              System.out.println("已经发出通知了");
            }
           lock.add();
            System.out.println("thread add " + i);
            TimeUnit.SECONDS.sleep(1);
          }
        }
      } catch (InterruptedException e) {
        e.printStackTrace();
      }
    }

}

private static class ThreadF extends Thread {
private final ThreadSignaling lock;

    public ThreadF(ThreadSignaling lock) {
      this.lock = lock;
    }

    @Override
    public void run() {
      try {
        synchronized (lock){
          while (true){
            if(lock.size() == 5){
              System.out.println("满足情况,线程退出");
                throw new InterruptedException();
            }
            try {
              lock.wait();
            } catch (InterruptedException e) {
              e.printStackTrace();
            }
          }
        }
      } catch (InterruptedException e) {
        e.printStackTrace();
      }
    }

}

public static void main(String[] args) throws InterruptedException {
ThreadSignaling myLock = new ThreadSignaling();
ThreadA threadA = new ThreadA(myLock);
ThreadB threadB = new ThreadB(myLock);

 // threadA.start();
//threadB.start();

    //  threadB.start();
    // threadA.start();

// ThreadC threadC = new ThreadC(myLock);
//
// ThreadD threadD = new ThreadD(myLock);
//
// threadC.start();
// threadD.start();

    ThreadE threadE = new ThreadE(myLock);
    ThreadF threadF = new ThreadF(myLock);
    threadE.start();
    threadF.start();

}

}
```
