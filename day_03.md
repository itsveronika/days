## Task - 00
```sql
SELECT
  m.pizza_name,
  m.price,
  pi.name AS pizzeria_name,
  pv.visit_date
FROM person_visits pv
JOIN person p ON pv.person_id = p.id
JOIN menu m ON pv.pizzeria_id = m.pizzeria_id
JOIN pizzeria pi ON pi.id = pv.pizzeria_id
WHERE (p.name = 'Kate') AND (m.price BETWEEN 800 AND 1000)
ORDER BY 1, 2, 3
```
![image](https://github.com/itsveronika/days/assets/113369081/5c51838f-b45c-442e-9ab1-7a9e4bf38195)
