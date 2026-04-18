# Solutions for StudyPlan SQL50 on LeetCode

## SELECT 

### 1757. Recyclable and Low Fat Products
```sql
SELECT product_id
FROM Products
WHERE low_fats = "Y" and recyclable="Y"
```

### 584. Find Customer Referee
```sql
SELECT name
FROM Customer
WHERE referee_id != 2 or referee_id is null
```

### 595. Big Countries
```sql
SELECT name, population, area
FROM World
WHERE population >= 25000000 OR area >= 3000000
```

### 1148. Article Views I
```sql
SELECT DISTINCT author_id AS id
FROM Views
WHERE author_id=viewer_id
ORDER BY id ASC
```

### 1683. Invalid Tweets
```sql
SELECT tweet_id
FROM Tweets
WHERE length(content)>15
```

## BASIC JOINS

### 1378. Replace Employee ID With The Unique Identifier
```sql
SELECT unique_id, name
FROM EmployeeUNI
RIGHT JOIN Employees on EmployeeUNI.id=Employees.id
```

### 1068. Product Sales Analysis I
```sql
SELECT product_name, year, price
FROM Sales
JOIN Product on Sales.product_id=Product.product_id
```

