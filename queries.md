# SQL Запити (Тема 7. Робота з часом. Додаткові вбудовані SQL функції)

## Завдання 1
SQL-запит, який для таблиці `orders` з атрибута `date` витягує рік, місяць і число. Виводить їх у три окремі атрибути поряд з атрибутом `id` та оригінальним атрибутом `date`:

```sql
SELECT 
    id,
    date,
    YEAR(date) AS year,
    MONTH(date) AS month,
    DAY(date) AS day
FROM orders;
```

---

## Завдання 2
SQL-запит, який для таблиці `orders` до атрибута `date` додає один день. Виводить атрибут `id`, оригінальний атрибут `date` та результат додавання:

```sql
SELECT 
    id,
    date,
    DATE_ADD(date, INTERVAL 1 DAY) AS date_plus_one_day
FROM orders;
```

---

## Завдання 3
SQL-запит, який для таблиці `orders` для атрибута `date` відображає кількість секунд з початку відліку (значення timestamp). Використовує функцію `UNIX_TIMESTAMP`:

```sql
SELECT 
    id,
    date,
    UNIX_TIMESTAMP(date) AS timestamp_seconds
FROM orders;
```

---

## Завдання 4
SQL-запит, який рахує, скільки таблиця `orders` містить рядків з атрибутом `date` у межах між `1996-07-10 00:00:00` та `1996-10-08 00:00:00`:

```sql
SELECT 
    COUNT(*) AS total_orders
FROM orders
WHERE date BETWEEN '1996-07-10 00:00:00' AND '1996-10-08 00:00:00';
```

---

## Завдання 5
SQL-запит, який для таблиці `orders` виводить на екран атрибут `id`, атрибут `date` та JSON-об’єкт `{"id": <атрибут id рядка>, "date": <атрибут date рядка>}` за допомогою функції `JSON_OBJECT`:

```sql
SELECT 
    id,
    date,
    JSON_OBJECT('id', id, 'date', date) AS order_json
FROM orders;
```
