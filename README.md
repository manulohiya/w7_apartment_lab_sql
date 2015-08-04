# Apartment Lab (SQL Practice)

For these challenges, you'll be working with two tables, `owners` and `properties`. Keep this relationship in mind when designing your schema: **one owner can have many properties**.

## Getting Started

1. Create a database called `apartmentlab`.
2. Using the `apartmentlab` database, create two tables, one for `owners` and one for `properties`. See the next section for schema specs.

## Schema

* The `owners` table should consist of:
	* **id** (this should be the primary key as well as a unique number that increments automatically)
	* **name**
	* **age**

* The `properties` table should consist of:
	* **id** (this should be the primary key as well as a unique number that increments automatically)
	* **name**
	* **num_units**
	* **owner_id** (this should be a foreign key that references the owners table)

## Challenges

In a <a href="https://help.github.com/articles/markdown-basics" target="_blank">markdown</a> file, write the SQL statements required to solve the following tasks. Make sure to test your queries in the `psql` terminal! Remember you can type `\?` in the `psql` terminal for a list of commands.

1. Show all the psql users. (**Hint:** Look for a command to show `roles`)
2. Show all the tables in your `apartmentlab` database.

\dt

3. Show all the data in the `owners` table.

select * from owners

4. Add three owners: Donald (age 56), Elaine (age 24), and Emma (age 36).

insert into owners (name, age)
values ('elaine', 24);

5. Show the names of all owners.
6. Show the ages of all of the owners in ascending order.
7. Show the name of an owner whose name is Donald.
8. Show the age of all owners who are older than 30.
9. Show the name of all owners whose name starts with an "E".
10. Add an owner named John who is 33 years old.
11. Add an owner named Jane who is 43 years old.
12. Change Jane's age to 30.
13. Change Jane's name to Janet.
14. Delete the owner named Janet.

delete from owners where name = 'jane'

15. Add a property named Archstone that has 20 units.

insert into properties (name, num_units) values('archstone', 20);

16. Add two more properties with names and number of units of your choice.


17. Show all of the properties in alphabetical order that are not named Archstone.

select * from properties where name <> 'archstone' order by name DESC;


18. Count the total number of rows in the properties table.

select count(name) as property_count from properties;


19. Show the highest age of all the owners.

apartmentlab=# select name, max(age) as oldest_owner 
from owners
group by name
order by oldest_owner desc
;

20. Show the names of the first three owners in your owners table.

select * from owners where id < 4;

21. Use a `FULL OUTER JOIN` to show all of the information from the owners table and the properties table.

select * from owners
full outer join properties
on owners.id = properties.owner_id;

22. Update at least one of your properties to belong to the owner with id 1.

UPDATE properties 
set owner_id = 1
where name = "archstone"
;


23. Use an `INNER JOIN` to show all of the owners with associated properties.

SELECT * FROM owners
inner join properties
on owners.id = properties.owner_id;


24. Use a `CROSS JOIN` to show all possible combinations of owners and properties.

SELECT * FROM owners
apartmentlab-# cross join properties;


## Stretch Challenges

**Note:** You may need to research documentation for these challenges.

1. In the `properties` table, change the name of the column `name` to `property_name`.



2. Count the total number of properties where the `owner_id` is between 1 and 3.
