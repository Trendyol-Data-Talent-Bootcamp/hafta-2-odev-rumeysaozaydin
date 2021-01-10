# Soru 1) 1980’den itibaren spor grubu bazında en çok madalya alan 1. 3. 5. ülkeyi bulalım.

```SQL
select * 
from(
select distinct sport,
first_value(country) over (partition by sport order by cnt DESC) as rank1,
nth_value(country,3) over (partition by sport order by cnt DESC) as rank3,
nth_value(country,5) over (partition by sport order by cnt DESC) as rank5,
from(
select sport,country,COUNT(1) as cnt from rumeysa_ozaydin.summer_medals
where (year>1980)
group by sport,country
order by sport,count(1) DESC)
)
where rank1 is not null and rank3 is not null and rank5 is not null
```
