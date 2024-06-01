# mario-database
 
 The databases you see are there by default. You can make your own like this:

```sql
CREATE DATABASE database_name;
```

The capitalized words are keywords telling PostgreSQL what to do. The name of the database is the lowercase word. Note that all commands need a semi-colon at the end. Create a new database named first_database.

> CREATE DATABASE first_database;

Your new database is there. If you don't get a message after entering a command, it means it's incomplete and you likely forgot the semi-colon. You can just add it on the next line and press enter to finish the command. Create another database named second_database.

> CREATE DATABASE second_database;

You can connect to a database by entering \c database_name. You need to connect to add information. Connect to your second_database.

> \c second_database

Looks like there's no tables or relations yet. Similar to how you created a database, you can create a table like this:
```sql
CREATE TABLE table_name();
```
Note that the parenthesis are needed for this one. It will create the table in the database you are connected to. Create a table named first_table in second_database.

> CREATE TABLE first_table();

Create another new table in this database. Give it a name of second_table.

> CREATE TABLE second_table();

You can view more details about a table by adding the table name after the display command like this: `\d table_name`. View more details about your second_table.

> \d second_table

Tables need columns to describe the data in them, yours doesn't have any yet. Here's an example of how to add one:
```sql
ALTER TABLE table_name ADD COLUMN column_name DATATYPE;
```
Add a column to second_table named first_column. Give it a data type of INT. INT stands for integer. Don't forget the semi-colon. 😄

> ALTER TABLE second_table ADD COLUMN first_column INT;

Use ALTER TABLE and ADD COLUMN to add another column to second_table named id that's a type of INT.

> ALTER TABLE second_table ADD COLUMN id INT;

Add another column to second_table named age. Give it a data type of INT.
> ALTER TABLE second_table ADD COLUMN age INT;


Those are some good looking columns. You will probably need to know how to remove them. Here's an example:

```sql
ALTER TABLE table_name DROP COLUMN column_name;
```
Drop your age column.
> ALTER TABLE second_table DROP COLUMN age;

Use the ALTER TABLE and DROP COLUMN keywords again to drop first_column.
> ALTER TABLE second_table DROP COLUMN first_column;


A common data type is VARCHAR. It's a short string of characters. You need to give it a maximum length when using it like this: `VARCHAR(30).`

Add a new column to `second_table`, give it a name of name and a data type of `VARCHAR(30)`.

> ALTER TABLE second_table ADD COLUMN name VARCHAR(30);

The 30 means the data in it can be a max of 30 characters. You named that column name, it should have been username. Here's how you can rename a column:
```sql
ALTER TABLE table_name RENAME COLUMN column_name TO new_name;
```
Rename the name column to username.

> ALTER TABLE second_table RENAME COLUMN name TO username;

Rows are the actual data in the table. You can add one like this:
```sql
INSERT INTO table_name(column_1, column_2) VALUES(value1, value2);
```
Insert a row into second_table. Give it an id of 1, and a username of Samus. The username column expects a `VARCHAR`, so you need to put Samus in single quotes like this: `'Samus'`.
> INSERT INTO second_table(id, username) VALUES (1, 'Samus');


You should have one row in your table. You can view the data in a table by querying it with the SELECT statement. Here's how it looks:
```sql
SELECT columns FROM table_name;
```
Use a SELECT statement to view all the columns in second_table. Use an asterisk (*) to denote that you want to see all the columns.

> SELECT * FROM second_table;

There's your one row. Insert another row into second_table. Fill in the id and username columns with the values 2 and 'Mario'.

> INSERT INTO second_table(id, username) VALUES (2, 'Mario');

Insert another row into second_table. Use 3 as the id, and Luigi as the username this time.

> INSERT INTO second_table(id, username) VALUES (3, 'Luigi');


That gives me an idea 😃 You can make a database of Mario video game characters. You should start from scratch for it. Why don't you delete the record you just entered. Here's an example of how to delete a row:
```sql
DELETE FROM table_name WHERE condition;
```
Remove Luigi from your table. The condition you want to use is username='Luigi'.

> DELETE FROM second_table WHERE username='Luigi';

It's gone. You can scrap all this for the new database. Delete Mario from second_table using the same command as before, except make the condition username='Mario' this time.

> DELETE FROM second_table WHERE username='Mario';
Only one more row should remain. Delete Samus from second_table.

> DELETE FROM second_table WHERE username='Samus';
