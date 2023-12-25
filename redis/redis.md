# Redis

## 一、NoSql 介绍

- NoSql 的数据结构类型
  1. key-value 型 （Redis）
  2. document 型 （MongoDB）
  3. 列类型 （Hbase）
  4. Graph 类型 （Neo4j）

|          |              sql              |              nosql              |
| -------- | :---------------------------: | :-----------------------------: |
| 数据结构 |            结构化             |            非结构化             |
| 数据关联 |            关联的             |            无关联的             |
| 查询方式 |           SQL 查询            |           非 SQL 查询           |
| 事务特性 |             ACID              |              BASE               |
| 存储方式 |             磁盘              |              内存               |
| 扩展性   |             垂直              |              水平               |
| 使用场景 |        1. 数据结构固定        |        1. 数据结构不固定        |
|          | 2. 对数据安全性和一致性要求高 | 2. 对数据安全性和一致性要求不高 |
|          |                               |         3. 对性能要求高         |

## 二、Redis 介绍

- **Re**mote **Di**ctionary **S**erver（远程词典服务器），是一个基于内存的 key-value 型 NoSql 数据库
- 特征
  - key-value 型，value 支持多种不同数据结构
  - 单线程，每个命令具有原子性
  - 低延迟，速度快（基于内存，IO 多路复用，良好的编码）
  - 支持数据持久化
  - 支持主从集群，分片集群
  - 支持多语言客户端

## 三、Redis 的数据结构

- 在 Redis 中，key 一般是 String 类型，而 value 有多中类型
  - 基本类型
    - String
    - Hash
    - List
    - Set
    - SortSet
  - 特殊类型
    - GEO
    - BitMap
    - HyperLog

## 四、Redis 的常用命令

- 通用命令
  - `KEYS`：查看多个 key，例：`KEYS *`
  - `DEL`：删除 key
  - `EXISTS`：判断 key 是否存在
  - `EXPIRE`：设置 key 的过期时间
  - `TTL`：查看 key 的剩余有效时间
- String 类型常用命令
  - `SET`：添加或修改
  - `GET`：获取
  - `MSET`：批量添加
  - `MGET`：批量获取
  - `INCR`：自增 1
  - `INCRBY`：自增整形步长
  - `INCRBYFLOAT`：自增浮点步长
  - `SETNX`：若 key 不存在则添加一个 String 类型的键值对
  - `SETEX`：添加并设置过期时间
- Redis 中 key 可以使用`:`进行分级，例如：`项目名:业务名:类型:ID`
- Hash 类型常用命令
  - `HSET key field value`：添加或修改一个 hash 类型数据
  - `HGET key field`：获取一个 hash 类型数据 key 中一个 filed 对应的 value
  - `HMSET`：批量添加
  - `HMGET`：批量获取
  - `HGETALL`：获取一个 hash 类型数据 key 中所有 filed 和 value
  - `HKEYS`：获取一个 hash 类型数据 key 中所有 filed
  - `HVALS`：获取一个 hash 类型数据 key 中所有 value
  - `HINCRBY`：让一个 hash 类型数据 key 中的 field 自增整形步长
  - `HSETNX`：若 hash 类型数据 key 中的 field 不存在，则添加该 field 对应的 value