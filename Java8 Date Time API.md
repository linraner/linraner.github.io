---
title: Java8 Date AND Time API
date: 2018-10-05 18:16:21
tags: 
- java
- note
---

## Java8 引入了新的时间类
### 使用 ``LocalDate`` 和 ``LocalTime``
创建 ``LocalDate`` 对象并读取值
```java
//2013-03-06
LocalDate date = LocalDate.of(2012,03,06);
//2012
int year = date.getYear();
//MARCH
Month month = date.getMonth();
//TUESDAY
DayOfWeek dow = date.getDayOfWeek();
//6
int day = date.getDayOfMonth();
//31
int len = date.lengthOfMonth();
//false
boolean leap = date.isLeapYear();
//使用工厂方法获取系统日期
LocalDate today = LocalDate.now();
LocalTime time = LocalTime.now().withNano(0);//去除毫秒
```
``TemporalField`` 是一个接口, 定义了如何访问 ``temporal`` 对象某个字段的值. ``ChronoField`` 枚举实现这一接口.

```java
int year = date.get(ChronoField.YEAR);
int month = date.get(ChronoField.MONTH_OF_YEAR);
int day = date.get(ChronoField.DAY_OF_MONTH);
```

``LocalDate`` 和 ``LocalTime`` 都可以解析字符串创建.

```java
LocalDate date = LocalDate.parse("2012-12-22");
LocalTime time = LocalTime.parse("22:22:22");
```

### 操作、解析和格式化

#### 使用 ``TemporalAdjuster``


