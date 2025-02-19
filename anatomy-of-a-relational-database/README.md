<h1>
  <span class="headline">Intro to PostgreSQL</span>
  <span class="subhead">Anatomy of a Relational Database</span>
</h1>

**Learning objective:** By the end of this lesson, students will be able to describe the fundamental structure of relational databases, including how tables, columns, and rows organize data. They will also understand common data types, constraints, and relationships that ensure data integrity and efficiency.

## Schema

The structure of a relational database is defined by its schema.

A schema defines multiple elements of a database, including:

- **Tables:** These store data in a structured format using rows and columns. Each table represents a specific type of data, such as books or authors.

- **Indexes:** These help speed up searches and queries by allowing the database to locate data more quickly.

- **Constraints:** These are rules that ensure the accuracy and consistency of data, such as requiring certain fields to always have a value or ensuring that data in one table matches data in another.

## Tables

Tables are the core components of a relational database. Here's a simple view of what a database table might look like. This might look similar to a table in a spreadsheet, and for a good reason - both are structured as tables composed of **_columns_** and **_rows_**:

<!-- ![An example of a relational database table](./assets/table.png) -->

```
        col    col                           col
         |      |                             |
       | id  | title                       | published_year |
row  - | --- | --------------------------- | -------------- |
row  - | 1   | Pride and Prejudice         | 1813           |
row  - | 2   | To Kill a Mockingbird       | 1960           |
row  - | 3   | 1984                        | 1949           |
row  - | 4   | The Alchemist               | 1988           |
row  - | 5   | The Kite Runner             | 2003           |
row  - | 6   | One Thousand and One Nights | 8th Century    |
```

A table in a relational database holds data for a particular _data resource_ such as **_books_**, which is represented in columns like `title`, `author_id`, and `published_year`.

> 📚 A _**data resource**_ represents a real-world object or concept. It is a group of definable things, like books, authors, publishers, etc. A resource is composed of _entities_ - each stored as a row within the table. Each column of the table holds a specific attribute. Collectively, columns describe the properties of each entity.

## Columns and Rows

### Rows (records)

A row in a table represents a single instance of the data entity.

For example, a particular **book** is in a **books** table.

TABLE: **books**

| id (PK) | title                       | published_year | author_id (FK) |
| ------- | --------------------------- | -------------- | -------------- |
| 1       | Pride and Prejudice         | 1813           | 1              |
| 2       | To Kill a Mockingbird       | 1960           | 2              |
| 3       | 1984                        | 1949           | 3              |
| 4       | The Alchemist               | 1988           | 4              |
| 5       | The Kite Runner             | 2003           | 5              |
| 6       | One Thousand and One Nights | 8th Century    | 6              |

TABLE: **authors**

| id (PK) | name                    | nationality |
| ------- | ----------------------- | ----------- |
| 1       | Jane Austen             | British     |
| 2       | Harper Lee              | American    |
| 3       | George Orwell           | British     |
| 4       | Paulo Coelho            | Brazilian   |
| 5       | Khaled Hosseini         | Afghan      |
| 6       | Traditional (Anonymous) | Various     |

### Columns (fields)

The columns of a table have a:

- Name
- Data type (all data in a column must be of the same type)
- Optional constraints

The typical naming convention is usually snake_cased and singular.

**PostgreSQL** has many [data types](https://www.postgresql.org/docs/current/datatype.html) for columns, but the most common ones include:

- `integer`
- `decimal`
- `varchar` (variable-length strings)
- `text` (same as `varchar`)
- `date` (does not include time)
- `timestamp` (both date and time)
- `boolean`

Typical constraints for a column include:

- `PRIMARY KEY`: column, or group of columns, uniquely identify a row
- `REFERENCES` (Foreign Key): value in a column must match the primary key in another table
- `NOT NULL`: column must have a value; it cannot be empty (null)
- `UNIQUE`: data in this column must be unique among all rows in the table

### Primary Keys (PK) and Foreign Keys (FK)

The field that uniquely identifies each row in the table is known as that table's **primary key (PK)**.

Since only one type of data entity can be held in a single table, related data, for example, the **books** written by an **author**, are stored in separate tables and linked via what is known as a **foreign key (FK)**.
