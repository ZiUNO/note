# database
1. 
-
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
