# database
1. week
- week
  1. 全局数据库名(大写)
  - 账号(安装)
    - 超级管理员 sys
    - 普通管理员 system
    - [ ] 示例方案
  - 启动数据库
    1. DOS命令方式
      - sqlplus 用户名/密码 [AS SYSDBA]
      - sqlplus 用户名/密码@database_name
        - 超级管理员需加[AS SYSDBA]
      - sql
    - 图形化界面
      - SQL Plus
    - sqlplusw 用户名/密码 [AS SYSDBA] dos转为图形化界面
  - show user
  - 连接数据库
    - conn 用户名/密码 [AS SYSDBA]
      - 通过conn可以更改当前管理员权限
  - 断开数据库
    - disc
  - 加锁、解锁
    - alter user 用户名 account lock|unlock
      - alter user 用户名
  - 查询当前账号下的所有表
    - select * from tab
  - 查看表结构
    - desc(describe) 表名
    |emp表|雇员表|
  - 查看表中的所有数据
    - select * from 表名
  - 设置页面宽度
    - set linesize 整数
  - 设置每页显示的行数 (不是记录数)
    - set pagesize 整数
  - 在缓冲区里进行修改操作
    1. 编辑缓冲区
      - ed(edit)
      - append
      - del
    - 执行缓冲区
      - r(run) 或 /
    - 查看缓冲区
      - l(list)
    - 清空缓冲区
      - clear buffer
  - 修改密码
    - alter user 用户名 identifed by 新密码
    - password 用户名
  - 密码失效(管理员)
    - alter user 用户名 password expire
  - 文件操作(若为.sql可省略后缀)
    1. 创建脚本文件
      - save 文件 (create)(保存缓冲区中的内容)
      - save 文件 replace
      - save 文件 append
    - 装载
      - get 文件
      - get 文件 nolist (不显示缓冲区内容)
    - 脚本文件的执行(装载并执行)
      - start 文件
      - **@文件**
  - 注释
    1. 多行注释 `/*多行注释*/`
    - 单行注释 `--单行注释`
    - remark (放在一行一句的头部)
- week
  - 常用函数
    - 单行函数: 字符，数值，日期，通用
    - 多行函数
  - 字符函数
    1. 大小写控制函数 lower upper initcap(每个单词的首字母大写)
    - 字符控制函数 concat(列连接) substr length instr lpad rpad trim(去掉前后指定字符，默认去掉空格)
    - 数值 round(截取小数点后几位) trunc mod
    - 日期 sysdate
      - 日期的算术运算
        - 日期
          - months_between
          - add_months
          - next_day
          - last_day
          - extract
        - 转换函数 fm 9 $ L
          - to_char(hiredate, 'YYYY-MM-DD')
          - to_char(sysdate,'yyyy-mm-dd hh12:mi:ss am')
          - to_char(sysdate,'fmyyyy-mm-dd hh12:mi:ss am') 去掉前导0
          - to_char(sal,, '9999-99')
        - to_data
        - to_number
      - 通用
        - nvl
        - nvl2
        - decode
          - select ename, decode(job, 'CLERK', '办事员',
                                      'SALESMAN', '销售人员',
                                      '其他')
        - case when then end
- week(PL/SQL)
  - Oracle
  ```
  BEGIN
    NULL;
  END;
  /
  ```
  ```
  DECLARE
    v_date DATE;
  ```
  `variable_name [CONSTANT] type [NOT NULL] [:=value]` (定义非空则必须给初值)
  ``
- week
  - 左右连接(哪边缺数据加在哪边)(只允许添加一个链接)
    - 左链接(+)在等号的右边
    - 右链接(+)在等号的左边
  - SQL1999
    1. 交叉连接
      - `select * from table1 CROSS JOIN table2`
    - 自然连接
      - `SELECT 列名 FROM　表名1　NATURAL JOIN 表名2`
    - using 子句
      - `SELECT 列名 FROM 表名1 JOIN 表名2 USING(列名)`
    - on 子句
      - `SELECT 列名 FROM 表名1 JOIN 表名2 ON(条件)`
    - 左右连接
      - `SELECT 列名 FROM 表名1 RIGHT OUTER JOIN 表名2 ON(条件)`
      - `SELECT 列名 FROM 表名1 LEFT OUTER JOIN 表名2 ON(条件)`
  - 组函数及分组统计
    - COUNT()
    - MAX()
    - MIN()
    - SUM()
    - AVG()
    - 分组操作
      ```
      SELECT
      FROM
      WHERE
      GROUP BY
      HAVING
      ORDER BY
      ```
    - ROLLUP() 做出横向的小计
    - CUDE() 做横向和纵向的小计
  - 子查询
    - in
    - any
    - all
  - 合并查询:合并多个SELECT语句查询的结果
    1. UNION 并集,去掉重复行
    - UNION ALL 不去掉重复行
    - INTERSECT 交集
    - MINUS 差集
  - 数据更新操作
    - 插入
      - 标准写法
        - INSERT INTO 表名(列名1, 列名2) VALUES(值1, 值2...)
        - TO_DATE('20xx-1y-2z', 'yyyy-mm-dd')
      - 省略写法
        - `INSERT INTO 表名 VALUES(值1, 值2...)` 值的顺序和格式必须和表中顺序格式相同
    - 修改
      - 全部修改
        - `UPDATE 表名 SET 列名=值,...`
      - 局部修改
        - `UPDATA 表名 SET 列名=值,... WHERE 条件`
        - `UPDATE 表名 SET (列名1, ...) = (SELECT 列名1, ...) WHERE`
    - 删除
      - 全部删除
        - DELETE [FROM] 表名
      - 局部删除
        - DELETE [FROM] 表名 (WHERE 条件)
      - 增删改，最后必须加上事务处理操作
  - 复制表
    - `CREATE TABLE 新表名 AS 数据来源` 数据来源:select语句
- week
  - 插入单值
    - INSERT INTO (SELECT empno, ename FROM myemp1) VALUES(值)
    - 利用临时表dual
      - INSERT INTO myemp1 (empno, ename) SELECT 2, 'allen' FROM dual'
    - 利用子查询插入数据(批量)
      - INSERT INTO myemp1 SELECT * FROM emp;
      - 范例:
        - INSERT INTO myemp1 SELECT 1100, 'TOM1', job, mgr, hiredate, sal, comm, deptno FROM emp WHERE empno = 7788;
      - 针对大量的数据，最好采用的不写入日志文件中，因为这样可以提高执行效率。想要实现这个效果: `"/*+APPEND*/"`
        - `INSERT /*+APPEND*/ INTO ...; commit;`
  - 向多个表中插入数据
    1. 无条件多表插入 - 备份
      ```
      INSERT ALL
      INTO 表1 VALUES(列1, ...)
      INTO 表2 VALUES(列1, ...)
      ...
      SELECT子查询语句(列名相同)
      ```
    - 有条件多表插入 - 分区表
      ```
      INSERT ALL/FIRST
      WHEN 条件1 THEN INTO 表1(列1,...)
      WHEN 条件2 THEN INTO 表2(列1,...)
      ...
      ELSE INTO 表n(列1,...)
      SELECT子查询语句
      ```
    - 多表插入的应用
      - 非关系型数据库--关系型数据库
      - 列转行
      ```
      INSERT ALL
      INTO sale_info VALUES(emp_id, week_id, sale_MON)
      INTO sale_info VALUES(emp_id, week_id, sale_TUE)
      ...
      SELECT * FROM sale_source_data;
      commit;
      ```
    - 截断表
      - truncate table 表名(在别的数据库中可能可以省略table,但关系型数据库中不可以省略)
    - ROWNUM:表示行号,但它是伪列
      - 一般用来做分页的操作
      - `ROWNUM <= 5`
      - FROM 子查询 --子查询中有ROWNUM列
    - 锁
    - 格式化查询
      - 对列格式化或查询报表格式化
        - 格式化列
          - col[umn]
            - heading
            - justify
            - clear 清除格式
            - format 定义显示的格式  a宽度 7几个字符
        - ```
        column ename heading 员工名 justify center format a7
        column sal heading 工资 justify left format L9999.99
        ```
        - `SELECT ename, sal FROM emp WHERE empno=7844`
        - 显示某个列的格式
          - `col sal`
        - 清除格式
          - `col sal clear`
          - `clrear column`
- week
      - 压缩列
        - BREAK ON 列名 [SKIP 值] (分组之后的间距)
        ```
        BREAK ON deptno [SKIP 1]
        SELECT deptno, ename FROM emp ORDER BY deptno
        ```
        - 为了实现组函数的分组统计操作，可以与compute命令结合使用
        - `COMPUTE 组函数 LABEL 标签内容 OF [expression / 列 ON 分组条件]`
        ```
        BREAK ON deptno;
        COMPUTE AVG LABEL '平均工资' OF sal ON deptno;
        SELECT deptno, ename, sal FROM emp ORDER BY deptno;
        ```

    - 设置标题和页脚
      - TTITLE 标题
      - BTITLE 页脚
      ```
      TTITLE CENTER '标题'
      BTITLE RIGHT '页脚'
      SELECT ...
      TTITLE --显示标题样式
      BTITLE --显示页脚样式
      TTITLE OFF; --关闭标题样式
      BTITLE OFF;
      ```
    - 层次查询
      ```
      SELECT [LEVEL] 列名
      FROM 表名
      [WHERE 条件]
      [START WITH 列名=值]
      [CONNECT BY PRIOR 关系]
      ```
      ```
      SELECT empno, ename, mgr FROM emp
      START WITH empno=7839
      CONNECT BY PRIOR empno=mgr;
      ```
      ```
      SELECT LPAD(' ', 5 * LEVEL - 1) || empno EMPNO, LPAD(' ', 5 * LEVEL - 1) || ename ename
      FROM emp
      START WITH empno=7839
      CONNECT BY PRIOR empno=mgr;
      ```

  - 建表
    - char
    - varchar2
    - DATE
    - Number(6)
    - Number(6, 2)
    - clob
    - blob
    ```
    CREATE TABLE 表名(
      列名1 数据类型 [defaul 默认值] PRIMARY KEY,
      列名2 数据类型 [defaul 默认值],
      ...
      )
    ```
  - 删除表
    - `DROP TABLE 表名` 把表放在回收站里面
    - `FLASHBACK TABLE 表名 TO BEFORE DROP` 从回收站里找回表
    - `DROP TABLE 表名 PURGE` 直接删除不经过回收站
    - `PURGE TABLE 表名` 删除回收站里的表
    - `SELECT object_name, original_name, operation, type FROM recyclebin` 从回收站里查看(回复只能回复最近的一个)
    - `PURGE recyclebin;` 清空回收站
  - 修改表
    - 增加列
      - ALTER TABLE 表名 ADD(列名1 数据类型 [defaul 默认值],...)
    - 修改列的数据类型和长度
      - ALTER TABLE 表名 MODIFY(列名1 数据类型 [defaul 默认值],...)
    - 修改列名
      - ALTER TABLE 表名 RENAME COLUMN 原列名 TO 新列名
    - 删除列
      - ALTER TABLE 表名 DROP COLUMN 列名
    - 修改列的无效状态
      - ALTER TABLE 表名 SET UNUSED COLUMN 列名
    - 删除无效列
      - ALTER TABLE 表名 DROP UNUSED COLUMNS
  - 表的重命名
    - RENAME 旧表名 TO 新表名
  - 约束
    - 约束的分类
      1. 主键约束:不能重复，不可为空
      - 唯一约束: 不可以重复，不可以为空
      - 非空约束: 不可以为空
      - 检查约束: 检查一个列的内容是否合法
      - 外键约束:
    ```(推荐)
    -- 表级别约束
    DROP TABLE 表名;
    CREATE TABLE 表名(
      列名1 数据类型 [defaul 默认值],
      列名2 数据类型 [defaul 默认值],
      ...,
      CONSTRAINT 自定义的提示信息 PRIMARY KEY(列名1) --自定义错误提示信息
      )
    ```
    ```
    -- 列级别约束
    DROP TABLE 表名;
    CREATE TABLE 表名(
      列名1 数据类型 [defaul 默认值] CONSTRAINT 自定义的提示信息 PRIMARY KEY,
      列名2 数据类型 [defaul 默认值],
      ...
    ```
- week
  - 唯一约束
  ```(推荐)
  -- 表级别约束
  DROP TABLE 表名;
  CREATE TABLE 表名(
    列名1 数据类型 [defaul 默认值] ,
    列名2 数据类型 [defaul 默认值] ,
    ...,
    CONSTRAINT 自定义的提示信息 PRIMARY KEY(列名1) --自定义错误提示信息
    CONSTRAINT 自定义的提示信息 UNIQUE(列名)
    )
  ```
  ```
  -- 列级别约束
  DROP TABLE 表名;
  CREATE TABLE 表名(
    列名1 数据类型 [defaul 默认值] ,
    列名2 数据类型 [defaul 默认值] UNIQUE,
    ...,
    CONSTRAINT 自定义的提示信息 PRIMARY KEY(列名1) --自定义错误提示信息
    )
  ```
  - 非空约束 (只有列级别,没有表级别)
  ```
  -- 列级别约束
  DROP TABLE 表名;
  CREATE TABLE 表名(
    列名1 数据类型 [defaul 默认值] ,
    列名2 数据类型 [defaul 默认值] NOT NULL,
    ...,
    CONSTRAINT 自定义的提示信息 PRIMARY KEY(列名1) --自定义错误提示信息
    )
  ```
  - 检查约束
  ```
  -- 列级别
  DROP TABLE 表名;
  CREATE TABLE 表名(
    列名1 数据类型 [defaul 默认值] CHECK(列名 IN(a, b, ...)),
    列名2 数据类型 [defaul 默认值] NOT NULL CHECK(列名 BETWEEN a AND b),
    ...,
    CONSTRAINT 自定义的提示信息 PRIMARY KEY(列名1) --自定义错误提示信息
    )
  ```
  ```(推荐)
  -- 表级别约束
  DROP TABLE 表名;
  CREATE TABLE 表名(
    列名1 数据类型 [defaul 默认值] ,
    列名2 数据类型 [defaul 默认值] ,
    ...,
    CONSTRAINT 自定义的提示信息 CHECK(列名 IN(a, b, ...)) --自定义错误提示信息
    )
  ```
  - 外键约束
  ```
  -- 列级别
  CREATE TABLE 表名(
    列名1 数据类型 [defaul 默认值] PRIMARY KEY,
    列名2 数据类型 [defaul 默认值] REFERENCES 表名(列名),
    ...
    )
  ```
  ```(推荐)
  -- 表级别约束
  DROP TABLE 表名;
  CREATE TABLE 表名(
    列名1 数据类型 [defaul 默认值] ,
    列名2 数据类型 [defaul 默认值] ,
    ...,
    CONSTRAINT 自定义的提示信息 FOREIGH KEY(列名) REFERENCES 表名(列名) --自定义错误提示信息
    )
  ```
  - 追加约束 表级别的(不能添加非空)
  ALTER TABLE 表名 ADD 约束
    - 修改列->修改为非空
  - 删除约束
    - 删除列级约束
    ALTER TABLE 表名 DROP 约束
    `ALTER TABLE 表名 DROP PRIMARY KEY`
    - 删除表级约束
    `ALTER TABLE 表名 DROP CONSTRAINT 自定义错误信息`
  - 约束的禁用和启动
    - 禁用
    `ALTER TABLE 表名 DISABLE 约束`
    ```
    ALTER TABLE 表名 DISABLE PRIMARY KEY
    ALTER TABLE 表名 DISABLE CONSTRAINT 自定义错误信息
    ```
    - 启动
    `ALTER TABLE 表名 ENABLE 约束`
  - 查看约束
    `SELECT * FROM user_constraint WHERE table_name='表名(大写)'`
  - 视图
    - 创建视图
      `CREATE VIEW v_emp AS SELECT语句`
      ```
      CREATE [OR REPLACE] [FORCE|UNFORCE] VIEW 视图名
      AS
      SELECT 语句
      [WITH CHECK OPTION 约束]
      [WITH READ ONLY];
      ```
    - 删除视图
      `DROP VIEW 视图名`
    - SELECT * FROM user_views; 查看视图名
  - 同义词(别名)
    - CREATE SYNONYM s_emp FOR 用户名
    - DROP SYNONYM s_emp;
  - 序列
    - 创建序列
    ```
    CREATE SEQUENCE 序列名
    [INCREMENT BY N] (每次递增加N)
    [START WITH N] (从N开始)
    [MAXVALUE N]
    [MINVALUE N]
    [CYCLE|NOCYCLE]
    [CACHE N| NOCACHE] (默认20)
    ```
- week
    - 修改序列 空间配额不可以减小
    ```
    ALTER SEQUENCE test_seq
    [INCREMENT BY N]
    [MAXVALUE N]
    [MINVALUE N]
    [CYCLE|NOCYCLE]
    [CACHE N| NOCACHE]
    -- 不能有start with
    ```
    - 删除序列
    `DROP SEQUENCE 序列名`
  - ROWID 是系统自动产生的,能唯一标识出每一条数据库记录的物理地址,通过rowid可以快速定位到一条行记录
    - 数据对象编号 6bits 相关文件编号 3bits 块编号 6btis 行编号 3bits
  - 索引
    - 单列索引 索引建立在一列上
    - 复合索引 索引建立在某几列上
    - 创建索引
      - 自动创建
        - 当建表的时候,使用了PRIMARY KEY 或者 UNIQUE约束时,数据库会自动创建一个索引
      - 手工创建
        -
        ```
        CREATE INDEX 索引名
        ON 表名(列名1, 列名2,...)
        -- 索引名的命名规范:idx_表名_列名  
        ```
    - 删除索引
      - `DROP INDEX 索引名`
  - 用户管理
    1. Oracle 的初始用户
      - SYS 超级管理员 权限最大 可以启动修改 关闭数据库
      - SYSTEM 一般管理员 辅助管理员 不可以启动和关闭数据,主要进行一些管理操作:创建用户,删除用户等
      - SCOTT 用来测试网络链接
      - PUBLIC 本质是一个用户组,数据库中的任何一个用户都属于该组,因为为数据库中每个用户授权,可以把授权直接赋予PUBLIC组
    - 用户属性
      1. 身份认证: 数据库身份认证 外部身份认证 全局身份认证
      - 默认表空间
      - 临时表空间
      - 表空间配额
      - 概要文件
      - 账号状态
    - 创建用户
      ```
      CREATE USER 用户名 IDENTIFIED
      [BY 密码 EXTERNALLY | GLOBALLY AS 'external_name']
      [DEFAULT TABLESPACE tablespace_name]
      [TEMPORARY TABLESPACE temp_tablespace_name]
      [QUOTA n K|M|UNLIMITED ON tablespace/-name]
      [PROFILE profile_name]
      [PASSWORD EXPIRE]
      [ACCOUNT LOCK|UNLOCK]
      ```
    - 修改账号
      ```
      ALTER USER 用户名 [IDENTIFIED]
      [BY 密码 EXTERNALLY | GLOBALLY AS 'external_name']
      [DEFAULT TABLESPACE tablespace_name]
      [TEMPORARY TABLESPACE temp_tablespace_name]
      [QUOTA n K|M|UNLIMITED ON tablespace/-name]
      [PROFILE profile_name]
      [DEFAULT ROLE role_list | ALL [EXCEPT role_list] | NONE]
      [PASSWORD EXPIRE]
      [ACCOUNT LOCK|UNLOCK]
      ```
    - 删除用户
    `DROP USER 用户 [CASCADE]`
    - 查询用户
      - ALL_USERS
      - DBA_USERS
      - USER_USERS
      - DBA_TS_QUOTAS
      - USER_TS_QUOTAS
      - V$SESSION
      - V$OPEN_CURSOR
    - 权限管理: 系统权限 对象权限
      - 系统权限
        1. 注意事项
          1. 只有DBA才能拥有ALTER DATABASE 系统权限
          - 应用程序开发者一般需要拥有的是CREATE TABLE, CREATE VIEW, CREATE INDEX 等系统权限
          - 普通用户一般只有CREATE SESSION系统权限
          - 只有授权时带有WITH, ADMIN, OPTINO子句时,用户才可以将获得的系统权限再授予给其他用户,即系统权限的传递性
        - 语法格式
        `GRANT 系统权限 TO 用户| 角色 PUBLIC [WITH | ADMIN  OPTION]`
          - 授权多个系统权限,则之间用,隔开
      - 权限回收
        - `REVOKE 系统权限 FROM 用户列表 | 角色列表 | PUBLIC`
        - 回收系统权限后传递不受影响
- week
  - 1
      - 对象权限
        - 对象权限的授予
          - `GRANT 对象权限列表 | ALL ON 对象 TO 用户列表 | 角色列表 [WITH GRANT OPTION]`
          - 范例
            ```
            GRANT SELECT, UPDATE, INSERT ON scott.emp TO user2 WITH GRANT OPTION;
            链接user2后...
            GRANT SELECT, UPDATE, INSERT ON scott.emp;-- 可以传递
            ```
        - 对象权限的回收
          - `REVOKE 对象权限列表 | ALL ON 对象 FROM 用户列表| 角色列表`
          - 回收对象权限后传递也受影响
      - 查询权限
        - DBA_TAB_PRIVS
        - ALL_TAB_PRIVS
        - USER_TAB_PRIVS
        - DBA_COL_PRIVS
        - ALL_COL_PRIVS
        - USER_COL_PRIVS
        - DBA_SYS_PRIVS
        - USER_SYS_PRIVS
      - 角色管理
        - 角色: 一系列相关权限的集合
        - 角色的分类
          - 系统预定义角色
          - 用户自定义角色
        1. 系统预定义角色
          - SELECT * FROM DBA_ROLES
        - 用户自定义角色
          1. 创建角色
            - `CREATE ROLE 角色名称 [NOT IDENTIFIED] [IDENTIFIED BY 密码] `
          - 角色权限的授予与回收
            - 与给用户授权类似
            - 给角色授权时需要注意:一个角色可以被授予给另外一个角色,但是不能授予其本身,不能产生循环授权
          - 修改角色
            - 让角色生效或失效
            - `ALTER ROLE 角色名 [NOT IDENTIFIED] [IDENTIFIED BY 密码]`
            - 注: 修改角色必须具有ALTER ANY ROLE系统权限,以及WITH ADMIN OPTION 权限。如果是角色的创建者,则自动具有针对该角色的修改权限
          - 角色的生效与失效
            -  `SET ROLE [角色名称[IDENTIFIED BY 密码]]|[ALL[EXCEPT 角色名称]]`
          - 删除角色
            - DROP ROLE 角色名称
          - 利用角色进行权限管理
            1. 给用户或角色授予角色
            GRANT 权限名, 角色名 TO 角色名
            - 从用户或角色回收角色
              - ROVEKE 角色列表 FROM 用户列表 | 角色列表
            - 用户角色的激活或屏蔽
              - ALTER USER 用户名 DEFAULT ROLE [角色名称] [ALL [EXCEPT 角色列表]]| [NONE]
          - 查询角色信息
          - DBA_TAB_PRIVS
          - ALL_TAB_PRIVS
          - USER_TAB_PRIVS
          - DBA_COL_PRIVS
          - ALL_COL_PRIVS
          - USER_COL_PRIVS
          - DBA_SYS_PRIVS
          - USER_SYS_PRIVS
          - SESSION_PRIVS
          - SESSION_ROLES
  - 概要文件
    - 概念
      - 是数据库和系统资源限制的集合。是oracle数据库安全策略的重要组成部分。利用概要文件,可以限制用户对数据库和系统资源的使用,同时还可以对用户口令进行管理
      - 每个数据库用户都必须有一个概要文件。通常dba将用户分为几个类型,然后每种类型的用户创建一个概要文件
      - 系统资源的限制
        - CPU使用时间
        - 每个用户的并发会话数
        - 用户连接数据库的时间
        - 用户连接数据库的空闲时间
        - 私有SQL区和PL/SQL区的使用
    1. 创建概念文件
      - CREATE PROFILE 概要文件名称 LIMIT 系统资源限制参数 | 口令管理参数
      - 范例
        ```
        -- 创建一个名为pwd_profile的概要文件,如果用户连接4次登陆失败,则该账号被锁定,10天后该账号自动解锁
        CREATE PROFILE pwd_profile LIMIT FAILED_LOGIN_ATTEMPTS 4 PASSWORD_LOCK_TIME 10;
        ```
        ```
        -- 创建一个名为res_profile的概要文件,要求每个用户最多可以创建4个并发会话,每个会话持续时间最长60分钟;如果会话在连续的20分钟内空闲,则结束会话。每个会话私有SQL区的大小为100kb,每个SQL语句占用CPU时间总量不超过10
        CREATE PROFILE res_profile LIMIT
        SESSION_PER_USER 4 CONNECT_TIME 60 IDLE_TIME 20 PRIVATE 100k CPU_PER_CALL 100;
        ```
      - 创建用户的时候指定概要文件
        - CREATE USER 用户名 IDENTIFIED BY 密码 PROFILE 概要文件名
      - 为用户指定概要文件
        - ALTER USER 用户名 PROFILE 概要文件名
      - 删除概要文件
        - DROP PROFILE 概要文件名称 CASCADE (级联关系,撤销为用户指定的)
- week
  - 1
    - 概要文件
      - 查询
        - USER_PASSWORD_LIMITS
        - USER_RESOURCE_LIMITS
        - DBA_PROFILES
- review
  - 考试题型
    1. 单选 40 * 1'
    - 阅读 12空 * 2' sql填空
    - 简答题 1 * 12'
      - 概念
    - 设计题 4 * 6'
      1. 表是否有问题
      - sql * 3
  - 注意事项
    - 写分号
  - 内容
    - 过程名称

# P.S.
  - 连接不上主机名 修改其中的host为本机名
    - tnnsames.ora
    - listener.ora
