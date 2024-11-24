

```dataview
table file.size as 文件大小,rating as 评分,author as 作者, date
from "Charlie的数学笔记"
```


# 使用代码块的形式

1.  输入三个 ${```}$ 进入代码块格式
2. 代码输入 $dataview$,告诉ob使用dataview的语法
3. $list$ 以列表的形式输出
%%table状态下, $as$  +别名可以更改名字,且只能在table状态下才能这样使用
1. $file.size$ 输出文件的大小
2. $file.ctime$查询文件的创建时间
3. $file.name$查询文件名称
4. $file.path$查询文件路径
5. $file.cday$文件创建日期
6. $from$ +"文件名",可以导出当前文件夹下的文件

```dataview
table file.size as 文件大小, file.ctime as 创建时间, file.mday, file.cday,file.path,file.name
from "GPT的回答"
```

```dataview
list file.ctime
from #课堂笔记 
where rating>5
```


