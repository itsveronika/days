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
```


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
