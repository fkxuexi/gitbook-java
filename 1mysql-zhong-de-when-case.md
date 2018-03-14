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


```sql
select 
  case date_format(last_login,'%Y-%m-%d')
	when date_format(now(),'%Y-%m-%d') then 1
	else 0
  end 
from user where user_no = 444
```