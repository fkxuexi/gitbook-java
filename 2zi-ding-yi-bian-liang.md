
select (@rowNum:=@rowNum+1) as rowNum, user_extra.*  from user_extra ,(select (@rowNum:=0)) b order by user_extra.profit_ability desc;