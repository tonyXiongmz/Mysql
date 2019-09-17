Mysql通过sql语句获取某一字段最优值的整条记录
select max(score) score,id from rsult;这样的语句只会获取到最大值是准确的,其他数据不匹配
正确的应该是将查询出来的值作为查询条件
select id,course,score from result where score=(select max(score) score from result)

连接查询时获取最大值,要将两张表的关联字段作为where条件
select 
sd.uid,replace(json_extract(u.user_data,'$.nickname'),'\"','') nickName,replace(json_extract(c.company_data,'$.name'),'\"','') companyName,
ifnull(max(sd.score),0) target,ifnull(sd.fast_pace,0) fast_pace,ifnull(sd.in_target,0) in_target ,ifnull(sd.failure,0) failure ,
cd.department_name,sd.create_time,replace(json_extract(u.user_data,'$.gender'),'\"','') gender
from shooting as sd left join  user as u on sd.uid=u.id left join company c on c.id=u.companyId 
left join department d on u.id=d.uid and c.id=d.company_id left join company_department cd on cd.id=d.department_id
where sd.type=1 and sd.score=(select max(score) score from shooting where sd.uid=uid)  group by sd.uid order by target desc 


