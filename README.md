# SQL_project
## Task 1
Difficulty: Moderate

### Task 1.1
In your company there hasn't been a database table with all the employee information yet.

You need to set up the table called employees in the following way:

<img width="1272" height="72" alt="image" src="https://github.com/user-attachments/assets/d8f65c34-f2b7-45c3-8a51-d2a0b9ea00cc" />

There should be NOT NULL constraints for the following columns:

first_name,

last_name ,

job_position,

start_date DATE,

birth_date DATE

### My solution
```sql
CREATE TABLE employee
(emp_id SERIAL PRIMARY KEY,
first_name text NOT NULL,
last_name text NOT NULL,
job_position text NOT NULL,
salary NUMERIC(8,2),
start_date date NOT NULL,
birth_date date NOT NULL,
store_id INT,
department_id INT,
manager_id INT)
```

### Task 1.2

Set up an additional table called departments in the following way:

<img width="394" height="72" alt="image" src="https://github.com/user-attachments/assets/d0051384-6089-4aa8-9441-ac85c261885c" />


Additionally no column should allow nulls.

### My solution

```sql
CREATE TABLE departments (
department_id SERIAL PRIMARY KEY NOT NULL,
department text NOT NULL,
division text NOT NULL
)
```

## Task 2
Difficulty: Moderate


Alter the employees table in the following way:

- Set the column department_id to not null.

- Add a default value of CURRENT_DATE to the column start_date.

- Add the column end_date with an appropriate data type (one that you think makes sense).

- Add a constraint called birth_check that doesn't allow birth dates that are in the future.

- Rename the column job_position to position_title.


### My solution

```sql
ALTER TABLE employee
ALTER department_id SET NOT NULL;

UPDATE employee
SET start_date = CURRENT_DATE;

ALTER TABLE employee
ADD COLUMN end_date date;

ALTER TABLE employee
ADD CONSTRAINT birth_check CHECK (birth_date < CURRENT_DATE);

ALTER TABLE employee
RENAME job_position TO position_title
```

## Task 3
Difficulty: Moderate



### Task 3.1



Insert the following values into the employees table.

There will be most likely an error when you try to insert the values.

So, try to insert the values and then fix the error.

Columns:

Columns:

(emp_id,first_name,last_name,position_title,salary,start_date,birth_date,store_id,department_id,manager_id,end_date)


Values:

(1,'Morrie','Conaboy','CTO',21268.94,'2005-04-30','1983-07-10',1,1,NULL,NULL),
(2,'Miller','McQuarter','Head of BI',14614.00,'2019-07-23','1978-11-09',1,1,1,NULL),
(3,'Christalle','McKenny','Head of Sales',12587.00,'1999-02-05','1973-01-09',2,3,1,NULL),
(4,'Sumner','Seares','SQL Analyst',9515.00,'2006-05-31','1976-08-03',2,1,6,NULL),
(5,'Romain','Hacard','BI Consultant',7107.00,'2012-09-24','1984-07-14',1,1,6,NULL),
(6,'Ely','Luscombe','Team Lead Analytics',12564.00,'2002-06-12','1974-08-01',1,1,2,NULL),
(7,'Clywd','Filyashin','Senior SQL Analyst',10510.00,'2010-04-05','1989-07-23',2,1,2,NULL),
(8,'Christopher','Blague','SQL Analyst',9428.00,'2007-09-30','1990-12-07',2,2,6,NULL),
(9,'Roddie','Izen','Software Engineer',4937.00,'2019-03-22','2008-08-30',1,4,6,NULL),
(10,'Ammamaria','Izhak','Customer Support',2355.00,'2005-03-17','1974-07-27',2,5,3,2013-04-14),
(11,'Carlyn','Stripp','Customer Support',3060.00,'2013-09-06','1981-09-05',1,5,3,NULL),
(12,'Reuben','McRorie','Software Engineer',7119.00,'1995-12-31','1958-08-15',1,5,6,NULL),
(13,'Gates','Raison','Marketing Specialist',3910.00,'2013-07-18','1986-06-24',1,3,3,NULL),
(14,'Jordanna','Raitt','Marketing Specialist',5844.00,'2011-10-23','1993-03-16',2,3,3,NULL),
(15,'Guendolen','Motton','BI Consultant',8330.00,'2011-01-10','1980-10-22',2,3,6,NULL),
(16,'Doria','Turbat','Senior SQL Analyst',9278.00,'2010-08-15','1983-01-11',1,1,6,NULL),
(17,'Cort','Bewlie','Project Manager',5463.00,'2013-05-26','1986-10-05',1,5,3,NULL),
(18,'Margarita','Eaden','SQL Analyst',5977.00,'2014-09-24','1978-10-08',2,1,6,2020-03-16),
(19,'Hetty','Kingaby','SQL Analyst',7541.00,'2009-08-17','1999-04-25',1,2,6,'NULL'),
(20,'Lief','Robardley','SQL Analyst',8981.00,'2002-10-23','1971-01-25',2,3,6,2016-07-01),
(21,'Zaneta','Carlozzi','Working Student',1525.00,'2006-08-29','1995-04-16',1,3,6,2012-02-19),
(22,'Giana','Matz','Working Student',1036.00,'2016-03-18','1987-09-25',1,3,6,NULL),
(23,'Hamil','Evershed','Web Developper',3088.00,'2022-02-03','2012-03-30',1,4,2,NULL),
(24,'Lowe','Diamant','Web Developper',6418.00,'2018-12-31','2002-09-07',1,4,2,NULL),
(25,'Jack','Franklin','SQL Analyst',6771.00,'2013-05-18','2005-10-04',1,2,2,NULL),
(26,'Jessica','Brown','SQL Analyst',8566.00,'2003-10-23','1965-01-29',1,1,2,NULL)

### My solution
```sql
INSERT INTO employee (emp_id,first_name,last_name,position_title,
salary,start_date, birth_date, store_id,department_id,manager_id,end_date)
VALUES (1,'Morrie','Conaboy','CTO',21268.94,'2005-04-30','1983-07-10',1,1,NULL,NULL),
(2,'Miller','McQuarter','Head of BI',14614.00,'2019-07-23','1978-11-09',1,1,1,NULL),
(3,'Christalle','McKenny','Head of Sales',12587.00,'1999-02-05','1973-01-09',2,3,1,NULL),
(4,'Sumner','Seares','SQL Analyst',9515.00,'2006-05-31','1976-08-03',2,1,6,NULL),
(5,'Romain','Hacard','BI Consultant',7107.00,'2012-09-24','1984-07-14',1,1,6,NULL),
(6,'Ely','Luscombe','Team Lead Analytics',12564.00,'2002-06-12','1974-08-01',1,1,2,NULL),
(7,'Clywd','Filyashin','Senior SQL Analyst',10510.00,'2010-04-05','1989-07-23',2,1,2,NULL),
(8,'Christopher','Blague','SQL Analyst',9428.00,'2007-09-30','1990-12-07',2,2,6,NULL),
(9,'Roddie','Izen','Software Engineer',4937.00,'2019-03-22','2008-08-30',1,4,6,NULL),
(10,'Ammamaria','Izhak','Customer Support',2355.00,'2005-03-17','1974-07-27',2,5,3,'2013-04-14'),
(11,'Carlyn','Stripp','Customer Support',3060.00,'2013-09-06','1981-09-05',1,5,3,NULL),
(12,'Reuben','McRorie','Software Engineer',7119.00,'1995-12-31','1958-08-15',1,5,6,NULL),
(13,'Gates','Raison','Marketing Specialist',3910.00,'2013-07-18','1986-06-24',1,3,3,NULL),
(14,'Jordanna','Raitt','Marketing Specialist',5844.00,'2011-10-23','1993-03-16',2,3,3,NULL),
(15,'Guendolen','Motton','BI Consultant',8330.00,'2011-01-10','1980-10-22',2,3,6,NULL),
(16,'Doria','Turbat','Senior SQL Analyst',9278.00,'2010-08-15','1983-01-11',1,1,6,NULL),
(17,'Cort','Bewlie','Project Manager',5463.00,'2013-05-26','1986-10-05',1,5,3,NULL),
(18,'Margarita','Eaden','SQL Analyst',5977.00,'2014-09-24','1978-10-08',2,1,6,'2020-03-16'),
(19,'Hetty','Kingaby','SQL Analyst',7541.00,'2009-08-17','1999-04-25',1,2,6,NULL),
(20,'Lief','Robardley','SQL Analyst',8981.00,'2002-10-23','1971-01-25',2,3,6,'2016-07-01'),
(21,'Zaneta','Carlozzi','Working Student',1525.00,'2006-08-29','1995-04-16',1,3,6,'2012-02-19'),
(22,'Giana','Matz','Working Student',1036.00,'2016-03-18','1987-09-25',1,3,6,NULL),
(23,'Hamil','Evershed','Web Developper',3088.00,'2022-02-03','2012-03-30',1,4,2,NULL),
(24,'Lowe','Diamant','Web Developper',6418.00,'2018-12-31','2002-09-07',1,4,2,NULL),
(25,'Jack','Franklin','SQL Analyst',6771.00,'2013-05-18','2005-10-04',1,2,2,NULL),
(26,'Jessica','Brown','SQL Analyst',8566.00,'2003-10-23','1965-01-29',1,1,2,NULL)
```


### Task 3.2

Insert the following values into the departments table.

<img width="485" height="288" alt="image" src="https://github.com/user-attachments/assets/1b66a6ff-423f-40f0-adde-d056a8442d5c" />

### My solution
```sql
INSERT INTO departments (department, division)
VALUES ('Analytics', 'IT'),
('Finance', 'Administration'),
('Sales', 'Sales'),
('Website', 'IT'),
('Back Office', 'Administration')
```


## Task 4

Difficulty: Moderate



### Task 4.1

Jack Franklin gets promoted to 'Senior SQL Analyst' and the salary raises to 7200.

Update the values accordingly.

### My solution
```sql
UPDATE employee
SET salary = 7200, position_title = 'Senior SQL Analyst'
WHERE first_name = 'Jack' AND last_name = 'Franklin'
```



### Task 4.2

The responsible people decided to rename the position_title Customer Support to Customer Specialist.

Update the values accordingly.

### My solution
```sql
UPDATE employee
SET position_title = 'Customer Specialist'
WHERE position_title = 'Customer Support'
```
Task 4.3

All SQL Analysts including Senior SQL Analysts get a raise of 6%.

Upate the salaries accordingly.

### My solution
```sql
UPDATE employee
SET salary = (salary + (6*100)/salary)
WHERE position_title = 'SQL Analyst'
```

Task 4.4

Question:

What is the average salary of a SQL Analyst in the company (excluding Senior SQL Analyst)?

Answer:

8834.75

### My solution
```sql
SELECT 
ROUND(AVG(salary),2)
FROM employee
WHERE position_title = 'SQL Analyst'
```


## Task 5

Difficulty: Advanced


### Task 5.1

Write a query that adds a column called manager that contains  first_name and last_name (in one column) in the data output.

### My solution
```sql
ALTER TABLE employee
ADD manager text;

UPDATE employee
SET manager = first_name || ' ' || last_name
WHERE first_name = first_name AND last_name = last_name;


```

Secondly, add a column called is_active with 'false' if the employee has left the company already, otherwise the value is 'true'.

### My solution
```sql
ALTER TABLE employee
ADD is_active BOOL;

Update employee
SET is_active = TRUE
WHERE end_date IS NULL;

Update employee
SET is_active = FALSE
WHERE end_date IS NOT NULL;
```

### Task 5.2

Create a view called v_employees_info from that previous query.

