<h1>
  <span class="headline">Intro to PostgreSQL</span>
  <span class="subhead">Modifying and Deleting Data</span>
</h1>

**Learning objective:** By the end of this lesson, students will be able to modify and delete data in a PostgreSQL database.

## Modifying or updating data

We have seen how to insert data into a table, but what if we need to update existing data? The `UPDATE` command is used to modify existing records in a table. The syntax for the `UPDATE` command is as follows:

```postgres
UPDATE table_name
SET column1 = value1, column2 = value2, ...
WHERE condition;
```

- `UPDATE table_name` tells SQL which table you want to update.
- `SET column1 = value1, column2 = value2, ...` specifies the columns that should be updated and their new values.
- `WHERE condition` determines which records in the table should be updated. **Without this condition, all records in the table would be updated.**

Let's say we want to update the nationality of **Gabriel García Márquez** from `Colombian` to `Latin American` in the `authors` table. We can use the `UPDATE` command to do this:

```postgres
UPDATE authors SET nationality = 'Latin American' WHERE name = 'Gabriel García Márquez';
```

> 🚨 The `WHERE` clause is used to filter the rows that will be updated. If you omit the `WHERE` clause, **all rows in the table will be updated.**

We can also update multiple columns at once. Let's say we realize that **F. Scott Fitzgerald** is missing a nationality, and we want to set it to `American` while also correcting **Antoine de Saint-Exupéry**'s nationality from `French` to `French (Aviator & Writer)`. We can do this using multiple updates:

```postgres
UPDATE authors SET nationality = 'American' WHERE name = 'F. Scott Fitzgerald';
UPDATE authors SET nationality = 'French (Aviator & Writer)' WHERE name = 'Antoine de Saint-Exupéry';
```

## Deleting data

The `DELETE` command allows you to remove one or more rows from a table based on a specific condition. This is useful for cleaning up data or removing unnecessary records.

The basic syntax for the `DELETE` command is:

```postgres
DELETE FROM table_name WHERE condition;
```

- `DELETE FROM table_name` instructs SQL to remove data from the specified table.
- `WHERE condition` specifies which rows should be deleted. **If this condition is not included, all rows in the table will be deleted, which is rarely intended and could lead to data loss.**

Let's say we need to remove an author, for example, **Harper Lee**, from the `authors` table. We can use the `DELETE` command as follows:

```postgres
DELETE FROM authors WHERE name = 'Harper Lee';
```

This command deletes only the row where the `name` column matches 'Harper Lee'.

> ⚠️ Important Note on Deleting Records: If an author is deleted from the `authors` table, the books associated with that author in the `books` table may be affected depending on the foreign key constraints. If the `author_id` column in the books table is set to ON DELETE CASCADE, deleting an author will automatically delete all books associated with them. If the foreign key is set to ON DELETE SET NULL, the books will remain in the database but will have their `author_id` set to `NULL`. If no constraint is set, attempting to delete an author with referenced books may result in a foreign key violation error.

Now, let's say we want to remove all books written before **1900** from the `books` table. We can use the `DELETE` command with a `WHERE` clause to specify this condition:

```postgres
DELETE FROM books WHERE published_year < 1900;
```

### Caution

Always use the `WHERE` clause with care when deleting data. **Accidentally omitting this clause will result in all records being deleted from the table, which could be catastrophic if not intended.**

If you want to delete **all** data in a table but keep its structure, use:

```postgres
DELETE FROM books;
```

Alternatively, if you want to remove **all records and reset the table’s auto-incrementing primary key**, you can use:

```postgres
TRUNCATE TABLE books;
```

> **`TRUNCATE` is faster than `DELETE` without a `WHERE` clause**, but it cannot be rolled back if executed outside a transaction.

Understanding how to safely modify and delete data ensures better database management and integrity in PostgreSQL.
