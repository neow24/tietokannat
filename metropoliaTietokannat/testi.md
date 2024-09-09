Yhteen tauluun kohdistuvien kyselyiden harjoitukset

1
select * from goal;
![alt text](image-3.png)

2
SELECT name, type FROM airport WHERE iso_country = 'FI';
![alt text](image-4.png)

3
SELECT name from airport where iso_country = 'FI' order by name asc;
![alt text](image-5.png)

4
select name, type from airport where iso_country = 'FI' order by type, name;
![alt text](image-6.png)

5
select name from country where name like 'F%';
![alt text](image-7.png)

6
select name from country where name like '%F%';
![alt text](image-8.png)

7
select location from game where screen_name = 'Vesa';
![alt text](image-9.png)

8
select co2_consumed from game where screen_name = 'Ilkka';
![alt text](image-10.png)

9
select co2_budget from game where id = '1';
![alt text](image-11.png)

Where-osan liitosehto harjoitukset

1


Join harjoitukset

1
select country.name, airport.name from airport inner join country on airport.iso_country = country.iso_country where country.name = 'Finland' and airport.scheduled_service = 'yes';
![alt text](image-12.png)

2
select game.screen_name, airport.name from airport inner join game on airport.ident = game.location;
![alt text](image-13.png)

3
select game.screen_name, country.name from (country inner join airport on airport.iso_country = country.iso_country) inner join game on game.location = airport.ident;
![alt text](image-14.png)

4
select airport.name, game.screen_name from airport left outer join game on airport.ident = game.location where airport.name like '%Hels%';
![alt text](image-15.png)

5
select goal.name, game.screen_name from goal left outer join goal_reached ON goal_reached.goal_id = goal.id left outer join game on goal_reached.game_id = game.id;
![alt text](image-16.png)

