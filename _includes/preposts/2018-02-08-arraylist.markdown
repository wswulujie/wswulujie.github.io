---
layout:     post
title:      "jdk8中的集合框架(二)--arrayList"
subtitle:   " \"jdk8中集合框架汇总\""
date:       2018-02-08 14:05:00
author:     "FengZzz"
header-img: "img/post-bg-2015.jpg"
catalog: true
tags:
    - java
---


##正文
arrayList是jdk对于数组元素的补充，但是它通过封装数组拷贝的操作，解决了数组长度不可变，必须由使用者自己解决的缺点，也就是可变长度，具体如下。
```html
public class ArrayList<E> extends AbstractList<E> implements List<E>, RandomAccess, Cloneable, java.io.Serializable {



```    


一些比较基础常用的集合类
```html
                                     ArrayList 
                             List      
                                     LinkedList                        

Iterable     Collection        
                                     HashSet
                             Set
                                     TreeSet
```                                         
Iterable接口：
Collection接口继承的父接口，主要方法为Iterator()方法，返回值类型为Iterator接口，由每个Collection实现类内部自己定义的内部类，实现Iterator接口，确保不同实现类，不同数据结构由自定义的迭代器遍历集合(多态的使用)。
```html

public interface Iterable<T> {

    Iterator<T> iterator();

}
```

Iterator接口：
该接口是所有具体的集合类中内部迭代器类的的父接口，在每个不同的集合类内部，通过的实现不同数据结构，由专属的内部类迭代器完成对于数据的访问，在该接口内，定义了通用的方法。

```html

public interface Iterator<E> {

    //检查是否还有下一个元素
    boolean hasNext();

    //输出下一个元素
    E next();

    //jdk8之后，可以在接口之中有具体的方法定义。
    default void remove() {
        throw new UnsupportedOperationException("remove");
    }

}
```
Collection接口：
该接口是奠定了集合容器的基础，内部包含针对容器对于元素的基本操作。该接口没有直接的实现对象，由该接口派生出两个分支 **Set**和**List**，**List**的实现类确保内部元素可重复，保存顺序与存入顺序一致，而**Set**的实现类确保内部元素不可重复，存储顺序与存入顺序没有关系。
```html

public interface Collection<E> extends Iterable<E> {

        int size();
        boolean add(E e);
        boolean remove(Object o);
}

```

List(有序，可重复)
List里存放的对象是有序的，同时也是可以重复的，List关注的是索引，拥有一系列和索引相关的方法，查询速度快。因为往list集合里插入或删除数据时，会伴随着后面数据的移动，所有插入删除数据速度慢。


Set(无序，不可重复)
Set里存放的对象是无序，不能重复的，集合中的对象不按特定的方式排序，只是简单地把对象加入集合中。

