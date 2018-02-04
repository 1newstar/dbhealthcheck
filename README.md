# dbhealthcheck
  A SQL Scripts to check oracle db health.
  
  
#### PS：这只是个脚本的DEMO,有需要的可以自己对脚本进行扩展，我后期也会慢慢进行扩展，逐渐将其丰富起来，有问题和好的建议，也请欢迎咨询我。
  
# examples
## 1、准备工作
脚本中遇到的问题汇总。
#### <1>、Listagg拼接字符串时，报ORA-01489: result of string concatenation is too long 错误
这是oracle11g版本的一个BUG，在12.1.0.2版本中得到修复。<br>
解决办法：<br>
  a、升级oracle数据库版本到12.1.0.2+，因为11g的varchar2最大支持4K,12C扩展到了32k。（此方法基本不可用，你懂的，嘿嘿）。<br>
  b、创建个类型转换函数STRAGG，转换为clob数据类型。详见脚本：[Listagg](https://github.com/DragonWujj/dbhealthcheck/blob/master/Problems/listagg/ORA-01489%20result%20of%20string%20concatenation%20is%20too%20long%20%20(listagg).sql) <br>

#### <2>、外部表访问数据库Alert日志,详见脚本：[alertlog](https://github.com/DragonWujj/dbhealthcheck/blob/master/Problems/Alert%20log/alertlog) <br>


## 2、执行脚本
```
chown -R oracle:oinstall  db_health_check.sql
su - oracle 

$ sqlplus dbcheck/dbcheck
SQL*Plus: Release 11.2.0.3.0 Production on Wed May 3 18:00:45 2017

Copyright (c) 1982, 2011, Oracle.  All rights reserved.


Connected to:
Oracle Database 11g Enterprise Edition Release 11.2.0.3.0 - 64bit Production
With the Partitioning, OLAP, Data Mining and Real Application Testing options

SQL> @db_health_check.sql


```


## 3、示例图片：
![image](https://github.com/DragonWujj/dbhealthcheck/blob/master/examples.png)


## 4、联系方式
##### 电子邮箱：997702411@qq.com
##### QQ号：997702411（水平欠佳）
