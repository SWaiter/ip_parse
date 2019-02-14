# ip_parse
支持ipv4 v6解析

文件格式为geoip.mmdb

## 创建自定义函数的步骤
- 1.创建java类 extends org.apache.hadoop.hive.sql.exec.UDF
- 
- 2.需要实现evalute函数，evalute函数支持重载
- 
- 3.把程序打包放在机器上
- 
- 4.进入hive客户端，上传jar包到hdfs
- 
- 5.创建duf函数

```hql
hive (default)> add jar /home/datacenter/ip_parse-1.0-jar-with-dependencies.jar;
hive (default)> create temporary function get_location_ip as 'com.yoozoo.dc.IPParse';
hive (default)> select get_location_ip('61.174.15.215');
OK
亚洲|CN|1814991|中国|浙江省|null|null|120.1614|30.2936|null
Time taken: 0.115 seconds, Fetched: 1 row(s)
hive (default)> select get_location_ip('61.174.15.215','en');
OK
Asia|CN|1814991|China|Zhejiang|null|null|120.1614|30.2936|null
```