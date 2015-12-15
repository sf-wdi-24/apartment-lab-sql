#ANSWERS
1.\du shows all users
2.\dt shows all tables
3.\d owners shows data in owners table
4.INSERT INTO owners (name, age)
  VALUES ('Donald', 56),
  VALUES ('Elaine', 24),
  VALues ('Emma', 36);
5. SELECT name FROM owners;
6. SELECT name, age FROM owners ORDER BY age;
     name  | age 
   --------+-----
    Elaine |  24
    Emma   |  36
    Donald |  56
7. SELECT * FROM owners
   WHERE name = 'Donald';
8. SELECT * FROM owners
	WHERE age > 30
	ORDER BY age; 
9. SELECT * FROM owners
	WHERE name LIKE 'E%'; --shows all names that start with 'E'
10. INSERT INTO owners
	(name, age)
	VALUES
	('John', 33);
11. INSERT INTO owners
	(name, age)
	VALUES
	('Jane', 43);
12. UPDATE owners
	SET age = 30
	WHERE name = 'Jane'
	RETURNING *;
13. UPDATE owners
	set name = 'Janet'
	where name = 'Jane';
14. DELETE FROM owners
	WHERE name = 'Janet'
	RETURNING *;
15. INSERT INTO properties (name, num_units)
	VALUES ('Archstone', 20);
16. INSERT INTO properties (name, num_units)
	VALUES ('Torrey Pines', 34),
			('Camino Del Rey', 97);
17. SELECT * FROM properties 
    WHERE name != 'Archstone'
    ORDER BY name
18. SELECT COUNT(*) FROM properties
19. SELECT name FROM owners
	WHERE age = (select max(age) from owners);
20. SELECT * FROM owners
	limit 3;
21. SELECT * FROM owners
	FULL OUTER JOIN properties
	ON owners.id = properties.owner_id;
22. UPDATE properties
	SET owner_id = 2
	WHERE name = 'Archstone';
23. SELECT * FROM owners
	INNER JOIN properties
	ON owners.id = properties.owner_id;
24. SELECT * FROM owners
CROSS JOIN PROPERTIES;