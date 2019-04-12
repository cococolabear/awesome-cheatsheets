### 查询上一条记录

```mysql
select if(@mobile=t.mobile,@lagcj:=@p_name,@lagcj:='') as before_p_name
       ,@mobile:=t.mobile as tmobile
       ,@p_name:=t.p_name as p_name
       ,t.*
  from (select * from dc_tmp.temp_aa order by id) t ,(select @lagcj:=null,@mobile:=0,@p_name:=null) r;
```
