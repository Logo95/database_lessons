### Отчёт о проделанной работе в PostgreSQL

#### Создание базы данных и таблиц

Для проведения операций обновления, удаления и выборки данных была создана база данных с названием `company_db`. В этой базе данных были созданы таблицы `employees`, `customers` и `products`, представляющие информацию о сотрудниках компании, клиентах и продукции соответственно. Ниже приведен SQL-код создания базы данных и таблиц:

```sql
-- Создание базы данных company_db
CREATE DATABASE company_db;

-- Подключение к базе данных company_db
\c company_db;

-- Создание таблицы employees
CREATE TABLE employees (
    id SERIAL PRIMARY KEY,
    name VARCHAR(100),
    department VARCHAR(100),
    salary NUMERIC
);

-- Создание таблицы customers
CREATE TABLE customers (
    id SERIAL PRIMARY KEY,
    name VARCHAR(100),
    email VARCHAR(100),
    last_purchase_date DATE
);

-- Создание таблицы products
CREATE TABLE products (
    id SERIAL PRIMARY KEY,
    name VARCHAR(100),
    category VARCHAR(100),
    price NUMERIC
);
```
### Обновление данных в таблице с операторами UPDATE и WHERE
Для обновления данных в таблице `employees` был использован оператор UPDATE, который позволяет изменить значения определенных столбцов в строках, удовлетворяющих определенному условию. Ниже приведен пример выполнения обновления данных в таблице `employees`, где увеличивается зарплата сотрудников отдела IT на 10%:
```sql
-- Обновление данных в таблице employees
UPDATE employees
SET salary = salary * 1.1 -- Увеличение зарплаты на 10%
WHERE department = 'IT'; -- Обновление только для сотрудников в отделе IT
```

### Удаление данных из таблицы с операторами DELETE и WHERE
Для удаления данных из таблицы `customers` был использован оператор DELETE, который удаляет строки, удовлетворяющие определенному условию. Ниже приведен пример удаления клиентов, совершивших последнюю покупку до 2023 года:
```sql
-- Удаление данных из таблицы customers
DELETE FROM customers
WHERE last_purchase_date < '2023-01-01'; -- Удаление клиентов, совершивших последнюю покупку до 2023 года
```

### Получение данных из таблицы с операторами SELECT и WHERE
Для получения данных из таблицы `products` был использован оператор SELECT, который позволяет выбирать данные из таблицы с определенными условиями. Ниже приведен пример выборки продуктов из категории "Электроника":
```sql
-- Получение данных из таблицы products
SELECT * 
FROM products
WHERE category = 'Electronics'; -- Получение только продуктов из категории "Электроника"
```
```
результат:  
id |      name       |   category   |  price    
----+-----------------+--------------+---------  
  1 | Smartphone      | Electronics  |  699.99  
  2 | Laptop          | Electronics  | 1299.99  
  3 | Smartwatch      | Electronics  |  199.99  
  4 | Headphones      | Electronics  |   79.99  
(4 rows)  
