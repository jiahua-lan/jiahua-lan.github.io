---
title: Spring Data JPA 使用技巧
date: 2020-10-07 06:00:54
categories:
  - [JPA, Spring Data JPA]
  - Spring Data
tags:
  - JPA
  - Spring Data JPA
---

* Spring Data JPA

> 对于从大学就开始学习并使用`Hibernate`的本猫而言，`Spring Data JPA`是一个无论如何都无法绕过的框架。虽然`JPA`这种东西和轻量简单扯不上什么关系，但是本猫还是觉得这是一个十分好用的框架。在此记录一下本猫关于使用`Spring Data JPA`的一些心的和技巧。

* 关于本文中的所有描述，都是基于`Hibernate`实现。

1. 美好的一天，从建表开始。

在本猫看来，`JPA`这套标准和它的实现们最让人割舍不下的就是它的自动建表。虽然这已经不是独一份的功能了，但是相较之与其他的框架，`JPA`的建表突出一个全面，无论是外键、索引、约束，抑或数据类型、精度还是表名、列名的映射都可以轻松搞定。

```java

@Entity
//通过name来设置表名
@Table(name = "people") 
public class Person {
    //申明表的主键
    @Id
    //申明主键的生成方式，在不进行额外设置的情况下使用序列自增。
    //如果底层数据库不支持序列，则通过创建一张序列表来模拟序列。
    @GeneratedValue
    private Long id;

    //通过name设置列名，通过unique设置唯一约束，通过nullable设置非空约束
    @Column(name="full_name", unique = true, nullable = false)
    private String fullName;
}

```

2. 