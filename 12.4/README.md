# Домашнее задание к занятию 12.4. «Реляционные базы данных: SQL. Часть 2» - Екимовский К.

---

### Задание 1

Запрос:
```
SELECT s.store_id, CONCAT(st.first_name, ' ', st.last_name) AS staff_name, c.city, COUNT(cus.customer_id) 
FROM store s
JOIN staff st ON st.staff_id = s.manager_staff_id 
JOIN address a ON a.address_id = s.address_id 
JOIN city c ON c.city_id = a.city_id
JOIN customer cus ON cus.store_id = s.store_id 
GROUP BY cus.store_id
HAVING COUNT(cus.customer_id) > 300;
```

---

### Задание 2

Запрос:
```
SELECT COUNT(f.film_id) 
FROM film f
WHERE f.`length` > (SELECT AVG(f.length) FROM film f);
```

---

### Задание 3

Запрос:
```
SELECT MONTH(p.payment_date), SUM(p.amount), COUNT(r.rental_id)
FROM payment p
JOIN rental r ON r.rental_id = p.payment_id 
GROUP BY MONTH(p.payment_date)
```

---

### Задание 4

Запрос:
```
SELECT CONCAT(st.first_name, ' ', st.last_name) AS staff_name, COUNT(r.rental_id),
  CASE
    WHEN COUNT(r.rental_id) > 8010 THEN 'YES'
    ELSE 'NO'
  END AS award
FROM staff st
JOIN rental r ON r.staff_id = st.staff_id
GROUP BY r.staff_id
```

----