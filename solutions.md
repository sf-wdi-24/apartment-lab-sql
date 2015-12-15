#Challenges
1. ` \du `
2. ` \dt `
3. ` SELECT * FROM owners; `
4. ` INSERT INTO owners (name, age) VALUES ('Donald', 56), ('Elaine', 24),('Emma', 36); `
5. ` SELECT NAME FROM owners; `
6. ` SELECT age FROM owners ORDER BY age ASC; `
7. ` SELECT name FROM owners WHERE name = 'Donald'; `
8. ` SELECT age FROM owners WHERE age > 30; `
9. ` SELECT name FROM owners WHERE name LIKE ('E%'); `
10. ` INSERT INTO owners (name, age) VALUES ('John', 33); `
11. ` INSERT INTO owners (name, age) VALUES ('Jane', 43); `
12. ` UPDATE owners SET (age) = (30) WHERE name = 'Jane'; `
13. ` UPDATE owners SET (name) = ('Janet') WHERE name = 'Jane'; `
14. ` DELETE FROM owners WHERE name = 'Janet'; `
15. ` INSERT INTO properties (name, num_units) VALUES ('Archstone', 20); `
16. ` INSERT INTO properties (name, num_units) VALUES ('Train Station Apts', 40), ('Nord Gardens', 100); `
17. ` SELECT * FROM properties WHERE name <> 'Archstone' ORDER BY name ASC; `
18. ` SELECT COUNT(id) FROM properties; `
19. ` SELECT MAX(age) AS Oldest_Owner FROM owners; `
20. ` SELECT name FROM owners LIMIT 3; `
21. ` SELECT * FROM owners FULL OUTER JOIN properties ON owners.id = properties.id; `
22. ` UPDATE properties SET owner_id = 1 WHERE name = 'Nord Gardens'; `
23. ` SELECT * FROM owners INNER JOIN properties ON owners.id = properties.owner_id; `
24. ` SELECT * FROM owners CROSS JOIN properties; `

##Stretch Challenges
1. ` ALTER TABLE properties RENAME COLUMN name TO property_name; `
2. ` SELECT COUNT(id) FROM PROPERTIES WHERE owner_id BETWEEN 1 AND 3; `
