---
title: "Priority Queues"
date: 2017-10-24T21:25:07+08:00
draft: false
tags: 
   - JAVA
categories:
  - 技术
  - 归档
---

[TOC]

本篇文章主要介绍优先队列(Priority Queue)和嵌套类(nested class)的基本用法。
接下来的文章会介绍在实现例如Greedy Best First Search和AStar搜索算法中使用priority queue。

<!--more-->

### Priority Queue

- In priority queue:

- The order of the queue is controlled by implementing **Comparable**.

### Nested Class: Java嵌套类

- if you make an inner class **static**, this is commonly called **a nested class**.

- create an inner class, you don't need an outer-class object.

- you can not access a non-static outer-class object from an object of a nested class.

### Example 1 (without nested class)

- Here is an example to show how we can specify order using Priority Queue.

<!--more-->

```java

/**
 * an example of Priority Queue
 * Created by HuGuodong on 2017/10/25.
 */

public class ToDoList extends PriorityQueue<ToDoList.ToDoItem>{
     class ToDoItem implements Comparable<ToDoItem> {
            private char primary;
            private int secondary;
            private String item;
            public ToDoItem(char pri, int sec, String i) {
                this.primary = pri;
                this.secondary = sec;
                this.item = i;
            }

         /**
          * order by the first arg, then the second arg
          * @param o
          * @return
          */
         @Override
            public int compareTo(ToDoItem o) {
                if (primary > o.primary) {
                    return 1;
                }
                if (primary == o.primary) {
                    if (secondary > o.secondary) {

                        return 1;
                    } else if (secondary == o.secondary) {
                        return 0;
                    }
                }
                return -1;
            }
            public String toString() {
                return Character.toString(primary) + secondary + ": " + item;
            }
        }
        public void add(char pri, int sec, String item){
            super.add(new ToDoItem(pri, sec, item));
        }

    public static void main(String[] args){
        ToDoList toDoList = new ToDoList();
        toDoList.add('c', 16,"Fog");
        toDoList.add('c', 3,"Dog");
        toDoList.add('a', 2,"Aog");
        while(!toDoList.isEmpty()){
            // remove is the same as poll, except its throw Exception, when it's empty.
            System.out.println(toDoList.remove());
            //System.out.println(toDoList.poll());
        }
//            result:
//            a2: Aog
//            c3: Dog
//            c16: Fog
    }
}

```

### Example 2 (nested class)

- Here is an example of using static inner class to implement PriorityQueue.

```java
public class MyPriorityQueue extends PriorityQueue<MyPriorityQueue.Student>{

    public static void main(String[] args){
        MyPriorityQueue que = new MyPriorityQueue();
        que.add(new Student(100, "guodong_hu"));
        que.add(new Student(99, "xie"));
        que.add(new Student(1, "lin"));
        while (!que.isEmpty()){
            System.out.println(que.poll());
        }
    }

    static class Student implements Comparable<Student>{
        Integer no;
        String name;
        public Student(Integer no, String name){
            this.no = no;
            this.name = name;
        }

        @Override
        public int compareTo(Student stu) {
            int result;
            if(no > stu.no){
                result = 1;
            }else if(no == stu.no){
                result = 0;
            }else{
                result = -1;
            }
            return result;
        }

        @Override
        public String toString() {
            return "Student{" +
                    "no=" + no +
                    ", name='" + name + '\'' +
                    '}';
        }
    }
}
```
