1、短域名生成

1)、路由到短域名生成处理函数,参数验证。

2)、根据长域名生成md5码的短域名地址。

3)、检测短域名地址在数据库中是否存在,如果存在,直接返回短域名地址。

4)、如果不存在,存入数据库中,产品名称,产品类型,短域名地址，长域名地址

5)、短域名地址作为key ,长域名地址作为value,存入redis中


2、短域名重定向

1)、短域名网址通过nginx重定向到一个本地lua脚本。

2)、lua脚本读取redis的key对应的value值，重定向到长域名。


redis缓存高可用设计：

1、redis 可以采用主从加哨兵模式。

2、redis cluster集群方式。

3、存储结构用简单的string key value结构就可以。


mysql数据库高可用设计：

1、方案1：mha一主从两从高可用加构设计。

2、方案2：Percona XtraDB Cluster 集群架构设计。

3、方案3：一主一从加keepalive 架构设计。

4、方案4：腾讯或阿里云高可用设计。

5、方案5：tidb 分布式集群高可用设计。

6、存储方案：产品名称，产品类型，短域名地址，长域名地址，创建时间，创建人相关字段就可以。

mail: zhouyh@139.com
