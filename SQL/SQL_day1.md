## SQL day 1 with Astha

- How to CREATE a DATABASE and USE it.

```SQL

CREATE DATABASE mergim_db

USE mergim_db
```



- How to CREATE a TABLE with COLUMS.



``` SQL
CREATE TABLE film_table
(
    film_id INT IDENTITY(1,1),
    film_name VARCHAR(20),
    film_type VARCHAR(12),
    date_of_release DATE,
    director VARCHAR(15),
    writer VARCHAR(15),
    star VARCHAR(15),
    film_language VARCHAR(15),
    website VARCHAR(MAX),
    plot_summary VARCHAR(MAX),

    PRIMARY KEY (film_id)

);
```



- How to ALTER a TABLE, adding a new COLUMN with Data Type INT.



``` SQL
ALTER TABLE film_table
ADD ratings INT
```



- How to VIEW the TABLE'S COLUMNS



```SQL
SP_HELP film_table
```



- How to INSERT ROWS (VALUES) into a TABLE.



```SQL
INSERT INTO film_table
(
    film_name, film_type, date_of_release, director
)
VALUES
(
    'EXTRACTION', 'ACTION', '20200424', 'Sam Hargrave'
)
```



- Show the TABLE.



```SQL
SELECT * FROM film_table
```



## Primary Key



- Most tables should have a primary Key.



- Primary keys should be Unique and not duplicated.



## Foreign keys



- Foreign keys are the primary key in another table. They are the link between relational databases.



## Composite Key



- Where two keys together form a Primary Key




## Candidate keys



- Where there are many keys which are 'Candidates' for being the primary key.
