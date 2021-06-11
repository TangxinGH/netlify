---
title: javaweb连mysql
date: 2019-10-17 11:27:29.000
updated: 2019-10-17 11:35:25.000
csdn_url: https://blog.csdn.net/weixin_43531940/article/details/102602578
description: 一共三个类：
userVo:// 定义一个 Bean，与数据库表中的各个字段对应：
connection://定义一个数据库连接类，用于获取 MySQL 的连接
option:操作数据库
uservo:定义你自己表相关字段
   // 定义一个 Bean，与数据库表中的各个字段对应：

   import java.util.Date;
    public class UserVo {
 pri...
tags: 
categories: javaweb
article_id: 102602578
---
﻿##### 一共三个类：
userVo:// 定义一个 Bean，与数据库表中的各个字段对应：
connection://定义一个数据库连接类，用于获取 MySQL 的连接
option:操作数据库
uservo:定义你自己表相关字段

```java
   // 定义一个 Bean，与数据库表中的各个字段对应：

   import java.util.Date;
    public class UserVo {
 private int id;
 private String userName;
 private int age;
 private int sex;
 private Date createDt;
        public int getId() {
         return id;
         }

        public void setId(int id) {
   this.id = id; }
         public String getUserName() {
        return userName;
       }

 public void setUserName(String userName) {
 this.userName = userName;
 }

   public int getAge() {
        return age;
  }

  public void setAge(int age) {
            this.age = age;
         }

         public int getSex() {
         return sex;
        }

   public void setSex(int sex) {
         this.sex = sex;
      }

     public Date getCreateDt() {
        return createDt;
        }

     public void setCreateDt(Date createDt) { this.createDt = createDt;
       }

       @Override
 public String toString() {
       return "UserVO [id=" + id + ", userName=" + userName + ", age=" + age
       + ", sex=" + sex + ", createDt=" + createDt + "]";
       }

    }
```


##### connectioin:定义数据库相关信息

```java
//定义一个数据库连接类，用于获取 MySQL 的连接



    import java.sql.Connection;
import java.sql.DriverManager;

     public class connection {
//user是数据库;
    private static final String URI = "jdbc:mysql://localhost:3306/user?useSSL=false&serverTimezone=UTC";
// + "user=tangxin&password=123456&useUnicode=true&characterEncoding=UTF-8";

//        private static final String DRIVER = "com.mysql.jdbc.Driver";//// MySQL 8.0 以下版本 - JDBC 驱动名及数据库 URL
// MySQL 8.0 以上版本 - JDBC 驱动名及数据库 URL
 private static final String DRIVER = "com.mysql.cj.jdbc.Driver";
         static final String USER = "tangxin";
         static final String PASS = "123456";
        public static Connection connectDB() throws Exception {
         //1、加载数据库驱动
        Class.forName(DRIVER);
        //2、获取数据库连接
         Connection conn = DriverManager.getConnection(URI,USER,PASS);

         return conn;
        }

   }
```


#### option类：增删查更
每一个方法后面都有一个main来测试当前方法，测试用。如mian1改为main就可以运行。

```java
import java.sql.*;
import java.util.ArrayList;
import java.util.HashMap;
import java.util.List;
import java.util.Map;


public class option {
//    查询所有的数据，在option中定义一个queryAll()方法：
//    这里使用Connection.createStatement()方法获取一个Statement对象，这个对象里面有很多的方法可以操作数据库，
// 使用excuteQuery(String sql)执行查询操作，查询结果为一个结果集ResultSet，可以通过这个结果集获取相关的信息。

    public List<UserVo> queryAll() throws Exception {
        Connection conn = connection.connectDB();
        String sql = "SELECT * FROM tbl_user_info";
        List<UserVo> userList = new ArrayList<UserVo>();

        Statement stmt = conn.createStatement();
        ResultSet rs = stmt.executeQuery(sql);
        iteration(userList, rs);

        return userList;
    }
////    检查信息:发现重复的代码
////    方法，必须针对当前运行时对象调用。? ，合并为了方法iteration!!,就是个循环；
    private void iteration(List<UserVo> userList, ResultSet rs) throws SQLException {
        while(rs.next()) {
            UserVo user = new UserVo();
            user.setId(rs.getInt("id"));
            user.setUserName(rs.getString("user_name"));
            user.setAge(rs.getInt("age"));
            user.setSex(rs.getInt("sex"));
            user.setCreateDt(rs.getDate("create_dt"));

            userList.add(user);
        }
    }
//测试 用，可以直接运行   main进行


    //改成main来测试查询所有数据
    public static void main1(String[] args) {
        option dao = new option();

        try {
            List<UserVo> userList = dao.queryAll();
            for(UserVo user : userList) {
                System.out.println(user);
            }
        } catch (Exception e) {
            e.printStackTrace();
        }
    }


//    根据条件查询，定义一个 queryByParams 方法：
public List<UserVo> queryByParams(List<Map<String, Object>> params) throws Exception {
    Connection conn = connection.connectDB();
    StringBuilder sql = new StringBuilder("SELECT * FROM tbl_user_info WHERE 1=1 ");

    for(Map<String, Object> param : params) {
        sql.append(" and ");
        sql.append(" " + param.get("col") + " ");
        sql.append(" " + param.get("rel") + " ");
        sql.append(" " + param.get("value") + " ");
    }
    System.out.println(sql.toString());

    List<UserVo> userList = new ArrayList<UserVo>();

    Statement stmt = conn.createStatement();
    ResultSet rs = stmt.executeQuery(sql.toString());
    iteration(userList, rs);
    return userList;
}
//    这个方法可以自由选择查询的条件，只需要向方法中传入一个条件的List即可，这些条件都是由Map组成的，
// 每一个Map包含三个元素，col表示查询条件对应哪一列，rel表示查询条件的关系是什么，
// value是指查询条件的值。这样写集成了多查询条件的方法，很多的业务下，查询的逻辑可能很多，
// 这样写只用一个统一的方法就可以解决多种不同查询条件的业务逻辑。

    public static void main2(String[] args) {
        option dao = new option();

        List<Map<String, Object>> params = new ArrayList<Map<String,Object>>();
        Map<String, Object> param1 = new HashMap<String, Object>();
        param1.put("col", "user_name");
        param1.put("rel", "like");
        param1.put("value", "'%Tom%'");
        params.add(param1);

        Map<String, Object> param2 = new HashMap<String, Object>();
        param2.put("col", "sex");
        param2.put("rel", "=");
        param2.put("value", 1);
        params.add(param2);
        try {
            List<UserVo> userList = dao.queryByParams(params);
            for(UserVo user : userList) {
                System.out.println(user);
            }
        } catch (Exception e) {
            e.printStackTrace();
        }

    }
//
//    在这个main方法中设定了两个查询条件，一是user_name like %John%，另一个是sex=1，当然条件也可以是其他的，执行程序运行结果为：
//    SELECT * FROM tbl_user_info WHERE 1=1  and  user_name  like  '%John%'  and  sex  =  1 
//    UserVo [id=6, userName=John, age=19, sex=1, createDt=2016-06-24]
//
//    2 ）增加
//    现在在 option 中写一个 addUser 方法用于新增一条信息：
public void addUser(UserVo user) throws Exception {
    Connection conn = connection.connectDB();
    String sql = "INSERT INTO tbl_user_info(user_name, age, sex, create_dt) "
            + " VALUES(?, ?, ?, ?)";

    PreparedStatement pstmt = conn.prepareStatement(sql);
    pstmt.setString(1, user.getUserName());
    pstmt.setInt(2, user.getAge());
    pstmt.setInt(3, user.getSex());
    pstmt.setDate(4, new Date(new java.util.Date().getTime()));

    pstmt.execute();
}
//这个方法使用Connection.prepareStatement(String sql)方法获取一个PreparedStatement对象，使用这个方法可以传入带参数的SQL语句，而参数的值可以通过PreparedStatement.setXXX(int index, XXX value)的方法指定，其中XXX为各种不同的类型，index指定第几个参数的下标。指定了参数的值之后，便可以执行excute()方法执行SQL语句了。
//    接下来写一个main方法来验证这个增加的方法：
//测试三增加记录
    public static void main3(String[] args) {
        option dao = new option();
        UserVo user = new UserVo();

        user.setUserName("Tom");
        user.setAge(20);
        user.setSex(1);
        try {
            dao.addUser(user);
        } catch (Exception e) {
            e.printStackTrace();
        }
    }
//3）删除
//    接下来再写一个删除的方法，根据用户的id来删除数据：

    public void deleteUser(int id) throws Exception {
        Connection conn = connection.connectDB();
        String sql = "DELETE FROM tbl_user_info WHERE id = ?";

        PreparedStatement pstmt = conn.prepareStatement(sql);
        pstmt.setInt(1, id);

        pstmt.execute();
    }
//    然后写一个main方法来验证：
public static void main4(String[] args) {
    option dao = new option();

    try {
        dao.deleteUser(4);/*删除id为4的*/
    } catch (Exception e) {
        e.printStackTrace();
    }
}
//4）更新数据库
//    最后来看一下更新数据库：
public void updateUser(UserVo user) throws Exception {
    Connection conn = connection.connectDB();
    String sql = "UPDATE tbl_user_info SET user_name=?, age=?, sex=?"
            + " WHERE id=?";

    PreparedStatement pstmt = conn.prepareStatement(sql);
    pstmt.setString(1, user.getUserName());
    pstmt.setInt(2, user.getAge());
    pstmt.setInt(3, user.getSex());
    pstmt.setInt(4, user.getId());

    pstmt.executeUpdate();
}
//    从SQL语句中可以看出更新也是根据用户的id进行选择性的更新的。
//    写一个main方法来验证：
public static void main(String[] args) {
    option dao = new option();
    UserVo user = new UserVo();

    user.setUserName("Mary");
    user.setAge(30);
    user.setSex(0);
    user.setId(5);

    try {
        dao.updateUser(user);
    } catch (Exception e) {
        e.printStackTrace();
    }
}

}

```

