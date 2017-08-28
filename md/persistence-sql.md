# SQL and Databases

-
-
# Relational databases

- relational databases store data as a set of **related** fields (A "relation")
- multiple relations across the same fields are stored together in a Table
- Relations -> Rows
- Fields -> Columns
- Collection of relations/rows -> Table

-
#### One way to think of it

- Object ~= Row (In the beginning anyway)
- Class ~= Table (again, in the beginning -- arrays make this tricky)
- Fields/Properties ~= Columns

-
### SQL

- Structured Query Language
- A standardized way to communicate with databases
- Heavily used on most relational databases
- Many different dialects with small variations 

-
### non-relational, schemaless, and noSQL databases:

- Slightly different meanings, often used to just mean "Not SQL"
- Take different approaches to data storage and retreival
- Often borrow some principles from SQL/Relational databases
- Beyond the scope of this lesson

-
### Our Environment:

- H2 embedded database
- Oracle dialect
- running in Spring Boot
- Using Hibernate ORM (more on that later)

-
-
### SQL Commands

-
#### INSERT

- Put data into a table
- Must provide all required values
- columns not provided are set to `NULL`
  -  This might cause an error

-
#### SELECT/FROM

- Request data from one or more tables
- Specify desired columns, or get all columns with `*`
- Used with aggregate functions like `COUNT()` and `SUM()`

-
#### WHERE

- Helps to refine queries/filter out results
- Refine further with `AND` or `OR` clauses


-
#### ORDER BY

- Control the order of returned results
- Specify the column to sort on
- Optional Ascending (`ASC`) or Descending (`DESC`) operator
  - `ASC` by default

NOTE: What happens when dealing with an OTHER type object?

-
#### GROUP BY

- Group results together by a column value
- Allows category-specific aggregate calculations
- eg: `SELECT make, AVG(price) FROM cars GROUP BY make;`

-
#### UPDATE

- Change existing values in database
- Affects all values in a column unless `WHERE` is present


-
#### Aliases (AS)

- Provides an alias for the named table or value
- Use it to make queries easier to read/shorter


-
#### DELETE

- Removes all selected rows
- Doesn't care if you didn't mean to hit `Enter` (No warning)

-
-
## Car Database Demo 


-
### Context:

```SQL
CREATE TABLE CAR (
  ID INT NOT NULL AUTO_INCREMENT,
  MAKE VARCHAR2(255) not null default '',
  MODEL varchar2(255) NOT NULL DEFAULT '',
  YEAR VARCHAR2(5) NOT NULL DEFAULT '01907',
  PRIMARY KEY (ID),
  CONSTRAINT 'unique_make_model_year' UNIQUE (make, model, year)
);

CREATE TABLE auto_prices (
  id INT PRIMARY KEY AUTO_INCREMENT,
  car_id INT REFERENCES car(id),
  package VARCHAR2(15) NOT NULL,
  price NUMBER(10,2) NOT NULL CHECK(price > 0),
  CONSTRAINT 'unique_package_per_car' UNIQUE (car_id, package)
);
```


-
```SQL
INSERT INTO car (make, model, year) 
VALUES ('Honda', 'Accord', 2012);

INSERT INTO car (make, model, year) 
VALUES ('Toyota', 'Camry', 2014);

INSERT INTO car (make, model, year) 
VALUES ('Honda', 'Civic', 2015);

INSERT INTO car (make, model, year) 
VALUES ('Subaru', 'Legacy', 2018);
```

-
```SQL
INSERT INTO auto_prices (car_id, package, price)
VALUES (2, Economy, 15000);
```

-
```SQL
INSERT INTO auto_prices (car_id, package, price)
VALUES
  (1, 'Economy', 12500),
  (1, 'Standard', 18000),
  (1, 'Navigation', 19500),
  (1, 'Luxury', 24000),
  (1, 'Opulent', 95000);
```

-
```SQL
INSERT INTO auto_prices (car_id, package, price) 
VALUES 
  (3, 'Economy', 10500), 
  (3, 'Standard', 16000), 
  (3, 'Navigation', 17500), 
  (3, 'Luxury', 22000), 
  (3, 'Opulent', 93000);
```

-
```SQL
SELECT c.make, c.model, p.package, p.price FROM car AS c, auto_prices AS p 
WHERE c.id = p.car_id;
```

```SQL
SELECT c.make, c.model, p.package, p.price 
FROM car AS c, auto_prices AS p 
WHERE c.id = p.car_id 
  AND c.make = 'Honda';
```

-
```SQL
DELETE FROM auto_prices WHERE package = 'Opulent';
```

```SQL
DELETE FROM auto_prices;
-- WHAT HAVE I DONE!?!
```

-
-
### Resources

- [SQL Zoo](http://sqlzoo.net/)
- [H2 Reference](http://www.h2database.com/html/main.html)
- Code School [Try SQL](https://www.codeschool.com/courses/try-sql)