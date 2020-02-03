---
title: "Decorator"
date: 2020-01-04T10:11:03+08:00
draft: false
tags: 
   - DesignPattern
categories:
  - 技术
  - 归档
---

[TOC]

 Brief introduction about Decorator.

<!--more-->

# 装饰模式（Decorator）

动态地给一个对象添加一些额外的职责，就增加功能来说，装饰模式比生成子类更为灵活。

## 场景

假设有个4S店，卖车。卖的🚗有宝马BMW和特斯拉的ModelX。
车分基本款和在此基础上的定制款。客户可以定制自己的爱车🚗，例如定制真皮座椅💺，和定制音响设备。

赵四买了个ModelX，改装了音响系统。

刘能看赵四买了ModelX，他想我也得整一个呀！
他买了的BMW，要装真皮座椅，和更牛的音响系统，让全村人都知道他刘能🐂🍺。

以上就是装饰模式的意思。

## 装饰模式

![decorator](https://gitee.com/gdhu/testtingop/raw/master/2019-11-20-001.jpg)

## 代码

[code example](./code/u006)

Client

```java
public class Client {

  public static void main(String[] args) {
    ICar bmw = new BMW();
    bmw.makeOrder();
//    A new order has been made.Car: u006.BMW

    // decorate
    ICar bmw_leather = new LeatherSeats(bmw);
    ICar bmw_addAudio = new AudioDecorator(bmw_leather);
    bmw_addAudio.makeOrder();
//    A new order has been made.Car: u006.BMW
//    Leather seats have been added.
//    Audio devices are awesome.

    ICar modelX = new ModelX();
    modelX.makeOrder();
//    A new order has been made. Car: u006.ModelX

    // decorate
    ICar modelX_audio = new AudioDecorator(modelX);
    modelX_audio.makeOrder();
//    A new order has been made. Car: u006.ModelX
//    Audio devices are awesome.

  }
}
```



```java
package u006;

/**
 * Created by HuGuodong on 11/20/19.
 */
public interface ICar {

  void makeOrder();
}

class ModelX implements ICar {

  @Override
  public void makeOrder() {
    System.out.println("A new order has been made. Car: " + this.getClass().getName());
  }
}

class BMW implements ICar {

  @Override
  public void makeOrder() {
    System.out.println("A new order has been made.Car: " + this.getClass().getName());
  }
}

abstract class CarDecorator implements ICar{

  protected ICar car;

  public CarDecorator(ICar car) {
    this.car = car;
  }

  public abstract void makeOrder();

}

class AudioDecorator extends CarDecorator {

  public AudioDecorator(ICar car) {
    super(car);
  }

  @Override
  public void makeOrder() {
    car.makeOrder();
    showAudioDevices();
  }

  public void showAudioDevices(){
    System.out.println("Audio devices are awesome.");
  }

}

class LeatherSeats extends CarDecorator {

  public LeatherSeats(ICar car) {
    super(car);
  }

  @Override
  public void makeOrder() {
    car.makeOrder();
    addLeatherSeats();
  }

  private void addLeatherSeats(){
    System.out.println("Leather seats have been added.");
  }
}
```

2019-11-19