# HTML

- 注释 `<!-- 注释 -->`
- 特殊符号
  - 空格 `&nbsp;`
  - 大于 `&gt;`
  - 小于 `&lt;`
  - 引号 `&quot;`
  - 版权号 `&copy`
- 常用表单元素 `<input name="" type="" size="显示宽度" maxlength="最大长度" value="初值">`
  - type:
    - 单行文本框 text
    - 文本域 textarea
      - `<textarea name="" cols="" rows=""></textarea>` (绝对)
    - 密码框 password
    - 单选按钮 radio 一组的name要相同
      - selected
    - 复选框 checkbox 一组的name不能相同
      - checked
    - 下拉列表 select
    - 提交按钮 submit
    - 重置按钮 reset
    - 按钮 button image
    - 文件 file
    - 隐藏域 hiddden
  - `disabled="disabled"`
- 语法
    - 表单语法
      - `<form action="" method=""></form>`
        - action: .jsp
        - method: `get`, `post`
      - `<option value="">text</option>`
    - 表格
      - table>tr>td
        - `<table border="边框宽度"></table>`
        - th 表头
        - caption 表格标题
        - td `colspan` 跨行
        - td `rospan` 跨列
- 框架
  - frameset (不能和body同时使用) frameset>frame+noframes
    ```
    <frameset cols="25%,50%,*" rows="50%,*" border="">
        <frame src="" scrolling="no" noresize="noresize"/>
        <!-- scrolling不显示滚动条, noresize不拉伸 -->
        <frame src="" target="rightframe"></frame>
    </frameset>
    ```
    - top.html
    - left.html
    - index.html
  - iframe
- css
  <head>
  <style type="text/css">
    选择器{
      color:blue;
    }
  </style>
  </head>
  - 选择器
    - 标签选择器 针对整个网页相同标签的更改样式
    - 类选择器 class
      - .class
    - id选择器
      - #id{}
      - `<div id="id"`
  - 偏移实现截图
