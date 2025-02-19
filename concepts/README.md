<h1>
  <span class="headline">Intro to PostgreSQL</span>
  <span class="subhead">Concepts</span>
</h1>


**Learning objective:** By the end of this lesson, students will be able to explain what a relational database is, how it differs from a non-relational database, and describe the structure of relational data, including tables, rows, and columns

## What is a database?

A **database** is a structured way to store and manage data. Databases enable efficient data retrieval, storage, and manipulation, making them essential for software applications, data analysis, and business intelligence.

There are two primary types of databases:

### Relational databases

Relational databases store data in structured tables with predefined relationships between them. They adhere to strict schemas and use **Structured Query Language (SQL)** to interact with data.

```markdown
| id  | A   | B   | C   |
| --- | --- | --- | --- |
| 1   | --- | --- | --- |
| 2   | --- | --- | --- |
| 3   | --- | --- | --- |
```

Key features:

- Data is stored in **tables** (similar to spreadsheets).
- Each **row** represents a unique record.
- Each **column** represents a specific field or attribute of the data.
- Relationships between tables are maintained using **primary keys** and **foreign keys**.
- Examples: **PostgreSQL, MySQL, Microsoft SQL Server**.

### Non-Relational `NoSQL` databases

Non-relational databases store data in more flexible formats, such as key-value pairs, documents, or graphs. They are optimized for scalability and performance in specific use cases, such as handling unstructured data.

```json
[
  {
    "id": 1,
    "A": "---",
    "B": "---",
    "C": "---"
  },
  {
    "id": 2,
    "A": "---",
    "B": "---",
    "C": "---"
  },
  {
    "id": 3,
    "A": "---",
    "B": "---",
    "C": "---"
  }
]
```

Key features:

- Data is stored in various formats (JSON, key-value, wide-column, graph, etc.).
- They often do not require a predefined schema.
- Designed for high scalability and distributed systems.
- Examples: **MongoDB (document-based), Redis (key-value), Neo4j (graph-based)**.

## SQL

[SQL (Structured Query Language)](https://developer.mozilla.org/en-US/docs/Glossary/SQL) is the standard language for interacting with relational databases. It allows users to:

- **Retrieve data** (`SELECT` queries).
- **Insert new records** (`INSERT` statements).
- **Update existing data** (`UPDATE` statements).
- **Delete data** (`DELETE` statements).
- **Define database structures** (`CREATE TABLE`, `ALTER TABLE`).

Though SQL is standardized, different relational database management systems `RDBMS` may have slight variations in syntax and supported features.

## PostgreSQL

[PostgreSQL](https://www.postgresql.org/) is an advanced, open-source **Relational Database Management System (RDBMS)** known for its power, flexibility, and reliability. Originally developed at the University of California, Berkeley, PostgreSQL has grown into one of the most robust database solutions used by companies worldwide.

**Key features:**

- **Full SQL compliance** with support for advanced SQL features.
- **Extensibility**, allowing users to define custom functions, operators, and data types.
- **Scalability**, supporting large datasets and high-performance applications.
- **Data integrity and security**, ensuring accurate and reliable data management.
- **Strong community support**, making it widely adopted in enterprise and web applications.

PostgreSQL is widely used in **web applications, financial systems, analytics platforms, and more**, making it a valuable tool for developers and data professionals.

## Understanding the structure of a relational database

### Tables, Rows, and Columns

Relational databases organize data into structured components:

- **Tables**: A table is the core structure in a relational database. It consists of rows and columns.
- **Rows**: Each row (or record) in a table represents a single entry of data.
- **Columns**: Columns define the specific attributes or fields of data (ex: `name`, `email`, `created_at`).

For example, consider a simple `employees` table:

```markdown
| id  | name   | role            | start_date |
| --- | ------ | --------------- | ---------- |
| 1   | Wei    | Developer       | 2022-01-10 |
| 2   | Ahmed  | Designer        | 2023-04-22 |
| 3   | Oliver | Project Manager | 2021-09-15 |
```

- Each **row** represents a different employee.
- Each **column** stores a specific type of information about employees.

### Relationships between tables

Relational databases establish relationships between tables using **keys**:

- **Primary Key (PK)**: A unique identifier for each row in a table.
- **Foreign Key (FK)**: A reference to a primary key in another table, establishing a relationship between tables.

Example: A `departments` table related to the `employees` table through a foreign key:

```markdown
| department_id | department_name |
| ------------- | --------------- |
| 1             | Engineering     |
| 2             | Design          |

| employee_id | name  | department_id |
| ----------- | ----- | ------------- |
| 1           | Wei   | 1             |
| 2           | Ahmed | 2             |
```

In this example, the `department_id` in the `employees` table links to the `department_id` in the `departments` table, creating a **one-to-many** relationship.

We'll explore more on types of relationships later in this lesson. 

### Next steps

Now that we understand the structure of relational databases and PostgreSQL, its time to start writing basic SQL queries to interact with our data!
