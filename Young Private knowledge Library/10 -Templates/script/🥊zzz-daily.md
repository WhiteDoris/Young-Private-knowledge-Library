```js
<%*
// 按照年-月-日的格式，得到今天日期的变量（例如2023-03-07）
let today = tp.date.now("YYYY-MM-DD")
// 获取输入到inputDate
let inputDate = await tp.system.prompt("输入示例："+today,today)
// 格式化变量titleName成年-月-日_周几
titleName = window.moment(inputDate, "YYYY-MM-DD", true).format("YYYY-MM-DD_ddd")
// 获取昨天的日期（文件名以日期命名）
before_date = window.moment(inputDate, "YYYY-MM-DD", true).add(-1,"days").format("YYYY-MM-DD_ddd")
// 获取明天的日期（文件名以日期命名）
after_date = window.moment(inputDate, "YYYY-MM-DD", true).add(1,"days").format("YYYY-MM-DD_ddd")
// 获取当前文件创建时间
let createTime = tp.file.creation_date("YYYY-MM-DD HH:mm")
// 获取当前文件修改时间
let modificationDate = tp.file.last_modified_date("dddd Do MMMM YYYY HH:mm:ss")
-%>
// 上述内容，运行后不会显示，下面的内容会显示，且变量值来自于上述代码
---
create time : <% createTime %>
modification date: <% modificationDate %>
---

<< [[<% before_date %>]] | [[<% after_date %>]] >>
```

```js
Date now: <% tp.date.now() %>
Date now with format: <% tp.date.now("Do MMMM YYYY") %>

Last week: <% tp.date.now("dddd Do MMMM YYYY", -7) %>
Today: <% tp.date.now("dddd Do MMMM YYYY, ddd") %>
Next week: <% tp.date.now("dddd Do MMMM YYYY", 7) %>

Last month: <% tp.date.now("YYYY-MM-DD", "P-1M") %>
Next year: <% tp.date.now("YYYY-MM-DD", "P1Y") %>

File's title date + 1 day (tomorrow): <% tp.date.now("YYYY-MM-DD", 1, tp.file.title, "YYYY-MM-DD") %>
File's title date - 1 day (yesterday): <% tp.date.now("YYYY-MM-DD", -1, tp.file.title, "YYYY-MM-DD") %>

Date tomorrow with format: <% tp.date.tomorrow("Do MMMM YYYY") %>    

This week's monday: <% tp.date.weekday("YYYY-MM-DD", 0) %>
Next monday: <% tp.date.weekday("YYYY-MM-DD", 7) %>
File's title monday: <% tp.date.weekday("YYYY-MM-DD", 0, tp.file.title, "YYYY-MM-DD") %>
File's title next monday: <% tp.date.weekday("YYYY-MM-DD", 7, tp.file.title, "YYYY-MM-DD") %>

Date yesterday with format: <% tp.date.yesterday("Do MMMM YYYY") %>

```