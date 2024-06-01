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