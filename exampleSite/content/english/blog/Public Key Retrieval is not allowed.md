很多种可能。
有一种是url问题
URI = "jdbc:mysql://localhost:3306/user?useSSL=false&serverTimezone=UTC";
传三个参数试试
DriverManager.getConnection(URI,USER,PASS);
