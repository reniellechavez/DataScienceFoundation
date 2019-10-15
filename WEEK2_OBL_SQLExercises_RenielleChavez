--Which is the highest city that as an airport?
select city, altitude from airports
where altitude=( select  max(altitude) altitude from airports)
--And which is the lowest city that as an airport?
select city, altitude from airports
where altitude=( select  min(altitude) altitude from airports)
--Retrieve the timezones and generate a dataframe with the timezones 
--and the amount of airports in them. Plot it as a histogram as well.
select timezone, count(name) from airports
group by timezone
--Which country has more airlines? And which one has less?

select * from (
select b.* from (select  country , count(*) quantity from airlines
group by country)b
where b.quantity = (select max(a.quantity)--, min(a.quantity)
from (
select country , count(*) quantity from airlines
group by country)a)
union
select b.* from (select  country , count(*) quantity from airlines
group by country)b
where b.quantity = (select min(a.quantity)
from (select country , count(*) quantity from airlines
group by country)a))everything
order by everything.quantity desc

--Which city has the most outgoing destinations? And the least?

select air.city , tab.quantity from (
select a.source, a.quantity from (
select source, count(*)quantity from routes
group by source)a
where a.quantity=(select max(quantity) from
		(select source, count(*) quantity from routes
		group by source)
	)
union 
select a.source, a.quantity from (select source, count(*) quantity from routes
group by source )a
where a.quantity=
	(select min(quantity) from
		(select source, count(*) quantity from routes
		group by source))
	)tab join airports air on air.code= tab.source
	order by tab.quantity desc
	
	



--And which city has the most incoming destinations? And the least?



select air.city , tab.quantity from (
select a.dest, a.quantity from (
select dest, count(*)quantity from routes
group by dest)a
where a.quantity=(select max(quantity) from
		(select dest, count(*) quantity from routes
		group by dest)
	)
union 
select a.dest, a.quantity from (select dest, count(*) quantity from routes
group by dest )a
where a.quantity=
	(select min(quantity) from
		(select dest, count(*) quantity from routes
		group by dest))
	)tab join airports air on air.code= tab.dest
	order by tab.quantity desc
	