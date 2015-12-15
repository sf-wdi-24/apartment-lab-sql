1.  \du
2.  \dt
3.  SELECT * FROM owners;
4. 	INSERT INTO owners (name, age) VALUES ('Donald', 56);
	INSERT INTO owners (name, age) VALUES ('Elaine',24);
	INSERT INTO owners (name, age) VALUES ('Emma',36);
5.  SELECT name FROM owners;
6.  SELECT age FROM owners  ORDER BY age;
7.  SELECT name FROM owners WHERE name = 'Donald';
8.  SELECT name FROM owners WHERE age>30;
9.  SELECT * FROM owners WHERE name LIKE 'E%';
10. INSERT INTO owners (name, age) VALUES ('John', 33);
11. INSERT INTO owners (name, age) VALUES ('Jane', 43);
12. UPDATE owners SET age = 30 WHERE age = 40; (how I update specific age of a person?)
13. UPDATE owners SET name = 'Janet' WHERE name = 'Jane';
14. apartmentlab=# DELETE FROM owners WHERE name = 'Janet';
15. INSERT INTO properties (name, num_unit) VALUES ('Archstone', 20);
16. INSERT INTO properties (name, num_unit) VALUES ('Zohar', 2000), ('Ido', 2000);
17. SELECT * FROM properties WHERE name <> 'Archstone' ORDER BY name;      
18. SELECT count(*) FROM properties;
19. SELECT max(age) FROM owners;
20. SELECT * FROM owners LIMIT 3;
21. SELECT * FROM owners 
	FULL OUTER JOIN properties 
	ON owners.id = properties.owner_id;   
22. UPDATE properties SET owner_id=1 WHERE id=4;
23. SELECT * FROM owners
	INNER JOIN properties 
	ON owners.id = properties.owner_id; 
24. SELECT * FROM owners  
	CROSS JOIN properties                                                                                                  
	WHERE owners.id=1;     

Stretch Challenges

1. ALTER TABLE properties RENAME COLUMN name TO property_name; 
2. SELECT * FROM owners WHERE id BETWEEN 1 AND 3;                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    
