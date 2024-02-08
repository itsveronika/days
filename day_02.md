## Task - 00
```sql
SELECT
	pi.name,
	pi.rating
FROM pizzeria pi
LEFT JOIN person_visits pv ON pi.id = pizzeria_id 
WHERE pv.id IS NULL
```
![image](https://github.com/ngllsq/sql_projects/assets/114596475/6e4f28c6-6fca-4b83-8d4b-b64c077f26b8)

## Task - 01
```sql
WITH all_days AS (
  SELECT days::date 
  FROM generate_series('2022-01-01', '2022-01-10', interval '1 day') AS days
)
SELECT all_days.days 
FROM all_days
LEFT JOIN person_visits pv ON all_days.days = pv.visit_date AND (pv.person_id = 1 OR pv.person_id = 2)
WHERE pv.visit_date IS NULL
ORDER BY 1 ASC;
```
![image](https://github.com/itsveronika/days/assets/113369081/181c8013-fc61-43af-8682-d5417f013055)

## Task - 06 
```sql
SELECT 
	m.pizza_name,
	pi.name AS pizzeria_name
FROM menu m
JOIN pizzeria pi ON m.pizzeria_id = pi.id
JOIN person_order po ON m.id = po.menu_id 
JOIN person p ON po.person_id = p.id
WHERE p.name = 'Denis' OR p.name = 'Anna'
ORDER BY 1, 2;
```
![image](https://github.com/itsveronika/days/assets/113369081/ceacb378-e4ae-40b9-9b15-d1a382f39433)

## Task - 09
```sql
SELECT DISTINCT p.name
FROM person p
JOIN person_order po ON p.id = po.person_id
JOIN menu m1 ON po.menu_id = m1.id AND m1.pizza_name = 'pepperoni pizza'
WHERE p.gender = 'female' 
AND EXISTS (
    SELECT 
    FROM person_order po2
    JOIN menu m2 ON po2.menu_id = m2.id AND m2.pizza_name = 'cheese pizza'
    WHERE po2.person_id = p.id
)
ORDER BY p.name;
```
![image](https://github.com/itsveronika/days/assets/113369081/d35c46cf-42be-4513-a36e-4706b2eaa81f)
