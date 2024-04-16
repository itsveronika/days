# Task 00
```sql
SELECT m.pizza_name, m.price, pi.name AS pizzeria_name, visit_date
FROM person_visits pv
JOIN person p ON pv.person_id = p.id
JOIN pizzeria pi ON pi.id = pv.pizzeria_id
JOIN menu m ON pv.pizzeria_id = m.pizzeria_id
WHERE p.name = 'Kate' AND m.price BETWEEN 800 AND 1000
ORDER BY pizza_name, price, pizzeria_name;
```
![image](https://github.com/itsveronika/days/assets/113369081/f065d1eb-f551-47fd-83a9-9414cb7ea2ee)

# Task 01
```sql
SELECT m.id
FROM menu m
LEFT JOIN person_order po ON po.menu_id = m.id
WHERE po.menu_id IS NULL
ORDER BY id;
```
![image](https://github.com/itsveronika/days/assets/113369081/889750bb-da84-486c-abfd-c9795c3d292f)

# Task 02
```sql
SELECT pizza_name, price, pi.name as pizzeria_name FROM menu m
JOIN pizzeria pi ON pi.id = m.pizzeria_id
LEFT JOIN person_order po ON po.menu_id = m.id
WHERE po.menu_id IS NULL
ORDER BY pizza_name, price;
```
![image](https://github.com/itsveronika/days/assets/113369081/c8ae2063-4ce1-4389-963b-958fa1b3dfd3)

# Task 03
```sql
SELECT pi.name as pizzeria_name 
FROM pizzeria pi
JOIN person_visits pv ON pv.pizzeria_id  = pi.id
JOIN person p ON p.id = pv.person_id
WHERE p.gender = 'female'

UNION ALL

SELECT pi.name as pizzeria_name
FROM pizzeria pi
JOIN person_visits pv ON pv.pizzeria_id  = pi.id
JOIN person p ON p.id = pv.person_id
WHERE p.gender = 'male'
ORDER BY pizzeria_name;
```
![image](https://github.com/itsveronika/days/assets/113369081/3c7b8bd3-3338-4c7f-b93a-f93d9b421acf)

# Task 04
```sql
WITH women_order AS (
	SELECT pi.name FROM person_order po
	JOIN menu m ON m.id = po.menu_id
	JOIN person p ON p.id = po.person_id
	JOIN pizzeria pi ON pi.id = m.pizzeria_id
	WHERE p.gender = 'female'
), men_order AS (
	SELECT pi.name FROM person_order po
	JOIN menu m ON m.id = po.menu_id
	JOIN person p ON p.id = po.person_id
	JOIN pizzeria pi ON pi.id = m.pizzeria_id
	WHERE p.gender = 'male'
)

(
	SELECT * FROM women_order
	EXCEPT
	SELECT * FROM men_order
)
UNION
(
	SELECT * FROM men_order
	EXCEPT
	SELECT * FROM women_order
)
```
![image](https://github.com/itsveronika/days/assets/113369081/dfdfa5bf-c6a7-4534-a74a-452455683037)

# Task 06
```sql
SELECT m1.pizza_name, p1.name AS pizzeria_name_1, p2.name AS pizzeria_name_2, m1.price AS price
FROM menu m1
JOIN menu m2 ON m1.pizza_name = m2.pizza_name AND m1.price = m2.price AND m1.pizzeria_id <> m2.pizzeria_id
JOIN pizzeria p1 ON m1.pizzeria_id = p1.id
JOIN pizzeria p2 ON m2.pizzeria_id = p2.id
ORDER BY m1.pizza_name;
```
![image](https://github.com/itsveronika/days/assets/113369081/763f379c-a70a-45f7-8fbd-0439691026f4)

# Task 07
```sql
INSERT INTO menu (id, pizzeriaid, pizzaname, price)
VALUES (19, 2, 'Греческая пицца', 800);
```
![image](https://github.com/itsveronika/days/assets/113369081/5c1325d1-0aa2-42a9-b2a2-6c14632a59ea)

# Task 08
```sql
INSERT INTO menu (id, pizza_name, price, pizzeria_id)
VALUES ((SELECT MAX(id) FROM menu) + 1, 'sicilian pizza', 900, (SELECT id FROM pizzeria WHERE name = 'Dominos'));
```
![image](https://github.com/itsveronika/days/assets/113369081/488015e2-11e7-4c59-a35d-149dbd8ca83e)

# Task 09
```sql


