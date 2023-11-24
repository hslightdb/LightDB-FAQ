# LightDB Oracle特性

- [1、如何选择LightDB安装包进行安装及确认数据库模式](https://github.com/hslightdb/LightDB-FAQ#1%E5%A6%82%E4%BD%95%E9%80%89%E6%8B%A9lightdb%E5%AE%89%E8%A3%85%E5%8C%85)  
- [2、LightDB如何进行逻辑备份、恢复](https://github.com/hslightdb/LightDB-FAQ#2lightdb%E5%A6%82%E4%BD%95%E8%BF%9B%E8%A1%8C%E9%80%BB%E8%BE%91%E5%A4%87%E4%BB%BD%E6%81%A2%E5%A4%8D)  
- [3、如何进行LightDB客户端部署，LightDB是否有windows版客户端?](https://github.com/hslightdb/LightDB-FAQ#3%E5%A6%82%E4%BD%95%E8%BF%9B%E8%A1%8Clightdb%E5%AE%A2%E6%88%B7%E7%AB%AF%E9%83%A8%E7%BD%B2lightdb%E6%98%AF%E5%90%A6%E6%9C%89windows%E7%89%88%E5%AE%A2%E6%88%B7%E7%AB%AF)    
- [4、LightDB更改列属性语法](https://github.com/hslightdb/LightDB-FAQ#4lightdb%E6%9B%B4%E6%94%B9%E5%88%97%E5%B1%9E%E6%80%A7%E8%AF%AD%E6%B3%95)  
- [5、LightDB的递归语法](https://github.com/hslightdb/LightDB-FAQ#5lightdb%E7%9A%84%E9%80%92%E5%BD%92%E8%AF%AD%E6%B3%95)  
- [6、如何确定LightDB当前连接是否已满，满了怎么分析?](https://github.com/hslightdb/LightDB-FAQ#6%E5%A6%82%E4%BD%95%E7%A1%AE%E5%AE%9Alightdb%E5%BD%93%E5%89%8D%E8%BF%9E%E6%8E%A5%E6%98%AF%E5%90%A6%E5%B7%B2%E6%BB%A1)  
- [7、如何配置LightDB集成开发环境](https://github.com/hslightdb/LightDB-FAQ#7%E5%A6%82%E4%BD%95%E9%85%8D%E7%BD%AElightdb%E9%9B%86%E6%88%90%E5%BC%80%E5%8F%91%E7%8E%AF%E5%A2%83)  
- [8、如何实现LightDB访问Oracle表](https://github.com/hslightdb/LightDB-FAQ#8%E5%A6%82%E4%BD%95%E5%AE%9E%E7%8E%B0lightdb%E8%AE%BF%E9%97%AEoracle%E8%A1%A8)  
- [9、如何定位LightDB数据库中锁阻塞链情况](https://github.com/hslightdb/LightDB-FAQ#9%E5%A6%82%E4%BD%95%E5%AE%9A%E4%BD%8Dlightdb%E6%95%B0%E6%8D%AE%E5%BA%93%E4%B8%AD%E9%94%81%E9%98%BB%E5%A1%9E%E9%93%BE%E6%83%85%E5%86%B5)  
- [10、如果用户无法在自己的数据库中创建和删除schema怎么办](https://github.com/hslightdb/LightDB-FAQ#10%E5%A6%82%E6%9E%9C%E7%94%A8%E6%88%B7%E6%97%A0%E6%B3%95%E5%9C%A8%E8%87%AA%E5%B7%B1%E7%9A%84%E6%95%B0%E6%8D%AE%E5%BA%93%E4%B8%AD%E5%88%9B%E5%BB%BA%E5%92%8C%E5%88%A0%E9%99%A4schema%E6%80%8E%E4%B9%88%E5%8A%9E)  




### 1.1.6 系统视图

#### 1.1.6.1 all_all_tables     
**描述：**
all_all_tables 视图包含了当前用户可访问的所有表的信息，包括表名、表空间、所有者等。

| 列名                      | 描述                                                                                                                                                                                                                                                                                   |
|---------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| owner                     | 表所有者的用户名。                                                                                                                                                                                                                                                                     |
| table_name                | 表的名称。                                                                                                                                                                                                                                                                             |
| tablespace_name           | 表所在的表空间名称。                                                                                                                                                                                                                                                                  |
| cluster_name              | 如果表是一个簇表，则为簇的名称；否则为空。                                                                                                                                                                                                                                             |
| iot_name                  | 如果表是索引组织表（IOT），则为索引组织表的名称；否则为空。                                                                                                                                                                                                                             |
| status                    | 表的状态：VALID（有效）、INVALID（无效）、或 N/A（不适用）。                                                                                                                                                                                                                             |
| pct_free                  | 表中数据块中的空闲空间百分比。                                                                                                                                                                                                                                                       |
| pct_used                  | 表中数据块中的使用空间百分比。                                                                                                                                                                                                                                                       |
| ini_trans                 | 表的初始事务数。                                                                                                                                                                                                                                                                       |
| max_trans                 | 表的最大事务数。                                                                                                                                                                                                                                                                       |
| initial_extent            | 表的初始扩展大小（以字节为单位）。                                                                                                                                                                                                                                                     |
| next_extent               | 表的下一个扩展大小（以字节为单位）。                                                                                                                                                                                                                                                   |
| min_extents               | 表的最小扩展数。                                                                                                                                                                                                                                                                       |
| max_extents               | 表的最大扩展数。                                                                                                                                                                                                                                                                       |
| pct_increase              | 表的百分比增长。                                                                                                                                                                                                                                                                       |
| freelists                 | 表的自由列表数。                                                                                                                                                                                                                                                                       |
| freelist_groups           | 表的自由列表组数。                                                                                                                                                                                                                                                                     |
| logging                   | 表是否启用日志记录。                                                                                                                                                                                                                                                                   |
| backed_up                 | 表是否已备份。                                                                                                                                                                                                                                                                         |
| num_rows                  | 表中的行数。                                                                                                                                                                                                                                                                           |
| blocks                    | 表所占用的块数。                                                                                                                                                                                                                                                                       |
| empty_blocks              | 表中的空块数。                                                                                                                                                                                                                                                                         |
| avg_space                 | 表中块的平均使用空间。                                                                                                                                                                                                                                                                 |
| chain_cnt                 | 表中行的平均链接数。                                                                                                                                                                                                                                                                   |
| avg_row_len               | 表中行的平均长度（以字节为单位）。                                                                                                                                                                                                                                                     |
| avg_space_freelist_blocks | 自由列表块中的平均空间。                                                                                                                                                                                                                                                               |
| num_freelist_blocks       | 自由列表块数。                                                                                                                                                                                                                                                                         |
| degree                    | 表的并行度。                                                                                                                                                                                                                                                                           |
| instances                 | 表的实例数。                                                                                                                                                                                                                                                                           |
| cache                     | 表是否缓存。                                                                                                                                                                                                                                                                           |
| table_lock                | 表是否锁定。                                                                                                                                                                                                                                                                           |
| sample_size               | 表用于统计信息的样本大小。                                                                                                                                                                                                                                                             |
| last_analyzed             | 表的最后一次分析时间。                                                                                                                                                                                                                                                                 |
| partitioned               | 表是否分区。                                                                                                                                                                                                                                                                           |
| iot_type                  | 索引组织表的类型。                                                                                                                                                                                                                                                                     |
| temporary                 | 表是否为临时表。                                                                                                                                                                                                                                                                       |
| secondary                 | 表是否为次要表。                                                                                                                                                                                                                                                                       |
| nested                    | 表是否为嵌套表。                                                                                                                                                                                                                                                                       |
| buffer_pool               | 表的缓冲池类型。                                                                                                                                                                                                                                                                       |
| flash_cache               | 表的 Flash Cache 类型。                                                                                                                                                                                                                                                                 |
| cell_flash_cache          | 表的 Cell Flash Cache 类型。                                                                                                                                                                                                                                                             |
| row_movement              | 表的行移动性。                                                                                                                                                                                                                                                                         |
| global_stats              | 表是否拥有全局统计信息。                                                                                                                                                                                                                                                               |
| user_stats                | 表是否拥有用户统计信息。                                                                                                                                                                                                                                                               |
| duration                  | 统计信息持续时间。                                                                                                                                                                                                                                                                     |
| skip_corrupt              | 是否跳过损坏的块。                                                                                                                                                                                                                                                                     |
| monitoring                | 是否监控此表。                                                                                                                                                                                                                                                                         |
| cluster_owner             | 表所在集群的所有者。                                                                                                                                                                                                                                                                   |
| dependencies              | 表的依赖项。                                                                                                                                                                                                                                                                           |

#### 1.1.6.2 all_catalog     
**描述：**
all_catalog all_catalog 视图包含了当前用户可访问的所有表、视图和序列的信息。

**列信息：**

| 列名                | 描述                                                                                                                                                                                         |
|---------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| owner               | 对象所有者的用户名。                                                                                                                                                                           |
| table_name          | 表的名称。                                                                                                                                                                                     |
| table_type          | 对象的类型：表、视图或序列。                                                                                                                                                                    |
| clustered           | 如果对象是聚集表，则为 "YES"；否则为 "NO"。                                                                                                                                                      |
| secondary           | 如果对象是次要对象，则为 "YES"；否则为 "NO"。                                                                                                                                                     |
| index_table         | 如果对象是索引表，则为 "YES"；否则为 "NO"。                                                                                                                                                      |
| temporary           | 如果对象是临时对象，则为 "YES"；否则为 "NO"。                                                                                                                                                    |
| dropped             | 如果对象已删除，则为 "YES"；否则为 "NO"。                                                                                                                                                        |
| global_stats        | 如果对象包含全局统计信息，则为 "YES"；否则为 "NO"。                                                                                                                                              |
| user_stats          | 如果对象包含用户统计信息，则为 "YES"；否则为 "NO"。                                                                                                                                              |
| aux_stats           | 如果对象包含辅助统计信息，则为 "YES"；否则为 "NO"。                                                                                                                                              |
| parttype            | 分区类型：RANGE（范围分区）、HASH（哈希分区）、LIST（列表分区）或 COMPOSITE（组合分区）。                                                                                                           |
| refpartname         | 分区的引用对象的名称。                                                                                                                                                                         |
| supertype           | 如果对象是超类型，则为 "YES"；否则为 "NO"。                                                                                                                                                      |
| container_table     | 如果对象是容器表，则为 "YES"；否则为 "NO"。                                                                                                                                                     |
| editioned           | 如果对象是兼容版控制的，则为 "YES"；否则为 "NO"。                                                                                                                                                |
| sharded             | 如果对象是分片的，则为 "YES"；否则为 "NO"。                                                                                                                                                      |
| container_data      | 如果对象是容器数据对象，则为 "YES"；否则为 "NO"。                                                                                                                                                |
| object_id           | 对象的唯一标识符。                                                                                                                                                                             |
| secondary_instance  | 如果对象是次要实例，则为 "YES"；否则为 "NO"。                                                                                                                                                   |
| can_use_for_pivot   | 如果对象可以用于数据透视表，则为 "YES"；否则为 "NO"。                                                                                                                                           |
| partitioned         | 如果对象是分区对象，则为 "YES"；否则为 "NO"。                                                                                                                                                   |
| object_type         | 对象的类型，如 TABLE、VIEW、SYNONYM 等。                                                                                                                                                         |
| container_map       | 如果对象是容器映射，则为 "YES"；否则为 "NO"。                                                                                                                                                   |
| object_link         | 如果对象是对象链接，则为 "YES"；否则为 "NO"。                                                                                                                                                   |
| container_privilege | 如果对象是容器特权，则为 "YES"；否则为 "NO"。                                                                                                                                                   |
| storage             | 对象的存储类型，如 PERMANENT、UNDO、TEMPORARY 等。                                                                                                                                               |
| editioning_view     | 如果对象是版本控制的视图，则为 "YES"；否则为 "NO"。                                                                                                                                              |
| editioned_view      | 如果对象是已发布的版本控制视图，则为 "YES"；否则为 "NO"。                                                                                                                                       |
| object_name         | 对象的名称。                                                                                                                                                                                   |
| default_collation   | 对象的默认排序规则。                                                                                                                                                                           |
| edition_name        | 对象所属的版本名称。                                                                                                                                                                           |
| editionable         | 如果对象可以作为版本的一部分进行管理，则为 "YES"；否则为 "NO"。                                                                                                                                  |
| last_ddl_time       | 对象的最后一次 DDL 操作的时间。                                                                                                                                                                |
| inmemory            | 如果对象是内存优化的，则为 "ENABLED"；否则为 "DISABLED"。                                                                                                                                       |
| generated           | 如果对象是自动生成的，则为 "YES"；否则为 "NO"。                                                                                                                                                  |
| duration            | 对象的持续时间。                                                                                                                                                                               |
| secondary_object_id | 如果对象是次要对象，则为对象的次要标识符。                                                                                                                                                      |
| container_data_link | 如果对象是容器数据链接，则为 "YES"；否则为 "NO"。                                                                                                                                               |
| container_map_expr  | 容器映射的表达式。                                                                                                                                                                             |
| xml_schema_name     | XML 对象所属的模式名称。                                                                                                                                                                       |
| xml_schema_namespace| XML 对象的命名空间。                                                                                                                                                                           |


#### 1.1.6.3 all_col_comments

**描述：**
all_col_comments 视图包含了当前用户可访问的所有表和视图列的注释信息。

**列信息：**

| 列名            | 描述                                                                                                     |
|-----------------|----------------------------------------------------------------------------------------------------------|
| owner           | 列所属对象的所有者用户名。                                                                                 |
| table_name      | 列所属的表或视图的名称。                                                                                   |
| column_name     | 列的名称。                                                                                                 |
| comments        | 列的注释信息。                                                                                             |
| data_default    | 列的默认值。                                                                                               |
| nullable        | 如果列可为空，则为 "YES"；否则为 "NO"。                                                                   |
| data_type       | 列的数据类型。                                                                                             |
| data_length     | 列数据的长度（以字节为单位）。                                                                             |
| data_precision  | 数字列的精度（总位数）。如果列不是数字列，则为空。                                                       |
| data_scale      | 数字列的标度（小数点后的位数）。如果列不是数字列，则为空。                                               |
| num_distinct    | 列的唯一值数量。                                                                                           |
| low_value       | 列的最小值。                                                                                               |
| high_value      | 列的最大值。                                                                                               |
| density         | 列的密度。                                                                                                |
| num_nulls       | 列中的空值数量。                                                                                           |
| histogram       | 直方图的类型。                                                                                            |
| timestamp#      | 列的时间戳。                                                                                              |
| column_id       | 列的 ID。                                                                                                  |
| default_length  | 默认长度。                                                                                                |
| num_buckets     | 直方图的存储数量。                                                                                        |
| distinct_keys   | 直方图中的不同键的数量。                                                                                  |
| low_value_#     | 低值。                                                                                                    |
| high_value_#    | 高值。                                                                                                    |
| density_#       | 密度。                                                                                                    |
| num_nulls_#     | 空值数量。                                                                                                |
| histogram_#     | 直方图类型。                                                                                              |
| histogram_2     | 直方图类型 2。                                                                                            |
| drop_column     | 如果列已删除，则为 "YES"；否则为 "NO"。                                                                   |
| column_name_#   | 列名。                                                                                                    |
| user_generated  | 如果列是用户生成的，则为 "YES"；否则为 "NO"。                                                             |
| hidden_column   | 如果列是隐藏列，则为 "YES"；否则为 "NO"。                                                                 |
| virtual_column  | 如果列是虚拟列，则为 "YES"；否则为 "NO"。                                                                 |
| segment_column  | 如果列是分段列，则为 "YES"；否则为 "NO"。                                                                 |
| result_cache    | 如果列是结果缓存列，则为 "YES"；否则为 "NO"。                                                             |
| join_column     | 如果列是连接列，则为 "YES"；否则为 "NO"。                                                                 |
| valid_column    | 如果列是有效列，则为 "YES"；否则为 "NO"。                                                                 |
| duration_column | 如果列是持续列，则为 "YES"；否则为 "NO"。                                                                 |
| app_default     | 如果列有应用程序默认值，则为 "YES"；否则为 "NO"。                                                         |
| hidden_default  | 如果列有隐藏默认值，则为 "YES"；否则为 "NO"。                                                             |
| expression      | 列的表达式。                                                                                              |
| column_usage    | 列的用途。                                                                                               |
| comment$        | 评论。                                                                                                    |


#### 1.1.6.4 all_cons_columns

**描述：**
all_cons_columns 视图包含了与约束相关的列信息，包括约束名、列名、位置和数据类型。

**列信息：**

| 列名               | 描述                                                                                                     |
|--------------------|----------------------------------------------------------------------------------------------------------|
| owner              | 约束所属对象的所有者用户名。                                                                               |
| constraint_name    | 约束的名称。                                                                                             |
| table_name         | 约束所属的表的名称。                                                                                       |
| column_name        | 约束涉及的列的名称。                                                                                     |
| position           | 列在约束中的位置。                                                                                         |
| table_owner        | 表所有者的用户名。                                                                                         |
| data_default       | 列的默认值。                                                                                             |
| data_type          | 列的数据类型。                                                                                             |
| data_length        | 列数据的长度（以字节为单位）。                                                                             |
| data_precision     | 数字列的精度（总位数）。如果列不是数字列，则为空。                                                       |
| data_scale         | 数字列的标度（小数点后的位数）。如果列不是数字列，则为空。                                               |
| nullable           | 如果列可为空，则为 "YES"；否则为 "NO"。                                                                   |
| data_type_mod      | 列的类型修改器。                                                                                         |
| data_type_owner    | 数据类型所有者。                                                                                           |
| data_type_owner_id | 数据类型所有者的 ID。                                                                                      |
| data_type_link     | 数据类型链接。                                                                                             |
| column_id          | 列的 ID。                                                                                                  |
| default_length     | 默认长度。                                                                                                |
| data_precision_radix | 数据精度的基数。                                                                                         |
| hidden_column      | 如果列是隐藏列，则为 "YES"；否则为 "NO"。                                                                 |
| virtual_column     | 如果列是虚拟列，则为 "YES"；否则为 "NO"。                                                                 |
| segment_column     | 如果列是分段列，则为 "YES"；否则为 "NO"。                                                                 |
| internal_column_id | 内部列 ID。                                                                                               |
| hidden_default     | 如果列有隐藏默认值，则为 "YES"；否则为 "NO"。                                                             |
| user_generated     | 如果列是用户生成的，则为 "YES"；否则为 "NO"。                                                             |
| default_on_null    | 如果列默认为 NULL，则为 "YES"；否则为 "NO"。                                                               |
| identity_column    | 如果列是标识列，则为 "YES"；否则为 "NO"。                                                                 |
| join_column        | 如果列是连接列，则为 "YES"；否则为 "NO"。                                                                 |
| join_column_id     | 连接列的 ID。                                                                                             |
| table_link         | 表链接。                                                                                                  |
| column_usage       | 列的用途。                                                                                               |
| expression         | 列的表达式。                                                                                              |
| dependency         | 列的依赖项。                                                                                              |
| comment$           | 评论。                                                                                                    |
                
#### 1.1.6.5 all_constraints

**描述：**
all_constraints 视图包含了当前用户可访问的所有约束的信息，包括主键、外键、唯一键和检查约束等。

**列信息：**

| 列名             | 描述                                                                                                             |
|------------------|------------------------------------------------------------------------------------------------------------------|
| owner            | 约束所属对象的所有者用户名。                                                                                       |
| constraint_name  | 约束的名称。                                                                                                     |
| constraint_type  | 约束的类型，例如，'P' 表示主键约束，'U' 表示唯一键约束，'R' 表示引用约束，'C' 表示检查约束。                        |
| table_name       | 约束所属的表的名称。                                                                                               |
| search_condition | 如果约束是检查约束，则是检查条件。                                                                                   |
| r_owner          | 如果约束是引用约束，则是引用约束所属对象的所有者用户名。                                                             |
| r_constraint_name| 如果约束是引用约束，则是引用约束的名称。                                                                           |
| delete_rule      | 如果约束是引用约束，则是删除规则。                                                                                 |
| status           | 约束的状态。                                                                                                     |
| deferrable       | 如果约束是延迟的，则为 "DEFERRABLE"；否则为 "NOT DEFERRABLE"。                                                      |
| deferred         | 如果约束是延迟激活的，则为 "DEFERRED"；否则为 "IMMEDIATE"。                                                          |
| validated        | 如果约束是验证过的，则为 "VALIDATED"；否则为 "NOT VALIDATED"。                                                      |
| generated        | 如果约束是自动生成的，则为 "GENERATED NAME"；否则为 "USER NAME"。                                                   |
| bad              | 如果约束无效，则为 "BAD"；否则为 "N/A"。                                                                           |
| rely             | 如果约束是依赖性约束，则为 "RELY"；否则为 "N/A"。                                                                  |
| last_change      | 最后一次更改约束的时间。                                                                                           |
| index_owner      | 索引所属对象的所有者用户名。                                                                                       |
| index_name       | 索引的名称。                                                                                                     |
| invalid          | 如果约束是无效的，则为 "INVALID"；否则为 "N/A"。                                                                   |
| view_related     | 如果约束与视图相关，则为 "YES"；否则为 "NO"。                                                                      |
| delete_rule      | 删除约束的规则。                                                                                                 |
| r_owner          | 引用约束所属对象的所有者用户名。                                                                                   |
| r_constraint_name| 引用约束的名称。                                                                                                 |
| search_condition | 检查约束的条件。                                                                                                 |
| r_owner          | 引用约束所属对象的所有者用户名。                                                                                   |
| r_constraint_name| 引用约束的名称。                                                                                                 |
| search_condition | 检查约束的条件。                                                                                                 |
                     
#### 1.1.6.6 all_dependencies

**描述：**
all_dependencies 视图包含了对象之间的依赖关系信息，包括对象依赖类型、依赖的对象名称等。

**列信息：**

| 列名            | 描述                                                                                          |
|-----------------|-----------------------------------------------------------------------------------------------|
| owner           | 对象的所有者用户名。                                                                             |
| name            | 对象的名称。                                                                                    |
| type            | 对象的类型（例如，TABLE、VIEW、PACKAGE 等）。                                                     |
| referenced_owner| 引用对象的所有者用户名。                                                                         |
| referenced_name | 引用对象的名称。                                                                                |
| referenced_type | 引用对象的类型（例如，TABLE、VIEW、PACKAGE 等）。                                                 |
| dependent_owner | 依赖对象的所有者用户名。                                                                         |
| dependent_name  | 依赖对象的名称。                                                                                |
| dependent_type  | 依赖对象的类型（例如，TABLE、VIEW、PACKAGE 等）。                                                 |
| dependency_type | 依赖关系的类型（例如，NORMAL、IMPLICIT、REVALIDATION、HARD、FORCE、REFERENCE、REFERENCE_PARTITIONED）。|
                   
#### 1.1.6.7 all_ind_columns

**描述：**
all_ind_columns 视图包含了所有索引的列级别信息，包括索引名、表名、列名等。

**列信息：**

| 列名             | 描述                                                               |
|------------------|--------------------------------------------------------------------|
| index_owner      | 索引所属对象的所有者用户名。                                         |
| index_name       | 索引的名称。                                                       |
| table_owner      | 索引所属的表的所有者用户名。                                         |
| table_name       | 索引所属的表的名称。                                                 |
| column_name      | 索引涉及的列的名称。                                               |
| column_position  | 列在索引中的位置。                                                   |
| column_length    | 列的长度。                                                         |
| char_length      | 列的字符长度。                                                     |
| descend          | 如果列是降序排序的，则为 "DESC"；否则为 "ASC"。                       |
| table_name       | 索引所属的表的名称。                                                 |
| table_type       | 索引所属的表的类型。                                                 |
                    
#### 1.1.6.8 all_ind_expressions

**描述：**
all_ind_expressions 视图包含了所有索引的表达式级别信息，包括索引名、表名、索引表达式等。

**列信息：**

| 列名            | 描述                                               |
|-----------------|----------------------------------------------------|
| index_owner     | 索引所属对象的所有者用户名。                         |
| index_name      | 索引的名称。                                       |
| table_owner     | 索引所属的表的所有者用户名。                         |
| table_name      | 索引所属的表的名称。                                 |
| column_expression | 索引的列级表达式。                                 |
| column_position | 表达式在索引中的位置。                               |
| column_length   | 表达式的长度。                                     |
| char_length     | 表达式的字符长度。                                 |

                 
#### 1.1.6.9 all_ind_partitions

**描述：**
all_ind_partitions 视图包含了所有索引分区的信息，包括索引名、分区名、表名等。

**列信息：**

| 列名             | 描述                                               |
|------------------|----------------------------------------------------|
| index_owner      | 索引所属对象的所有者用户名。                         |
| index_name       | 索引的名称。                                       |
| partition_name   | 分区的名称。                                       |
| subpartition_count| 子分区的数量。                                     |
| high_value       | 分区的高值。                                       |
| table_name       | 索引所属的表的名称。                                 |
| table_owner      | 索引所属的表的所有者用户名。                         |
| table_partitioned| 表是否分区。若分区，则为 "YES"；否则为 "NO"。         |

                 
#### 1.1.6.10 all_ind_statistics                   
#### 1.1.6.11 all_index_usage                      
#### 1.1.6.12 all_indexes                          
#### 1.1.6.13 all_jobs                             
#### 1.1.6.14 all_mview_comments                   
#### 1.1.6.15 all_mview_logs                       
#### 1.1.6.16 all_mviews                           
#### 1.1.6.17 all_objects                          
all_part_indexes                     
all_part_key_columns                 
all_part_tables                      
all_procedures                       
all_sequences                        
all_source                           
all_subpart_key_columns              
all_synonyms                         
all_tab_col_statistics               
all_tab_cols                         
all_tab_columns                      
all_tab_comments                     
all_tab_modifications                
all_tab_partitions                   
all_tab_statistics                   
all_tab_subpartitions                
all_tables                           
all_trigger_cols                     
all_triggers                         
all_types                            
all_users                            
all_views                            
col                                  
cols                                 
dba_all_tables                       
dba_catalog                          
dba_col_comments                     
dba_cons_columns                     
dba_constraints                      
dba_data_files                       
dba_dependencies                     
dba_ind_columns                      
dba_ind_expressions                  
dba_ind_partitions                   
dba_ind_statistics                   
dba_index_usage                      
dba_indexes                          
dba_jobs                             
dba_jobs_running                     
dba_mview_comments                   
dba_mview_logs                       
dba_mviews                           
dba_objects                          
dba_objects_list_without_pkg         
dba_part_indexes                     
dba_part_key_columns                 
dba_part_tables                      
dba_procedures                       
dba_role_privs                       
dba_roles                            
dba_segments                         
dba_sequences                        
dba_source                           
dba_source_all                       
dba_subpart_key_columns              
dba_synonyms                         
dba_tab_col_statistics               
dba_tab_cols                         
dba_tab_columns                      
dba_tab_comments                     
dba_tab_modifications                
dba_tab_partitions                   
dba_tab_statistics                   
dba_tab_subpartitions                
dba_tables                           
dba_tablespaces                      
dba_trigger_cols                     
dba_triggers                         
dba_types                            
dba_users                            
dba_views                            
dict                                 
dictionary                           
dual                                 
gv$nls_parameters                    
ind                                  
nls_database_parameters              
nls_instance_parameters              
nls_session_parameters               
obj                                  
plan_table                           
product_component_version            
tab                                  
tabs                                 
user_all_tables                      
user_catalog                         
user_col_comments                    
user_cons_columns                    
user_constraints                     
user_dependencies                    
user_ind_columns                     
user_ind_expressions                 
user_ind_partitions                  
user_ind_statistics                  
user_index_usage                     
user_indexes                         
user_jobs                            
user_mview_comments                  
user_mview_logs                      
user_mviews                          
user_objects                         
user_part_indexes                    
user_part_key_columns                
user_part_tables                     
user_procedures                      
user_role_privs                      
user_segments                        
user_sequences                       
user_source                          
user_subpart_key_columns             
user_synonyms                        
user_tab_col_statistics              
user_tab_cols                        
user_tab_columns                     
user_tab_comments                    
user_tab_modifications               
user_tab_partitions                  
user_tab_statistics                  
user_tab_subpartitions               
user_tables                          
user_tablespaces                     
user_trigger_cols                    
user_triggers                        
user_types                           
user_users                           
user_views                           
v$nls_parameters  

### 1.1.7 字符集和字符序

| 特性       | Oracle        | LightDB               |
|------------|---------------|-----------------------|
| UTF-8      | AL32UTF8      | UTF-8                 |
| GBK        | ZHS16GBK      | GBK/GB18030 2022      |

### 1.1.8 其他特性

| 特性                            | Oracle                | LightDB                           |
|---------------------------------|-----------------------|-----------------------------------|
| csv文本数据导出与加载           | SQLLOADER、SQLULDR    | COPY、LTULDR、LTLOADER、LT_BULKLOAD |
| 逻辑二进制数据导出与加载       | EXPDP、IMPDP、EXP、IMP | LT_DUMP、LT_RESTORE             |

## 1.2 高级特性

### 1.2.1 事务一致性与隔离级别

| 特性         | Oracle               | LightDB                        |
|--------------|----------------------|--------------------------------|
| 隔离级别     | 支持SQL标准的四种隔离级别，包括读未提交、读已提交、可重复读和串行化。默认读已提交 | 支持，同Oracle |
| 并发控制机制 | Oracle使用多版本并发控制（MVCC）机制来保证并发访问的数据一致性。读写不相互阻塞 | LightDB使用行记录信息来记录当前事务号，以此实现多版本并发控制 |
| Undo         | Oracle使用undo段来保存旧版本的数据。当其他事务需要读取某个版本的数据时，可以从undo段中获取 | LightDB中通过行记录中xmin/xmax标记事务信息来进行回滚 |

### 1.2.2 优化器

| 特性       | Oracle                                                                                              | LightDB                                                                   |
|------------|-----------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------|
| 优化器     | 提供CBO和RBO两种优化器。提供了多种优化手段如优化器提示、SQL计划基线等。支持任意复杂的SQL查询转换、布隆过滤等并且优化能力很强 | 支持基于成本的优化器CBO，生成执行计划，不支持布隆过滤器，对于复杂SQL支持良好 |
| 执行器     | Oracle执行器支持各种算子，包括各种连接方式、并行、下推、物化、平铺、各种访问方式                       | LightDB执行器也支持各种算子、并行、链接算法、平铺、分区裁剪                 |

### 1.2.3 优化器提示

| 特性         | Oracle                                                                                                 | LightDB                                                                           |
|--------------|--------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------|
| 优化器提示   | Oracle支持完备的优化器提示、包含并行执行、表关联方式控制、星型链接、跨库访问等多种优化器提示           | LightDB支持完备的优化器提示、包含并行执行、表关联方式控制、星型链接等多种优化器提示，暂不支持跨库访问 |

### 1.2.4 高可用

| 特性      | Oracle                                                                                     | LightDB                                                                               |
|-----------|--------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------|
| 高可用    | 使用RAC来实现高可用性。RAC是一种共享磁盘数据库集群解决方案，允许多个节点访问同一数据库，提供了故障转移、负载均衡等功能。此外，Oracle还提供了数据复制技术Data Guard | 使用流复制Streaming Replication来实现高可用性。主库将变更操作的Write-Ahead Logs发送到从库，从库根据这些日志来更新其数据 |

### 1.2.5 备份恢复

| 特性    | Oracle                                                                                               | LightDB                                                                                           |
|---------|------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------|
| 备份    | 逻辑备份：expdp和exp工具导出数据库的逻辑结果和数据；物理备份：使用RMAN（Recovery Manager）工具进行数据库级备份 | 逻辑备份：lt_dump/lt_dumpall来备份数据库或表的逻辑结果和数据；物理备份：使用lt_basebackup或拷贝备份LTDATA目录 |
| 恢复    | RMAN可以恢复整个数据库、单个表空间、单个数据文件或者某个时间点的数据。它还可以在恢复过程中自动处理故障。    | 对于lt_dump的备份，使用lt_restore进行逻辑恢复。对于lt_basebackup的备份，可以直接将备份文件拷贝到数据目录进行物理恢复 |

### 1.2.6 安全特性

| 特性        | Oracle                                                                                                   | LightDB                                                                                   |
|-------------|----------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------|
| 安全相关    | Oracle支持TDE透明加密、提供数据库级别审计日志，静态数据加密，IP白名单访问控制                            | 支持TDE透明加密，OPE保序加密，SM国密，提供多种数据库级别审计日志，IP访问控制                 |

### 1.2.7 分区支持

| 特性         | Oracle                                                                                                   | LightDB                                                                                   |
|--------------|----------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------|
| 分区支持     | LightDB支持List、hash、range分区和组合二级分区方式，同时支持global索引、分区索引、分区裁 | 支持广播、hash hash、random多种并行的数据分发处理方式，并行不支持bloom过滤 |
