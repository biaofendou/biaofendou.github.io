---
title: SpringBoot_database
date: 2019-10-09 10:52:56
tags: 
- Spring Boot
- 数据库
categories:
- 框架
description: <center><h3>Spring Boot中数据库的比较</h3></center>
photo: https://biaofendou.github.io/images/photos/18091.jpg
---

# Spring Boot中几种数据库的比较

## 一、MySQL

对于传统关系型数据库来说，Spring Boot使用JPA（Java Persistence API）资源库来实现对数据库的操作，MySQL就是典型的关系型数据库。JPA就是为POJO（Plain Ordinary Java Object）提供持久化的标准规范，即将Java的普通对象通过对象关系映射（Object-Relational Mapping，ORM）持久化到数据库中。

>  JDBC
>
> > Java应用通过JDBC接口访问数据库，JDBC（Java DataBase Connectivity/Java数据库连接）为各种数据库，如mysql、oracle等，提供一个统一的接口，应用程序通过JDBC执行各种SQL操作，如select、insert等等。在本文中，我们会通过JDBC访问数据库，验证数据库是否正常连接。

> JPA
>
> > JPA（Java Persistence API/Java持久层接口），是ORM（Object Relational Mapping/对象关系映射）的一个标准，ORM的作用是在数据库表与Java对象之间建立映射，理论上来说有ORM就无需直接通过SQL操作数据库了，通过Java对象即可，这样会方便很多，Hibernate是实现JPA标准的一个有名例子。JPA建立在JDBC之上，也是通过JDBC访问数据库。

> Mybatis
>
> > ORM有一些缺点，如过于笨重，比如在多表联合查询时相当繁琐，但直接使用原始的JDBC操作数据库过于低效，mybatis是现在互联网项目使用比较多的一个Java持久层库。虽然mybatis经常被和Hibernate比较，但mybatis不是JPA的一个实现，mybatis可以理解为加强版的SQL，实现了诸如动态SQL、结果集映射等，高效又不失灵活，个人倾向使用mybatis。同样的，mybatis建立在JDBC之上，通过JDBC访问数据库。后面的教程将对mybatis做详细介绍。

### 1. MySQL依赖配置

```xml
<dependencies>
        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-web</artifactId>
        </dependency>
        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-data-jpa</artifactId>
        </dependency>
        <dependency>
            <groupId>mysql</groupId>
            <artifactId>mysql-connector-java</artifactId>
            <scope>runtime</scope>
        </dependency>
        
        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-test</artifactId>
            <scope>test</scope>
        </dependency>
</dependencies>
```

### 2.创建实体

首先创建一些普通对象，用来与数据库的标建立映射关系，接着延时如何使用JPA对数据库进行增删改查。

```java
@Entity
@Table(name = "department")
public class Department {
    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long id;
    private String name;
    public Department(){}

}

```

### 3.实体持久化

通过上面实体的定义，实现了使用Java的普通对象（POJO）与数据库表建立映射关系（ORM），接下来使用JPA来实现持久化。

```java
public interface UserJPA extends JpaRepository<UserEntity,Long>, JpaSpecificationExecutor<UserEntity>, Serializable {

}
```

## 二、Redis

关系型数据库在性能上存在一些缺陷，所以大家在使用关系型数据库时，会与具有高效存储功能的缓存系统结合使用，以提高系统的并发性。Redis是一种可以持久存储的缓存系统，是一个高性能的key-value数据库，它使用键-值对的方式存储数据。

### 1. Redis依赖配置

###  2. 创建Redis服务类

