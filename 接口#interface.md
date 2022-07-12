# 接口：

- interface
- public interface 接口名{ }
- 实现接口：class 类名 implements 接口名{ }


- 接口的特性：
    - 方法没有方法体 > 抽象方法
    - 定义静态方法、静态常量 > 由接口名直接调用的 
    - 定义默认的方法 > 直接被继承的 可以由对象直接调用

- 抽象方法：
    - public abstract 方法名(参数列表);
    - 接口中的抽象方法是默认的

- 抽象：
    - 类： 类相对于对象抽象
        - 类中的方法是具体的 逻辑具体
        - 类中的属性是抽象的
    - 抽象的行为可以用接口来定义

类： 以属性来区分类型
接口： 可以以行为/功能来区分类型

- 动物类： 吃
    - 老虎 狮子：吃

- 植物类： 没有吃
    - 食人花： 吃

## 类型：

- 基本数据类型 : 定义的变量 都是存储值的 可以使用 == 比较
    - 整数型 byte short int long
    - 浮点型 float double
    - 字符型 char
    - 布尔型 boolean
- 引用数据类型 ： 定义的变量(对象) 都是存储地址 >不能使用 == 比较
    - 类 接口 数组


## 样例：
- 接口的使用方式： 
  - 作为功能类的模板 
  - 定义一个类实现接口、重写接口中所有的抽象方法 

- 接口可以抽象行为，以行为分类
- 门： 开门 关门
    - 开关

```java

/**
 * 方法写成具体之后，不方便用来扩展 升级 
 */
public class Door{

    public void openDoor(){
      System.out.println ("开门");
    }

    public void closeDoor(){
      System.out.println ("关门");
    }

}


class DoorManage{
    public static void main(String[] args){
        Door door = new Door ();
        door.openDoor ();
        door.closeDoor ();
    }
}



```
## 加入接口
```java

package com.oop.zyf0712;
// 接口 
interface Openable{
    void open();

    // 用接口名 以及实现了这个接口的类名调用
   static final  int num=10;
   public static void test(){
       System.out.println ("静态方法 ");
   }

   // 可以被实现了接口的类的对象调用 继承给实现类
   public default  void testDefault(){


   }

}

interface Closeable{
    void close();
}

// 类 
public class Door{

    // 1：抽象类
    Lock lock;// 不能创建对象

    public void openDoor(){
        lock.open ();
    }
    public void closeDoor(){
        lock.close ();
    }
/*
  // 2：接口实现
  LockInterface lock;// 不能创建对象

  public void openDoor(){
    lock.open ();
  }
  public void closeDoor(){
    lock.close ();
  }
*/


}

// 1：抽象类 
abstract class Lock implements Openable, Closeable{

}


// 抽象类的实现类
class FaceIDLock extends Lock{
    @Override
    public void open(){
        System.out.println ("人脸识别开门！");
    }

    @Override
    public void close(){
        System.out.println ("人脸识别锁门！");
    }
}
// 抽象类的实现类
class PwdLock extends Lock{
    // 重写的方法 会被优先调用
    @Override
    public void open(){
        System.out.println ("密码验证 开门！");
    }

    @Override
    public void close(){
        System.out.println ("密码验证 锁门！");
    }
}

// 2：接口 
interface LockInterface{
  void open();
  void close();
}

public class KeyLock implements LockInterface{
    @Override
    public void open(){
        System.out.println ("钥匙开门！");
    }

    @Override
    public void close(){
        System.out.println ("钥匙锁门！");
    }
}

class DoorManage{
    public static void main(String[] args){
        Door door = new Door ();
//        door.lock=new FaceIDLock();
        door.lock = new PwdLock ();

        door.lock.testDefault ();
        Openable.test();

        door.openDoor ();
        door.closeDoor ();
    }
}


```

## 任务： 
- 写一篇文章来介绍接口： 
  - 基本数据类型 & 引用数据类型  
  - 接口的作用 以及 使用方式 
  






































