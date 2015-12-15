1. SELECT rolname FROM pg_roles;
2. \connect apartmentlab
   \dt
3. TABLE owners;
4. INSERT INTO owners (name, age) VALUES ('Donald', 56), ('Elaine', 24), ('Emma', 36)
5. SELECT name FROM owners;
6. SELECT age FROM owners ORDER BY age;
7. SELECT * FROM owners WHERE name = 'Donald';
8. SELECT name FROM owners WHERE age > 30;
9. SELECT name FROM owners WHERE name ~ 'E';
10+11. INSERT INTO owners (name, age) VALUES ('John', 33), ('Jane', 43);
12. UPDATE owners SET age = 30 WHERE name = 'Jane';
13. UPDATE owners SET name = 'Janet' WHERE name = 'Jane';
14. DELETE FROM owners WHERE name = 'Janet';
15. INSERT INTO properties (name, num_units, owner_id) VALUES ('Archstone', 20, null);
16. INSERT INTO properties (name, num_units) VALUES ('Ford', 15), ('Vernor Estates', 25);
17. SELECT * FROM properties WHERE name != 'Archstone' ORDER BY name;
18. SELECT COUNT(*) FROM properties;
19. SELECT MAX(age) FROM owners;
20. SELECT name FROM owners LIMIT (3);
21. SELECT * FROM owners FULL OUTER JOIN properties ON owners.id = properties.owner_id;
22. SELECT * FROM owners INNER JOIN properties ON owners.id = properties.owner_id;
23. SELECT * FROM owners CROSS JOIN properties;