---
layout: post
title: JDBC基础六步
date: 2021-03-19 16:36:00
author: 牧之
tags: 
  - JDBC
subtitle:   ""
header-style: text
---


数据准备：

```sql
create database wkcto;

use wkcto;

create table tbl_student(
	id varchar(255),
  name varchar(255),
  birth char(10)
)

insert into tbl_student(id, name, birth) values('1', 'zhangsan', '1980-12-11');
insert into tbl_student(id, name, birth) values('2', 'lisi', '1999-01-20');
insert into tbl_student(id, name, birth) values('3', 'wangwu', '1920-09-29');
commit;
select * from tbl_student;
```

jdbc代码：

```java
import java.sql.*;
import java.util.ArrayList;
import java.util.List;

public class JDBCTets01 {
  public static void main(String[] args) {

    Connection conn = null;
    PreparedStatement ps = null;
    ResultSet rs = null;
    List<Student> studentList = new ArrayList<>();// 钻石表达式
    try {
      // 1、注册驱动
      Class.forName("com.mysql.jdbc.Driver");

      // 2、获取连接
      String url = "jdbc:mysql://localhost:3306/wkcto";
      String user = "root";
      String password = "root";
      conn = DriverManager.getConnection(url, user, password);
      String sql = "select id,name,birth from tbl_student";

      // 3、获取预编译的数据库操作对象
      ps = conn.prepareStatement(sql);

      // 4、执行SQL语句
      rs = ps.executeQuery();

      // 5、处理查询结果集
      while (rs.next()) {
        String id = rs.getString("id");
        String name = rs.getString("name");
        String birth = rs.getString("birth");

        // 将以上零散数据封装到JavaBean
        Student student = new Student();
        student.setId(id);
        student.setName(name);
        student.setBirth(birth);
        // 把JavaBean放到容器中
        studentList.add(student);
      }
    } catch (Exception e) {
      e.printStackTrace();
    } finally {

      // 释放资源
      if (rs != null) {
        try {
          rs.close();
        } catch (SQLException e) {
          e.printStackTrace();
        }
      }
      if (ps != null) {
        try {
          ps.close();
        } catch (SQLException e) {
          e.printStackTrace();
        }
      }
      if (conn != null) {
        try {
          conn.close();
        } catch (SQLException e) {
          e.printStackTrace();
        }
      }
    }

    // 使用list集合展示（view）
    for (Student s : studentList) {
      System.out.println(s);
    }
  }
}

```

实体类：

```java
public class Student {
  private String id;
  private String name;
  private String birth;

  @Override
  public String toString() {
    return "Student{" +
        "id='" + id + '\'' +
        ", name='" + name + '\'' +
        ", birth='" + birth + '\'' +
        '}';
  }

  public String getId() {
    return id;
  }

  public void setId(String id) {
    this.id = id;
  }

  public String getName() {
    return name;
  }

  public void setName(String name) {
    this.name = name;
  }

  public String getBirth() {
    return birth;
  }

  public void setBirth(String birth) {
    this.birth = birth;
  }
}

```
执行结果：
```
Student{id='1', name='zhangsan', birth='1980-12-11'}
Student{id='2', name='lisi', birth='1999-01-20'}
Student{id='3', name='wangwu', birth='1920-09-29'}
```