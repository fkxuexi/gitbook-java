### 1、mysql中也存在中case when

```sql
select 
	case date_format(last_login,'%Y-%m-%d')
		when date_format(now(),'%Y-%m-%d') then 1
		else 0
	end 
from user where user_no = 444
```