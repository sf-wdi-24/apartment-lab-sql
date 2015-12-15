# Apartment Lab (SQL Practice)

1. Show all the psql users. (**Hint:** Look for a command to show `roles`)

2. Show all the tables in your `apartmentlab` database.

3. Show all the data in the `owners` table.
4. Add three owners: Donald (age 56), Elaine (age 24), and Emma (age 36).
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
15. Add a property named Archstone that has 20 units.
16. Add two more properties with names and number of units of your choice.
17. Show all of the properties in alphabetical order that are not named Archstone.
18. Count the total number of rows in the properties table.
19. Show the highest age of all the owners.
20. Show the names of the first three owners in your owners table.
21. Use a `FULL OUTER JOIN` to show all of the information from the owners table and the properties table.
22. Update at least one of your properties to belong to the owner with id 1.
23. Use an `INNER JOIN` to show all of the owners with associated properties.
24. Use a `CROSS JOIN` to show all possible combinations of owners and properties.

## Stretch Challenges

**Note:** You may need to research documentation for these challenges.

1. In the `properties` table, change the name of the column `name` to `property_name`.
2. Count the total number of properties where the `owner_id` is between 1 and 3.