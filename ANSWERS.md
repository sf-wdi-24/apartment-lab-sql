# Apartment Lab (SQL Practice)

1. Show all the psql users. (**Hint:** Look for a command to show `roles`)
	
	\du shows all users...I am currently the only user 

	apartmentlab=# \du
	                             	List of roles
	 Role name |                   Attributes                   | Member of 
	-----------+------------------------------------------------+-----------
	 John      | Superuser, Create role, Create DB, Replication | {}



2. Show all the tables in your `apartmentlab` database.

	While in psql apartmentlabs db in terminal, type \dt and the table

3. Show all the data in the `owners` table.

	SELECT * FROM owners

4. Add three owners: Donald (age 56), Elaine (age 24), and Emma (age 36).
	
	apartmentlab=# INSERT INTO owners
	apartmentlab-# (name, age)
	apartmentlab-# VALUES
	apartmentlab-# ('Donald', 56), ('Elaine', 24), ('Emma', 36);
	INSERT 0 3
	apartmentlab=#

5. Show the names of all owners.

	apartmentlab=# SELECT name FROM owners
	apartmentlab-# ;
  		name  
	  --------
 	Donald
 	Elaine
 	Emma
	(3 rows)

	apartmentlab=# 

6. Show the ages of all of the owners in ascending order.

	apartmentlab=# SELECT * FROM owners
	apartmentlab-# ORDER BY age;
	 id |  name  | age 
	----+--------+-----
	  2 | Elaine |  24
	  3 | Emma   |  36
	  1 | Donald |  56
	(3 rows)

	apartmentlab=# 

7. Show the name of an owner whose name is Donald.
	
	apartmentlab=# SELECT * FROM owners                                                                                             WHERE name = 'Donald';
	 id |  name  | age 
	----+--------+-----
	  1 | Donald |  56
	(1 row)


8. Show the age of all owners who are older than 30.
	
	apartmentlab=# SELECT * FROM owners WHERE age > 30
	apartmentlab-# ;
	 id |  name  | age 
	----+--------+-----
	  1 | Donald |  56
	  3 | Emma   |  36
	(2 rows)

9. Show the name of all owners whose name starts with an "E".

	apartmentlab=# SELECT * FROM owners WHERE name LIKE '[E]%';
	 id | name | age 
	----+------+-----
	(0 rows)

	apartmentlab=# SELECT * FROM owners WHERE name LIKE 'E%';
	 id |  name  | age 
	----+--------+-----
	  2 | Elaine |  24
	  3 | Emma   |  36
	(2 rows)

	apartmentlab=# 
	

10. Add an owner named John who is 33 years old.

	apartmentlab=# INSERT INTO owners
	apartmentlab-# (name, age)
	apartmentlab-# VALUES
	apartmentlab-# ('John', 33), ('Jane', 43);
	INSERT 0 2
	apartmentlab=# 

11. Add an owner named Jane who is 43 years old.
		 (SEE QUESTION 10)

12. Change Jane's age to 30.
	
	apartmentlab=# UPDATE owners
	apartmentlab-# SET age = 30
	apartmentlab-# WHERE name = 'Jane';
	UPDATE 1
	apartmentlab=# 

13. Change Jane's name to Janet.
	
	apartmentlab=# UPDATE owners
	apartmentlab-# SET name = 'Janet'
	apartmentlab-# WHERE name = 'Jane';
	UPDATE 1
	apartmentlab=# 

14. Delete the owner named Janet.

	apartmentlab=# DELETE FROM owners WHERE name = 'Janet';
	DELETE 1

15. Add a property named Archstone that has 20 units.
	
	apartmentlab=# INSERT INTO properties
	apartmentlab-# (name, num_units)
	apartmentlab-# VALUES
	apartmentlab-# ('Archstone', 20)
	INSERT 0 1
	apartmentlab=#

16. Add two more properties with names and number of units of your choice.

	apartmentlab=# INSERT INTO properties
	apartmentlab-# (name, num_units)
	apartmentlab-# VALUES
	apartmentlab-# ('Cold Spring', 75), ('Longmeadow', 50);
	INSERT 0 2
	apartmentlab=#

17. Show all of the properties in alphabetical order that are not named Archstone.
	
	apartmentlab=# SELECT * FROM properties                                                     	WHERE name <> 'Archstone' ORDER BY name;
	 id |    name     | num_units | owner_id 
	----+-------------+-----------+----------
	  2 | Cold Spring |        75 |         
	  3 | Longmeadow  |        50 |         
	(2 rows)

	apartmentlab=#

18. Count the total number of rows in the properties table.

	apartmentlab=# SELECT COUNT(*) FROM properties;
 	count 
	-------
     3
	(1 row)

19. Show the highest age of all the owners.

	apartmentlab=# SELECT MAX(age) FROM owners;
 	max 
	-----
  	56
	(1 row)

20. Show the names of the first three owners in your owners table.

apartmentlab=# SELECT * FROM owners LIMIT 3;
 id |  name  | age 
----+--------+-----
  1 | Donald |  56
  2 | Elaine |  24
  3 | Emma   |  36
(3 rows)


21. Use a `FULL OUTER JOIN` to show all of the information from the owners table and the properties table.
22. Update at least one of your properties to belong to the owner with id 1.
23. Use an `INNER JOIN` to show all of the owners with associated properties.
24. Use a `CROSS JOIN` to show all possible combinations of owners and properties.

## Stretch Challenges

**Note:** You may need to research documentation for these challenges.

1. In the `properties` table, change the name of the column `name` to `property_name`.
2. Count the total number of properties where the `owner_id` is between 1 and 3.