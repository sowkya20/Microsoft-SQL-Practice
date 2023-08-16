# Microsoft-SQL-Practice

GO
use Ankit_Bansal_YTB
Go 
select Team_name, count(1) as no_of_records,sum(winf_flag) as no_of_matches_played, count(1) - sum(winf_flag) as no_of_looses
,sum(Draw_flag) as no_of_Drwas
from(
Select [Team_1] as Team_name, 
Case when [Team_1] = Winner then 1 else 0 end as winf_flag,
Case when Winner = 'Draw' then 1 else 0 end as Draw_flag
from  [dbo].[icc_world_cup]
union all 
Select [Team_2] as Team_name, Case when [Team_2] = Winner then 1 else 0 end as winf_flag,
Case when Winner = 'Draw' then 1 else 0 end as Draw_flag from  [dbo].[icc_world_cup])A
group by Team_name order by no_of_matches_played DESC
go
