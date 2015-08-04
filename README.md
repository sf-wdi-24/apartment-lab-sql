# Apartment Lab (SQL Practice)

For these challenges, you'll be working with two tables, `owners` and `properties`. Keep this relationship in mind when designing your schema: **one owner can have many properties**.

## Getting Started

1. Create a database called `apartmentlab`.

	```sql
	CREATE DATABASE apartmentlab;
	```

2. Using the `apartmentlab` database, create two tables, one for `owners` and one for `properties`. See the next section for schema specs.

	```sql
	CREATE TABLE owners (
	  id SERIAL PRIMARY KEY,
	  name VARCHAR(255),
	  age INTEGER
	);

	CREATE TABLE properties (
	  id SERIAL PRIMARY KEY,
	  name VARCHAR(255),
	  num_units INTEGER,
		owner_id INTEGER REFERENCES owners
	);
	```

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

	```sql
	\dg

	# OR

	\du
	```

2. Show all the tables in your `apartmentlab` database.

	```sql
	\dt
	```

3. Show all the data in the `owners` table.

	```sql
	SELECT * FROM owners;
	```

4. Add three owners: Donald (age 56), Elaine (age 24), and Emma (age 36).

	```sql
	INSERT INTO owners (name, age)
  	VALUES ('Donald', 56);

	INSERT INTO owners (name, age)
  	VALUES ('Elaine', 24);

	INSERT INTO owners (name, age)
  	VALUES ('Emma', 36);
	```

5. Show the names of all owners.

	```sql
	SELECT name FROM owners;
	```

6. Show the ages of all of the owners in ascending order.

	```sql
	SELECT age FROM owners ORDER BY age ASC;
	```

7. Show the name of an owner whose name is Donald.

	```sql
	SELECT * FROM owners WHERE name = 'Donald';
	```

8. Show the age of all owners who are older than 30.

	```sql
	SELECT * FROM owners WHERE age > 30;
	```

9. Show the name of all owners whose name starts with an "E".

	```sql
	SELECT * FROM owners WHERE name LIKE 'E%';
	```

10. Add an owner named John who is 33 years old.

	```sql
	INSERT INTO owners (name, age)
  	VALUES ('John', 33);
	```

11. Add an owner named Jane who is 43 years old.

	```sql
	INSERT INTO owners (name, age)
  	VALUES ('Jane', 43);
	```

12. Change Jane's age to 30.

	```sql
	UPDATE owners SET age = 30 WHERE name = 'Jane';
	```

13. Change Jane's name to Janet.

	```sql
	UPDATE owners SET name ='Janet' WHERE name = 'Jane';
	```

14. Delete the owner named Janet.

	```sql
	DELETE FROM owners WHERE name = 'Janet';
	```

15. Add a property named Archstone that has 20 units.

	```sql
	INSERT INTO properties (name, num_units)
		VALUES ('Archstone', 20);
	```

16. Add two more properties with names and number of units of your choice.

	```sql
	INSERT INTO properties (name, num_units)
		VALUES ('Terraces', 50);

	INSERT INTO properties (name, num_units)
		VALUES ('Wynn', 300);
	```

17. Show all of the properties in alphabetical order that are not named Archstone.

	```sql
	SELECT * FROM properties WHERE name <> 'Archstone' ORDER BY name ASC;
	```

18. Count the total number of rows in the properties table.

	```sql
	SELECT COUNT (*) FROM properties;
	```

19. Show the highest age of all the owners.

	```sql
	SELECT MAX(age) FROM owners;
	```

20. Show the names of the first three owners in your owners table.

	```sql
	SELECT * FROM owners LIMIT 3;
	```

21. Use a `FULL OUTER JOIN` to show all of the information from the owners table and the properties table.

	```sql
	SELECT * FROM owners
	FULL OUTER JOIN properties
	ON owners.id = properties.owner_id;
	```

22. Update at least one of your properties to belong to the owner with id 1.

	```sql
	UPDATE properties SET owner_id = 1 WHERE id = 1;
	```

23. Use an `INNER JOIN` to show all of the owners with associated properties.

	```sql
	SELECT * FROM owners
	INNER JOIN properties
	ON owners.id = properties.owner_id;
	```

24. Use a `CROSS JOIN` to show all possible combinations of owners and properties.

	```sql
	SELECT * FROM owners
	CROSS JOIN properties;
	```

## Stretch Challenges

**Note:** You may need to research documentation for these challenges.

1. In the `properties` table, change the name of the column `name` to `property_name`.

	```sql
	ALTER TABLE properties RENAME COLUMN name TO property_name;
	```

2. Count the total number of properties where the `owner_id` is between 1 and 3.

	```sql
	SELECT COUNT(*) FROM properties WHERE owner_id BETWEEN 1 AND 3;
	```
