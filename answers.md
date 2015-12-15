1.\du all users 
2.\du all tables
3.select id * from owners
4. insert into owners(name,age)
 values ('Donald',56),
 ('Elaine',24),
 ('Emma',36);
5.select name from owners
6.select age FROM owners  ORDER BY age
7.select name FROM owners WHERE name = 'Donald'
8.select name FROM owners WHERE age>30
9.select * FROM owners WHERE name LIKE 'E%'
10.insert into owners (name, age) VALUES ('John', 33)
11.insert into owners (name, age) VALUES ('Jane', 43)
12.
13.update owners SET name = 'Janet' WHERE name = 'Jane
14.apartmentlab=# DELETE FROM owners WHERE name = 'Janet'
15.insert into properties (name, num_unit) VALUES ('Archstone', 20)
16.insert into properties (name, num_unit) VALUES ('Zohar', 2000), ('Ido', 2000)
17.select * FROM properties WHERE name <> 'Archstone' ORDER BY name
18.select count(*) FROM properties
19.select max(age) FROM owners
20.select * FROM owners LIMIT 3
21.select * FROM owners 
	FULL OUTER JOIN properties 
	ON owners.id = properties.owner_id
22.update properties set owner_id=1 where id=4
23.select * from owners
	INNER JOIN properties 
	ON owners.id = properties.owner_id
24.select * from owners  
	CROSS JOIN properties                                                                                                      
	WHERE owners.id=1
