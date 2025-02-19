<h1>
  <span class="headline">Intro to PostgreSQL</span>
  <span class="subhead">Inserting and Selecting Data</span>
</h1>

**Learning objective:** By the end of this lesson, students will be able to insert data into a table and query data from a table using PostgreSQL.

## Inserting data

We now have a database and tables established, but they are empty! We can add a single row or multiple rows into a table using the `INSERT INTO` command.

The syntax for the `INSERT INTO` command looks like this:

```postgres
INSERT INTO table_name (column1, column2, ...)
VALUES
(value1, value2, ...)[, (value1, value2, ...), ...];
```

Let's add some books to the `books` table:

```postgres
-- Insert a single row
INSERT INTO books (title, published_year, author_id)
VALUES
('Pride and Prejudice', 1813, 1);

-- Insert multiple rows
INSERT INTO books (title, published_year, author_id)
VALUES
('To Kill a Mockingbird', 1960, 2),
('1984', 1949, 3),
('The Alchemist', 1988, 4);
```

> 🚨 Notice our use of the single quote (`'`) character above - this is required to indicate the use of a string in SQL.

> **Note:** We are not specifying the `id` column when inserting data into the `books` table. Since the `id` column is a `SERIAL` data type, PostgreSQL will automatically increment the value each time a new row is inserted.

Now lets add our authors to the `authors` table:

```postgres
-- Insert multiple rows
INSERT INTO authors (id, name, nationality)
VALUES
(1, 'Jane Austen', 'British'),
(2, 'Harper Lee', 'American'),
(3, 'George Orwell', 'British'),
(4, 'Paulo Coelho', 'Brazilian');
```

## Selecting data

Now that we have data in our `books` table, we can use the `SELECT` command to query the data. The syntax for the `SELECT` command is as follows:

```postgres
SELECT column1, column2, ... FROM table_name;
```

Let's query all the data from the `books` table:

```postgres
SELECT * FROM books;
```

> The `*` is a wildcard character that selects all columns from the table. If you only want to select specific columns, you can replace the `*` with the column names you want to select.

You should see the data you inserted into the `books` table in the terminal.

```postgresql
 id |          title           | published_year | author_id
----+--------------------------+---------------+-----------
  1 | Pride and Prejudice      |          1813 |         1
  2 | To Kill a Mockingbird    |          1960 |         2
  3 | 1984                     |          1949 |         3
  4 | The Alchemist            |          1988 |         4
(4 rows)
```

### Selecting data with `SELECT` clauses

The `SELECT` command is foundational in SQL for retrieving data from databases. To make your queries more precise and efficient, you can use several standard _clauses_ with `SELECT`:

- `WHERE`: Filters the returned rows based on a condition.
- `ORDER BY`: Sorts the returned rows based on a column.
- `LIMIT`: Limits the number of returned rows.
- `COUNT`: Returns the number of returned rows.

Let's look at how these clauses are used in real SQL queries:

#### Query 1: Books where the published year is before 1950

```postgres
SELECT title FROM books WHERE published_year < 1950;
```

Output:

```postgresql
         title
------------------------
 Pride and Prejudice
 1984
(2 rows)
```

#### Query 2: Books sorted by title in ascending order

```postgres
SELECT title, published_year FROM books ORDER BY title ASC;
```

Output:

```postgresql
         title           | published_year
------------------------+---------------
 1984                   | 1949
 Pride and Prejudice    | 1813
 The Alchemist          | 1988
 To Kill a Mockingbird  | 1960
(4 rows)
```

#### Query 3: First two books

```postgres
SELECT * FROM books LIMIT 2;
```

Output:

```postgresql
 id |         title          | published_year | author_id
----+------------------------+---------------+----------
  1 | Pride and Prejudice    |          1813 |        1
  2 | To Kill a Mockingbird  |          1960 |        2
(2 rows)
```

#### Query 4: Count the number of books in the table

```postgres
SELECT COUNT(*) FROM books;
```

Output:

```postgresql
 count
-------
     4
(1 row)
```

While the `SELECT` command might seem straightforward, its power becomes apparent when dealing with larger databases. With the right clauses, `SELECT` can help you efficiently query vast amounts of data, extract meaningful insights, and perform complex data manipulations.
