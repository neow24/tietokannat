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
select country.name as 'country name', airport.name as 'airport name' from airport inner join country on airport.iso_country = country.iso_country where country.name ='Iceland';
![alt text](image-17.png)

2
select name as 'airport name' from airport where iso_country = 'FR' and type = 'large_airport';
![alt text](image-18.png)

3
select country.name as 'country_name', airport.name as 'airport_name' from airport inner join country on country.iso_country = airport.iso_country where airport.continent = 'AN';
![alt text](image-19.png)

4
select airport.elevation_ft from airport inner join game on airport.ident = game.location where game.screen_name = 'Heini';
![alt text](image-20.png)

5
select airport.elevation_ft*0.3048 as 'elevation_m' from airport inner join game on airport.ident = game.location where game.screen_name = 'Heini';
![alt text](image-21.png)

6
select airport.name from airport inner join game on airport.ident = game.location where game.screen_name = 'Ilkka';
![alt text](image-22.png)

7
select country.name from airport inner join game on airport.ident = game.location inner join country on airport.iso_country = country.iso_country where game.screen_name = 'Ilkka';
![alt text](image-23.png)

8
select goal.name from goal inner join goal_reached on goal.id = goal_reached.goal_id inner join game on goal_reached.game_id = game.id where game.screen_name = 'Heini';
![alt text](image-24.png)

9
select airport.name from goal inner join goal_reached on goal.id = goal_reached.goal_id inner join game on goal_reached.game_id = game.id inner join airport on game.location = airport.ident where goal.name = 'clouds' and game.screen_name = 'Ilkka';
![alt text](image-25.png)

10
select country.name from goal inner join goal_reached on goal.id = goal_reached.goal_id inner join game on goal_reached.game_id = game.id inner join airport on game.location = airport.ident inner join country on airport.iso_country = country.iso_country where goal.name = 'clouds' and game.screen_name = 'Ilkka';
![alt text](image-26.png)

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

Sisäkysely harjoitukset

1
select country.name from country inner join airport on country.iso_country = airport.iso_country where airport.name like 'Satsuma%';
![alt text](image-27.png)

2
select name from airport where iso_country = 'MC';
![alt text](image-28.png)

3
select game.screen_name from game inner join goal_reached on game.id = goal_reached.game_id inner join goal on goal_reached.goal_id = goal.id where name = 'clouds';
![alt text](image-29.png)

4
select country.name from country where country.iso_country not in (select airport.iso_country from airport);
![alt text](image-30.png)

5
select goal.name from goal where goal.id not in (select goal_reached.goal_id from goal_reached inner join game on goal_reached.game_id = game.id where game.screen_name = 'Heini');
![alt text](image-31.png)

Koostetieto kyselyt harjoitukset

1
select max(elevation_ft) from airport;
![alt text](image-32.png)

2
select continent, count(*) from country group by continent;
![alt text](image-33.png)

3
select screen_name, count(*) from goal_reached inner join game on goal_reached.game_id = game.id group by screen_name;
![alt text](image-34.png)

4
select screen_name from game order by co2_consumed limit 1;
![alt text](image-35.png)

5
select country.name, count(*) from country inner join airport on country.iso_country = airport.iso_country group by country.name order by count(*) desc limit 50;
![alt text](image-36.png)

6
select country.name from country inner join airport on country.iso_country = airport.iso_country group by country.iso_country having count(*) >= 1000;
![alt text](image-37.png)

7
select name from airport where elevation_ft in (select max(elevation_ft) from airport);
![alt text](image-38.png)

8
select country.name from country inner join airport on country.iso_country = airport.iso_country where elevation_ft in (select max(elevation_ft) from airport);
![alt text](image-39.png)

9
select count(*) from goal inner join goal_reached on goal.id = goal_reached.goal_id inner join game on goal_reached.game_id = game.id where screen_name = 'Vesa';
![alt text](image-40.png)

10
select name from airport order by latitude_deg limit 1;
![alt text](image-41.png)

