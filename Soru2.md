# Soru 2) 1980’den itibaren herhangi bir spor grubunda üst üste 3 veya daha fazla madalya almış atletleri bulalım.

```SQL
select distinct a.Athlete 
from rumeysa_ozaydin.summer_medals a inner join rumeysa_ozaydin.summer_medals b 
on b.Athlete = a.Athlete
inner join
rumeysa_ozaydin.summer_medals c
on c.Athlete = b.Athlete
where a.year >= 1980 and b.year = a.year + 4 and c.year = b.year + 4
order by a.athlete
```
