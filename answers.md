1. \du

2. \dt

3. SELECT * FROM owners;

4. INSERT INTO owners
   (name, age)
   VALUES
   ('Donald', 56),
   ('Elaine', 24),
   ('Emma', 36);
5. SELECT name FROM owners;

6. SELECT age FROM owners ORDER BY age;

7. SELECT name from owners
   WHERE name = 'Donald';

8. SELECT name FROM owners
   WHERE age > 30;

9. SELECT name from onwers
   WHERE name LIKE 'E%';

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
    WHERE name = 'Jane';

13. UPDATE owners
    SET name = 'Janet'
    WHERE name = 'Jane';

14. DELETE FROM owners
    WHERE name = 'Janet';

15. INSERT INTO properties
    (name, num_units)
    VALUES
    ('Archstone', 20);

16. INSERT INTO properties
    (name, num_units)
    VALUES
    ('Brimcreek', 43),
    ('Salty Pool', 55);

17. SELECT name FROM properties
    WHERE name NOT LIKE 'Archstone%'
    ORDER BY name;

18. SELECT COUNT(name) FROM properties;

19. SELECT max(age) FROM owners;

20. SELECT name FROM owners LIMIT 3;

21. SELECT * FROM owners
    FULL OUTER JOIN properties
    ON owners.id = properties.id;

22. UPDATE properties
    SET owner_id = '1'
    WHERE name = 'Salty Pool';

23. SELECT * FROM owners
    INNER JOIN properties
    ON owners.id = properties.owner_id;

24. SELECT * FROM owners
    CROSS JOIN properties;

### Stretch
1. ALTER TABLE properties RENAME COLUMN name TO property_name;

2.























