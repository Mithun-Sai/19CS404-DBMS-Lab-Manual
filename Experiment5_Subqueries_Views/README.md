# Experiment 5: Subqueries and Views

## AIM
To study and implement subqueries and views.

## THEORY

### Subqueries
A subquery is a query inside another SQL query and is embedded in:
- WHERE clause
- HAVING clause
- FROM clause

**Types:**
- **Single-row subquery**:
  Sub queries can also return more than one value. Such results should be made use along with the operators in and any.
- **Multiple-row subquery**:
  Here more than one subquery is used. These multiple sub queries are combined by means of ‘and’ & ‘or’ keywords.
- **Correlated subquery**:
  A subquery is evaluated once for the entire parent statement whereas a correlated Sub query is evaluated once per row processed by the parent statement.

**Example:**
```sql
SELECT * FROM employees
WHERE salary > (SELECT AVG(salary) FROM employees);
```
### Views
A view is a virtual table based on the result of an SQL SELECT query.
**Create View:**
```sql
CREATE VIEW view_name AS
SELECT column1, column2 FROM table_name WHERE condition;
```
**Drop View:**
```sql
DROP VIEW view_name;
```


## Question 1
<img width="1237" height="543" alt="image" src="https://github.com/user-attachments/assets/b8aa2a61-4d07-4fe8-9b16-17f81b2093a9" />


```sql
SELECT ord_no,
       purch_amt,
       ord_date,
       customer_id,
       salesman_id
FROM orders
WHERE salesman_id IN (
    SELECT salesman_id
    FROM orders
    WHERE customer_id = 3007
);
```

### Output:

<img width="637" height="276" alt="image" src="https://github.com/user-attachments/assets/5d55499a-ddc9-4fcb-bd26-c2b3f8ae1f58" />


## Question 2
<img width="506" height="372" alt="image" src="https://github.com/user-attachments/assets/fbaae250-2235-4526-9437-8fe9ceac6c31" />


```sql
SELECT *
FROM CUSTOMERS
WHERE SALARY > 1500;

```

### Output:

<img width="633" height="342" alt="image" src="https://github.com/user-attachments/assets/870b16d1-8caa-4040-9770-461c9a8c03f3" />


## Question 3
<img width="601" height="372" alt="image" src="https://github.com/user-attachments/assets/99c577d2-bd93-484b-bdb8-d408e805a7f6" />


```sql
SELECT s.salesman_id, s.name
FROM salesman s
JOIN customer c
ON s.salesman_id = c.salesman_id
GROUP BY s.salesman_id, s.name
HAVING COUNT(c.customer_id) > 1;
```

### Output:
<img width="342" height="286" alt="image" src="https://github.com/user-attachments/assets/4bee9720-e3af-4f62-a459-f3abd339f3ed" />


## Question 4
<img width="627" height="421" alt="image" src="https://github.com/user-attachments/assets/ebd94602-747c-4926-9db0-0023f335a67c" />


```sql
SELECT o.ord_no,
       o.purch_amt,
       o.ord_date,
       o.salesman_id
FROM orders o
JOIN salesman s
ON o.salesman_id = s.salesman_id
WHERE s.commission = (
    SELECT MAX(commission)
    FROM salesman
);
```

### Output:
<img width="532" height="280" alt="image" src="https://github.com/user-attachments/assets/46787a80-7400-47c0-ba9a-8f454cb9298d" />


## Question 5
<img width="575" height="232" alt="image" src="https://github.com/user-attachments/assets/a4ba2e2c-403b-4736-891d-9c600157853e" />


```sql
SELECT department_id AS depar,
       department_name
FROM Departments
WHERE LENGTH(department_name) > (
    SELECT AVG(LENGTH(department_name))
    FROM Departments
);
```

### Output:
<img width="312" height="255" alt="image" src="https://github.com/user-attachments/assets/8cb664c2-2ff6-446d-866c-2fcbda61f038" />


## Question 6
<img width="480" height="250" alt="image" src="https://github.com/user-attachments/assets/969852a3-6a3f-48cf-96ab-66419d8a0da8" />


```sql
SELECT medication_id AS medic,
       medication_name,
       dosage
FROM Medications
WHERE dosage = (
    SELECT MIN(dosage)
    FROM Medications
);
```

### Output:
<img width="461" height="247" alt="image" src="https://github.com/user-attachments/assets/02a309e4-a3bc-45b6-9c86-cc604ec13719" />


## Question 7
<img width="533" height="342" alt="image" src="https://github.com/user-attachments/assets/4158529f-fd30-4f9e-a43d-f6b6532d84fa" />


```sql
SELECT DISTINCT commission 
FROM salesman 
WHERE city = 'Paris';
```

### Output:
<img width="456" height="247" alt="image" src="https://github.com/user-attachments/assets/8cbaab40-416e-4abc-9dbb-56261b10452a" />


## Question 8
<img width="562" height="308" alt="image" src="https://github.com/user-attachments/assets/6b57bc1a-7e2c-4fad-ba8b-01ec135db6ce" />


```sql
SELECT *
FROM Employee
WHERE age < (
    SELECT AVG(age)
    FROM Employee
    WHERE income > 1000000
);
```

### Output:
<img width="637" height="265" alt="image" src="https://github.com/user-attachments/assets/3a6a05a2-2641-410e-b116-bfc865bbc057" />


## Question 9
<img width="492" height="342" alt="image" src="https://github.com/user-attachments/assets/aa43ed97-234a-45db-a7ed-e2c81a44db27" />


```sql
SELECT *
FROM CUSTOMERS
WHERE SALARY > 4500;
```

### Output:
<img width="625" height="266" alt="image" src="https://github.com/user-attachments/assets/ffb43b5d-7c32-40d2-9115-01be05c35444" />


## Question 10
<img width="626" height="332" alt="image" src="https://github.com/user-attachments/assets/6b55eec8-f910-415e-b641-d69e4217d2fe" />


```sql
SELECT student_name, grade
FROM GRADES g
WHERE grade = (
    SELECT MIN(grade)
    FROM GRADES
    WHERE subject = g.subject
);
```

### Output:
<img width="407" height="257" alt="image" src="https://github.com/user-attachments/assets/75f415a9-c4a6-49c4-b7dd-579b85372737" />



## RESULT
Thus, the SQL queries to implement subqueries and views have been executed successfully.
