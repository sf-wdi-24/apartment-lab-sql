1. Show all the psql users. (Hint: Look for a command to show roles)

apartmentlab=# \du
                             List of roles
 Role name |                   Attributes                   | Member of 
-----------+------------------------------------------------+-----------
 davesloan | Superuser, Create role, Create DB, Replication | {}


2. Show all the tables in your apartmentlab database.

apartmentlab=# \dt
            List of relations
 Schema |    Name    | Type  |   Owner   
--------+------------+-------+-----------
 public | owners     | table | davesloan
 public | properties | table | davesloan
(2 rows)


3. Show all the data in the owners table.

apartmentlab=# SELECT * FROM owners;
 id | name | age 
----+------+-----
(0 rows)


4. Add three owners: Donald (age 56), Elaine (age 24), and Emma (age 36).

apartmentlab=# INSERT INTO owners (name, age)
apartmentlab-# VALUES ('Donald', 56);
INSERT 0 1
apartmentlab=# INSERT INTO owners (name, age)
apartmentlab-# VALUES ('Elaine', 24);
INSERT 0 1
apartmentlab=# INSERT INTO owners (name, age)
apartmentlab-# Values ('Emma', 36);
INSERT 0 1

5. Show the names of all owners.

apartmentlab=# SELECT * FROM owners;
 id |  name  | age 
----+--------+-----
  1 | Donald |  56
  2 | Donald |  56
  3 | Elaine |  24
  4 | Emma   |  36
(4 rows)

Deleting one of the Donalds. 

apartmentlab=# DELETE FROM owners
apartmentlab-# WHERE id = 1
apartmentlab-# RETURNING *;
 id |  name  | age 
----+--------+-----
  1 | Donald |  56
(1 row)

DELETE 1

apartmentlab=# SELECT * FROM owners;
 id |  name  | age 
----+--------+-----
  2 | Donald |  56
  3 | Elaine |  24
  4 | Emma   |  36
(3 rows)

6. Show the ages of all of the owners in ascending order.

apartmentlab=# SELECT * FROM owners ORDER BY age;
 id |  name  | age 
----+--------+-----
  3 | Elaine |  24
  4 | Emma   |  36
  2 | Donald |  56
(3 rows)

7. Show the name of an owner whose name is Donald.

apartmentlab=# SELECT * FROM owners WHERE name  = 'Donald';
 id |  name  | age 
----+--------+-----
  2 | Donald |  56
(1 row)


8. Show the age of all owners who are older than 30.

apartmentlab=# SELECT * FROM owners WHERE age > 30;
 id |  name  | age 
----+--------+-----
  2 | Donald |  56
  4 | Emma   |  36
(2 rows)

9. Show the name of all owners whose name starts with an "E".


apartmentlab=# SELECT * FROM owners WHERE name LIKE 'E%';
 id |  name  | age 
----+--------+-----
  3 | Elaine |  24
  4 | Emma   |  36
(2 rows)


10. Add an owner named John who is 33 years old.

apartmentlab=# INSERT INTO owners (name, age)
apartmentlab-# VALUES ('John', 33);
INSERT 0 1

11. Add an owner named Jane who is 43 years old.

apartmentlab=# INSERT INTO owners (name, age)
apartmentlab-# VALUES ('Jane', 43);

12. Change Jane's age to 30.

apartmentlab=# UPDATE owners
apartmentlab-# SET age = 30
apartmentlab-# WHERE name = 'Jane'
apartmentlab-# RETURNING *;
 id | name | age 
----+------+-----
  6 | Jane |  30
(1 row)

13. Change Jane's name to Janet.

apartmentlab=# UPDATE owners
apartmentlab-# SET name = 'Janet'
apartmentlab-# WHERE name = 'Jane'
apartmentlab-# RETURNING *;
 id | name  | age 
----+-------+-----
  6 | Janet |  30

14. Delete the owner named Janet.

apartmentlab=# DELETE FROM owners
apartmentlab-# WHERE name = 'Janet'
apartmentlab-# RETURNING *;
 id | name  | age 
----+-------+-----
  6 | Janet |  30
(1 row)

DELETE 1

15. Add a property named Archstone that has 20 units.

apartmentlab=# INSERT INTO properties (name, num_units)
apartmentlab-# VALUES ('Archstone', 20);
INSERT 0 1

16. Add two more properties with names and number of units of your choice.

apartmentlab=# INSERT INTO properties (name, num_units)                         VALUES ('Sharon_Oaks', 25);
INSERT 0 1
apartmentlab=# INSERT INTO properties (name, num_units)                         VALUES ('Whiteoak_Townhouses', 35);
INSERT 0 1

17. Show all of the properties in alphabetical order that are not named Archstone.

apartmentlab=# SELECT ALL * FROM properties WHERE name <> 'Archstone';
 id |        name         | num_units | owner_id 
----+---------------------+-----------+----------
  2 | Sharon_Oaks         |        25 |         
  3 | Whiteoak_Townhouses |        35 |         
(2 rows)

18. Count the total number of rows in the properties table.

apartmentlab=# select count(*) from properties;
 count 
-------
     3

19. Show the highest age of all the owners.

apartmentlab=# SELECT MAX(age) FROM owners;
 max 
-----
  56

20. Show the names of the first three owners in your owners table.

apartmentlab=# select * from owners limit 3;
 id |  name  | age 
----+--------+-----
  2 | Donald |  56
  3 | Elaine |  24
  4 | Emma   |  36

21. Use a FULL OUTER JOIN to show all of the information from the owners table and the properties table.

apartmentlab-# on owners.id = properties.id;
 id |  name  | age | id |        name         | num_units | owner_id 
----+--------+-----+----+---------------------+-----------+----------
  2 | Donald |  56 |  2 | Sharon_Oaks         |        25 |         
  3 | Elaine |  24 |  3 | Whiteoak_Townhouses |        35 |         
  4 | Emma   |  36 |    |                     |           |         
  5 | John   |  33 |    |                     |           |         
    |        |     |  1 | Archstone           |        20 |         


22. Update at least one of your properties to belong to the owner with id 2.

apartmentlab=# UPDATE properties SET owner_id = 2 WHERE name = 'Sharon_Oaks';

apartmentlab=# select * from properties;
 id |        name         | num_units | owner_id 
----+---------------------+-----------+----------
  1 | Archstone           |        20 |         
  3 | Whiteoak_Townhouses |        35 |         
  2 | Sharon_Oaks         |        36 |        2

23. Use an INNER JOIN to show all of the owners with associated properties.

apartmentlab-# on owners.id = properties.owner_id;
 id |  name  | age | id |    name     | num_units | owner_id 
----+--------+-----+----+-------------+-----------+----------
  2 | Donald |  56 |  2 | Sharon_Oaks |        36 |        2


24. Use a CROSS JOIN to show all possible combinations of owners and properties.
        ^
apartmentlab=# select * from properties cross join owners;
 id |        name         | num_units | owner_id | id |  name  | age 
----+---------------------+-----------+----------+----+--------+-----
  1 | Archstone           |        20 |          |  2 | Donald |  56
  1 | Archstone           |        20 |          |  3 | Elaine |  24
  1 | Archstone           |        20 |          |  4 | Emma   |  36
  1 | Archstone           |        20 |          |  5 | John   |  33
  3 | Whiteoak_Townhouses |        35 |          |  2 | Donald |  56
  3 | Whiteoak_Townhouses |        35 |          |  3 | Elaine |  24
  3 | Whiteoak_Townhouses |        35 |          |  4 | Emma   |  36
  3 | Whiteoak_Townhouses |        35 |          |  5 | John   |  33
  2 | Sharon_Oaks         |        36 |        2 |  2 | Donald |  56
  2 | Sharon_Oaks         |        36 |        2 |  3 | Elaine |  24
  2 | Sharon_Oaks         |        36 |        2 |  4 | Emma   |  36
  2 | Sharon_Oaks         |        36 |        2 |  5 | John   |  33
(12 rows)




