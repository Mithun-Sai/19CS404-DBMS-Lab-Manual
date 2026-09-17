# Experiment 6: Joins

## AIM
To study and implement different types of joins.

## THEORY

SQL Joins are used to combine records from two or more tables based on a related column.

### 1. INNER JOIN
Returns records with matching values in both tables.

**Syntax:**
```sql
SELECT columns
FROM table1
INNER JOIN table2
ON table1.column = table2.column;
```

### 2. LEFT JOIN
Returns all records from the left table, and matched records from the right.

**Syntax:**

```sql
SELECT columns
FROM table1
LEFT JOIN table2
ON table1.column = table2.column;
```
### 3. RIGHT JOIN
Returns all records from the right table, and matched records from the left.

**Syntax:**

```sql
SELECT columns
FROM table1
RIGHT JOIN table2
ON table1.column = table2.column;
```
### 4. FULL OUTER JOIN
Returns all records when there is a match in either left or right table.

**Syntax:**

```sql
SELECT columns
FROM table1
FULL OUTER JOIN table2
ON table1.column = table2.column;
```

## Question 1
<img width="610" height="397" alt="image" src="https://github.com/user-attachments/assets/bae68c14-eeed-49d8-84ac-b484a7b7b24b" />

```sql
SELECT p.first_name
FROM patients p
INNER JOIN surgeries s
ON p.patient_id = s.patient_id
WHERE s.surgery_date = '2024-01-15';

```

### Output:
<img width="272" height="245" alt="image" src="https://github.com/user-attachments/assets/1473c8b3-07ae-4511-b104-b3ad05a9c116" />


## Question 2
<img width="612" height="510" alt="image" src="https://github.com/user-attachments/assets/dcf36b44-7454-484d-9322-fdb5fe5be563" />

```sql
SELECT c.cust_name AS "Customer Name",
       c.city,
       s.name AS "Salesman",
       s.commission
FROM customer c
INNER JOIN salesman s
ON c.salesman_id = s.salesman_id;
```

### Output:
<img width="637" height="520" alt="image" src="https://github.com/user-attachments/assets/85e743c3-d020-4b43-a6c7-b2eb1afd0dd3" />


## Question 3
<img width="636" height="507" alt="image" src="https://github.com/user-attachments/assets/9d70cc9b-c0e2-4aab-bcaa-f9466ec3d177" />


```sql
SELECT o.ord_no, o.purch_amt, c.cust_name, c.city
FROM orders o
INNER JOIN customer c
ON o.customer_id = c.customer_id
WHERE o.purch_amt BETWEEN 500 AND 2000;
```

### Output:
<img width="632" height="300" alt="image" src="https://github.com/user-attachments/assets/434acebe-53df-42ee-817a-239d4aeca9ac" />


## Question 4
<img width="608" height="355" alt="image" src="https://github.com/user-attachments/assets/a268abda-f5d8-40bd-9999-7f7708c2cee0" />


```sql
SELECT p.*
FROM patients p
INNER JOIN appointments a
ON p.patient_id = a.patient_id
WHERE a.appointment_date BETWEEN '2024-02-01' AND '2024-02-28';
```

### Output:
<img width="625" height="267" alt="image" src="https://github.com/user-attachments/assets/05c230cd-dd41-4fbb-a5cd-8c188ac3d653" />


## Question 5
<img width="622" height="767" alt="image" src="https://github.com/user-attachments/assets/2ab4a957-7a49-4bbc-a571-1940563615da" />

```sql
SELECT c.cust_name,
       c.city,
       o.ord_no,
       o.ord_date,
       o.purch_amt AS "Order Amount",
       s.name,
       s.commission
FROM customer c
LEFT JOIN orders o
    ON c.customer_id = o.customer_id
LEFT JOIN salesman s
    ON c.salesman_id = s.salesman_id;
```

### Output:
<img width="632" height="667" alt="image" src="https://github.com/user-attachments/assets/b3656b48-4fc8-4130-b036-ffe975f85190" />


## Question 6
<img width="640" height="237" alt="image" src="https://github.com/user-attachments/assets/24dfb953-a037-43f4-97db-209838cfb583" />

```sql
SELECT s.name, c.cust_name, c.city, c.grade, c.salesman_id
FROM salesman s
LEFT JOIN customer c
    ON s.salesman_id = c.salesman_id
WHERE s.salesman_id IN (
    SELECT salesman_id
    FROM customer
    GROUP BY salesman_id
    HAVING COUNT(*) > 1
);
```

### Output:
<img width="630" height="372" alt="image" src="https://github.com/user-attachments/assets/92fca3a1-7c8d-4057-b4e2-0f54dbc2d406" />


## Question 7
<img width="602" height="370" alt="image" src="https://github.com/user-attachments/assets/2d37f857-ecb7-42c5-bf54-f49a5bf57162" />

```sql
SELECT n.*
FROM nurses n
INNER JOIN departments d
ON n.department_id = d.department_id
WHERE d.department_name = 'Pediatrics';
```

### Output:
<img width="636" height="263" alt="image" src="https://github.com/user-attachments/assets/0879bce8-877c-4c15-ad06-1079f3388be0" />


## Question 8
<img width="627" height="487" alt="image" src="https://github.com/user-attachments/assets/5cd01bb7-4a62-4fed-bab2-5eac732b64be" />

```sql
SELECT c.cust_name,
       c.city,
       c.grade,
       s.name AS Salesman,
       s.city
FROM customer c
INNER JOIN salesman s
    ON c.salesman_id = s.salesman_id
WHERE c.grade < 300
ORDER BY c.customer_id ASC;
```

### Output:
<img width="650" height="450" alt="image" src="https://github.com/user-attachments/assets/da5e9d71-8730-4b81-92cb-54babaa04e3b" />


## Question 9
<img width="621" height="752" alt="image" src="https://github.com/user-attachments/assets/ec1e470f-3946-429a-8639-6fc6c2264f58" />

```sql
SELECT o.ord_no,
       o.ord_date,
       o.purch_amt,
       c.cust_name AS "Customer Name",
       c.grade,
       s.name AS "Salesman",
       s.commission
FROM orders o
INNER JOIN customer c
    ON o.customer_id = c.customer_id
INNER JOIN salesman s
    ON o.salesman_id = s.salesman_id;
```

### Output:
<img width="637" height="672" alt="image" src="https://github.com/user-attachments/assets/daa6d365-c668-469c-9445-1acac8089c69" />


## Question 10
<img width="632" height="287" alt="image" src="https://github.com/user-attachments/assets/69d878a4-842e-4407-952b-b256b78f9d91" />

```sql
SELECT s.name AS salesman_name,
       c.cust_name AS customer_name
FROM salesman s
LEFT JOIN customer c
ON s.salesman_id = c.salesman_id;
```

### Output:
<img width="415" height="502" alt="image" src="https://github.com/user-attachments/assets/301ff8cc-6266-461c-9a5a-5a324f601354" />


## RESULT
Thus, the SQL queries to implement different types of joins have been executed successfully.
