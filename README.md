### 命名规范
- 包名: `eg: service_test` 
- 文件: `eg: userDetial.py`
- 类名: `eg: class User:`
- 类中方法名: `eg: def getUser():`
- 文件方法名: `eg: def get_user():`
- 变量定义: `eg: user_id`
- 参数传递: `eg: user_id` 
- 创建对象: `eg: userDetial = UserDetial()`
- 配置文件: `eg: user_id`


### 线上库说明:
- 配置:
    ```
    ~/config/config.cfg
    ```

- mysql 
    ```
	说明: 缠论策略实例
	脚本: ~/data/db.sh
    ```

- liangpiao_k1 
    ```
	说明: 基础K线实例 2007-2016
	脚本: ~/data/db_k1.sh
    ```

- liangpiao_k2 
    ```
	说明: 基础K线实例 2017-2019
	脚本: ~/data/db_k1.sh
    ```

- tableTool.py
    ```
	参数: python tableTool.py $env $func $type $db_name

	例: python tableTool.py prod create back liangpiao_k2  (create 需要手建立 分表0)
    ```

- 数据库容量查看:
    ```
	select
	table_schema as '数据库',
	sum(table_rows) as '记录数',
	sum(truncate(data_length/1024/1024/1024, 2)) as '数据容量(GB)',
	sum(truncate(index_length/1024/1024/1024, 2)) as '索引容量(GB)'
	from information_schema.tables
	group by table_schema
	order by sum(data_length) desc, sum(index_length) desc;
    ```

- k线数据:
    ```
	索引:
		INDEX KEY `uniq_stock_cond` (`stock_no`,`level`,`snap_time`)
		变更
		UNIQUE KEY `uniq_stock_cond` (`stock_no`,`level`,`snap_time`)
    ```