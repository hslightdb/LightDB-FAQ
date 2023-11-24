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
#### 1.1.6.3 all_col_comments                     
#### 1.1.6.4 all_cons_columns                     
#### 1.1.6.5 all_constraints                      
#### 1.1.6.6 all_dependencies                     
#### 1.1.6.7 all_ind_columns                      
#### 1.1.6.8 all_ind_expressions                  
#### 1.1.6.9 all_ind_partitions                   
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
