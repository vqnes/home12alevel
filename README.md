# MySQL, Data manipulation
### Operator INSERT
```sql
mysql> INSERT INTO actors SET first_name="Pierce", middle_name="Brendan", last_name="Brosnan", birth_date="1953-05-16", homeland="Ireland";

Query OK, 1 row affected (0.24 sec)


mysql> INSERT INTO movie_directors (first_name, middle_name, last_name, pseudonym, birth_date, death_date, homeland) VALUES
    -> ("Wesley", "Wales", "Anderson", null, "1969-05-01", null, "USA"),
    -> ("Quentin", "Jerome", "Tarantino", null, "1963-03-27", null, "USA");

Query OK, 2 rows affected (0.11 sec)
Records: 2  Duplicates: 0  Warnings: 0


mysql> INSERT INTO actors (first_name, middle_name, last_name, pseudonym, birth_date, death_date, homeland) SELECT first_name, middle_name, last_name, pseudonym, birth_date, death_date, homeland FROM actors;

Query OK, 3 rows affected (0.06 sec)
Records: 3  Duplicates: 0  Warnings: 0
```
### Operator SELECT
```sql
mysql> SELECT * FROM actors;

+----+------------+-------------+-----------+-----------+------------+------------+----------+
| id | first_name | middle_name | last_name | pseudonym | birth_date | death_date | homeland |
+----+------------+-------------+-----------+-----------+------------+------------+----------+
|  1 | Bradley    | William     | Pitt      | NULL      | 1963-12-18 | NULL       | USA      |
|  2 | Leonardo   | Wilhelm     | DiCaprio  | NULL      | 1974-11-11 | NULL       | USA      |
|  3 | Pierce     | Brendan     | Brosnan   | NULL      | 1953-05-16 | NULL       | Ireland  |
|  4 | Bradley    | William     | Pitt      | NULL      | 1963-12-18 | NULL       | USA      |
|  5 | Leonardo   | Wilhelm     | DiCaprio  | NULL      | 1974-11-11 | NULL       | USA      |
|  6 | Pierce     | Brendan     | Brosnan   | NULL      | 1953-05-16 | NULL       | Ireland  |
+----+------------+-------------+-----------+-----------+------------+------------+----------+
6 rows in set (0.00 sec)


mysql> SELECT first_name, middle_name, last_name FROM actors;

+------------+-------------+-----------+
| first_name | middle_name | last_name |
+------------+-------------+-----------+
| Bradley    | William     | Pitt      |
| Leonardo   | Wilhelm     | DiCaprio  |
| Pierce     | Brendan     | Brosnan   |
| Bradley    | William     | Pitt      |
| Leonardo   | Wilhelm     | DiCaprio  |
| Pierce     | Brendan     | Brosnan   |
+------------+-------------+-----------+
6 rows in set (0.00 sec)


mysql> SELECT DISTINCT first_name, middle_name, last_name FROM actors;

+------------+-------------+-----------+
| first_name | middle_name | last_name |
+------------+-------------+-----------+
| Bradley    | William     | Pitt      |
| Leonardo   | Wilhelm     | DiCaprio  |
| Pierce     | Brendan     | Brosnan   |
+------------+-------------+-----------+
3 rows in set (0.00 sec)


mysql> SELECT * FROM actors LIMIT 2, 3;

+----+------------+-------------+-----------+-----------+------------+------------+----------+
| id | first_name | middle_name | last_name | pseudonym | birth_date | death_date | homeland |
+----+------------+-------------+-----------+-----------+------------+------------+----------+
|  3 | Pierce     | Brendan     | Brosnan   | NULL      | 1953-05-16 | NULL       | Ireland  |
|  4 | Bradley    | William     | Pitt      | NULL      | 1963-12-18 | NULL       | USA      |
|  5 | Leonardo   | Wilhelm     | DiCaprio  | NULL      | 1974-11-11 | NULL       | USA      |
+----+------------+-------------+-----------+-----------+------------+------------+----------+
3 rows in set (0.00 sec)


mysql> SELECT birth_date, death_date FROM actors GROUP BY birth_date, death_date HAVING birth_date>"1960";

+------------+------------+
| birth_date | death_date |
+------------+------------+
| 1963-12-18 | NULL       |
| 1974-11-11 | NULL       |
+------------+------------+
2 rows in set, 1 warning (0.00 sec)


mysql> SELECT first_name, middle_name, last_name FROM actors WHERE homeland="USA" GROUP BY first_name, middle_name, last_name, birth_date ORDER BY birth_date;

+------------+-------------+-----------+
| first_name | middle_name | last_name |
+------------+-------------+-----------+
| Bradley    | William     | Pitt      |
| Leonardo   | Wilhelm     | DiCaprio  |
+------------+-------------+-----------+
2 rows in set (0.01 sec)
```
### Operators UPDATE and DELETE
```sql
mysql> UPDATE actors SET middle_name="Will" WHERE id=4;

Query OK, 1 row affected (0.10 sec)
Rows matched: 1  Changed: 1  Warnings: 0


mysql> DELETE FROM actors WHERE id>3;

Query OK, 3 rows affected (0.25 sec)
```
