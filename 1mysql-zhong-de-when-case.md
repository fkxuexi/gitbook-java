### 1、mysql中也存在中case when

#### 1.1 语法格式：

- 简单case函数：

```sql 
CASE sex 
  when '1' then '男'
  when '2' then '女'
  else '其他'
END   
```

- case 搜索函数：

```
CASE 
  when sex = 1 then '男'
  when sex = 2 then '女'
  else '其他'
END  
```

总的来说case 搜索功能要来的强大一些，因为when后面的对比的值可以为任意的字段，而简单case函数则只能是与之对比的只能是case后面跟的字段

```sql
select 
  case date_format(last_login,'%Y-%m-%d')
	when date_format(now(),'%Y-%m-%d') then 1
	else 0
  end 
from user where user_no = 444
```