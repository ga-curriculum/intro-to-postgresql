<h1>
  <span class="headline">Intro to PostgreSQL</span>
  <span class="subhead">Setup</span>
</h1>

## Setup

In this lesson, you will use your **Terminal application** to create and interact with a PostgreSQL database. You will use the `psql` command-line tool to interact with the database.

### Start the PostgreSQL command line (`psql`)

#### Mac/Linux users

Open your Terminal and use the command:

```bash
psql
```

#### Windows users (using git bash)

If you're using **Git Bash** or **PowerShell**, run:

```bash
psql -U <username> -h localhost
```

> **Windows users** may need to specify `-U <username>` to connect.

#### Expected output

You should see a prompt that looks like this:

```postgres
psql (16.2 (Homebrew))
Type "help" for help.

username=#
```

> The version number `(16.2 (Homebrew))` may be different on your machine.  
> You are in the **PostgreSQL command line tool** if you see your **username followed by `#`**.

#### Exit PostgreSQL

To close the PostgreSQL command-line tool, type:

```postgres
\q
```

Then press `Enter`.

### Optional setup instructions

If you would like to **save SQL commands for later**, follow these steps:

Navigate to your lessons directory:

```bash
cd ~/lessons
```

#### Create a new directory

Run the following commands to create and enter the **`intro-to-postgresql`** directory:

```bash
mkdir intro-to-postgresql
cd intro-to-postgresql
```

#### Create a SQL file

Run:

```bash
touch test-queries.sql
```

#### Open the directory in VS Code

Run:

```bash
code .
```

#### 📝 Notes

- You can add **comments** to your SQL file by prefixing them with `--`:

```sql
-- This is a comment in SQL
SELECT * FROM users;
```

- These comments **will not be executed** by PostgreSQL but can help you take notes!

Now you’re ready to start working with PostgreSQL! 🚀
