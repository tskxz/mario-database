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

There's two columns. You won't need either of them for the Mario database. Alter the table second_table and drop the column `username`.
> ALTER TABLE second_table DROP COLUMN username;

Next, drop the id column.
> ALTER TABLE second_table DROP COLUMN id;

Still two. You won't need either of those for the new database either. Drop second_table from your database. Here's an example:
```sql
DROP TABLE table_name;
```
> DROP TABLE second_table;

Next, drop first_table from the database.
> DROP TABLE first_table;

Rename first_database to mario_database. You can rename a database like this:
```sql
ALTER DATABASE database_name RENAME TO new_database_name;
```
> ALTER DATABASE first_database RENAME TO mario_database;

Now that you aren't connected to second_database, you can drop it. Use the `DROP DATABASE` keywords to do that.

> DROP DATABASE second_database;

Create a new table named characters, it will hold some basic information about Mario characters.

> CREATE TABLE characters();

Next, you can add some columns to the table. Add a column named character_id to your new table that is a type of SERIAL.
> ALTER TABLE characters ADD COLUMN character_id SERIAL;

The SERIAL type will make your column an INT with a NOT NULL constraint, and automatically increment the integer when a new row is added. View the details of the characters table to see what SERIAL did for you.
> /d characters

Add a column to characters called name. Give it a data type of VARCHAR(30), and a constraint of `NOT NULL`. Add a constraint by putting it right after the data type.
> ALTER TABLE characters ADD COLUMN name VARCHAR(30) NOT NULL;

You can make another column for where they are from. Add another column named homeland. Give it a data type of VARCHAR that has a max length of 60.
> ALTER TABLE characters ADD COLUMN homeland VARCHAR(60);


Video game characters are quite colorful. Add one more column named favorite_color. Make it a VARCHAR with a max length of 30.
> ALTER TABLE characters ADD COLUMN favorite_color VARCHAR(30);

You are ready to start adding some rows. First is Mario. Earlier, you used this command to add a row:
```sql
INSERT INTO second_table(id, username) VALUES(1, 'Samus');
```

The first parenthesis is for the column names, you can put as many columns as you want. The second parenthesis is for the values for those columns. Add a row to your table, give it a `name` of `Mario`, a `homeland` of `Mushroom Kingdom`, and a `favorite_color` of `Red`. Make sure to use single quotes where needed.

> INSERT INTO characters(character_id, name, homeland, favorite_color) VALUES (1, 'Mario', 'Mushroom Kingdom', 'Red');

Add another row for Luigi. Give it a name of Luigi, a homeland of Mushroom Kingdom, and a favorite_color of Green.
> INSERT INTO characters(character_id, name, homeland, favorite_color) VALUES (2, 'Luigi', 'Mushroom Kingdom', 'Green');

Add another row for Peach. Give her the values: Peach, Mushroom Kingdom, and Pink.
> INSERT INTO characters(character_id, name, homeland, favorite_color) VALUES (3, 'Peach', 'Mushroom Kingdom', 'Pink');

Adding rows one at a time is quite tedious. Here's an example of how you could have added the previous three rows at once:
```sql
INSERT INTO characters(name, homeland, favorite_color)
VALUES('Mario', 'Mushroom Kingdom', 'Red'),
('Luigi', 'Mushroom Kingdom', 'Green'),
('Peach', 'Mushroom Kingdom', 'Pink');
```
Add two more rows. Give the first one the values: Toadstool, Mushroom Kingdom, and Red. Give the second one: Bowser, Mushroom Kingdom, and Green. Try to add them with one command.
> INSERT INTO characters(character_id, name, homeland, favorite_color) VALUES (4, 'Toadstool', 'Mushroom Kingdom', 'Red'), (5, 'Bowser', 'Mushroom Kingdom', 'Green');

If you don't get a message after a command, it is likely incomplete. This is because you can put a command on multiple lines. Add two more rows. Give the first one the values: Daisy, Sarasaland, and Yellow. The second: Yoshi, Dinosaur Land, and Green. Try to do it with one command.
> INSERT INTO characters(character_id, name, homeland, favorite_color) VALUES (5, 'Daisy', 'Sarasaland', 'Yellow'), (6, 'Yoshi', 'Dinosaur Land', 'Green');

It looks good, but there's a few mistakes. You can change a value like this:

```sql
UPDATE table_name SET column_name=new_value WHERE condition;
```
You used username='Samus' as a condition earlier. SET Daisy's favorite_color to Orange. You can use the condition name='Daisy' to change her row.

> UPDATE characters SET favorite_color='Orange' WHERE name='Daisy';

Toadstool's name is wrong as well, it's actually Toad. Use UPDATE to SET his name to Toad. Use the condition favorite_color='Red'.
> UPDATE characters SET name='Toad' WHERE favorite_color='Red';

Using favorite_color='Red' was not a good idea. Mario's name changed to Toad because he likes red, and now there's two rows that are the same. Well, almost. Only the character_id is different. You will have to use that to change it back to Mario. Use UPDATE to set the name to Mario for the row with the lowest character_id
> UPDATE characters SET name='Mario' WHERE character_id = 1;

Toad's favorite color is wrong. He likes blue. Change Toad's favorite color to Blue. Use whatever condition you want, but don't change any of the other rows.
> UPDATE characters SET favorite_color='Blue' WHERE name='Toad';

Bowser's favorite_color is wrong. He likes Yellow. Why don't you update it without changing any of the other rows?
> UPDATE characters SET favorite_color='Yellow' WHERE name='Bowser';

Bowser's homeland is wrong as well. He's from the Koopa Kingdom. Why don't you change it to that without changing any other rows?
> UPDATE characters SET homeland='Koopa Kingdom' WHERE name='Bowser';


View all the data, but put it in order by character_id.
```sql
SELECT columns FROM table_name ORDER BY column_name;
```

> SELECT * FROM characters ORDER BY character_id;

It looks good. Next, you are going to add a primary key. It's a column that uniquely identifies each row in the table. Here's an example of how to set a PRIMARY KEY:
```sql
ALTER TABLE table_name ADD PRIMARY KEY(column_name);
```
The name column is pretty unique, why don't you set that as the primary key for this table.

> ALTER TABLE characters ADD PRIMARY KEY(name);

You can see the key for your name column at the bottom. It would have been better to use character_id for the primary key. Here's an example of how to drop a constraint:
```sql
ALTER TABLE table_name DROP CONSTRAINT constraint_name;
```
Drop the primary key on the name column. You can see the constraint name is characters_pkey.
ALTER TABLE characters DROP CONSTRAINT characters_pkey;

It's gone. Set the primary key again, but use the character_id column this time.
> ALTER TABLE characters ADD PRIMARY KEY(character_id);

The table looks complete for now. Next, create a new table named more_info for some extra info about the characters.
> CREATE TABLE more_info();

Add a column to your new table named more_info_id. Make it a type of SERIAL.
> ALTER TABLE more_info ADD COLUMN more_info_id SERIAL;

Set your new column as the primary key for this table.
> ALTER TABLE more_info ADD PRIMARY KEY(more_info_id);

Add another column to more_info named birthday. Give it a data type of DATE.
> ALTER TABLE more_info ADD COLUMN birthday DATE;

Add a height column to more_info that's a type of INT.
> ALTER TABLE more_info ADD COLUMN height INT;

Add a weight column. Give it a type of NUMERIC(4, 1). That data type is for decimals. NUMERIC(4, 1) has up to four digits and one of them has to be to the right of the decimal.
> ALTER TABLE more_info ADD COLUMN weight NUMERIC(4,1);

There’s your four columns and the primary key you created at the bottom. To know what row is for a character, you need to set a foreign key so you can relate rows from this table to rows from your characters table. Here's an example that creates a column as a foreign key:
```sql
ALTER TABLE table_name ADD COLUMN column_name DATATYPE REFERENCES referenced_table_name(referenced_column_name);
```
That's quite the command. In the more_info table, create a character_id column. Make it an INT and a foreign key that references the character_id column from the characters table. Good luck.

> ALTER TABLE more_info ADD COLUMN character_id INT REFERENCES characters(character_id);

There's your foreign key at the bottom. These tables have a "one-to-one" relationship. One row in the characters table will be related to exactly one row in more_info and vice versa. Enforce that by adding the UNIQUE constraint to your foreign key. Here's an example:
```sql
ALTER TABLE table_name ADD UNIQUE(column_name);
```
Add the UNIQUE constraint to the column you just added.

> ALTER TABLE more_info ADD UNIQUE(character_id);

The column should also be NOT NULL since you don't want to have a row that is for nobody. Here's an example:
```sql
ALTER TABLE table_name ALTER COLUMN column_name SET NOT NULL;
```
Add the NOT NULL constraint to your foreign key column.

```sql
ALTER TABLE more_info ALTER COLUMN character_id SET NOT NULL;
```

The structure is set, now you can add some rows. First, you need to know what character_id you need for the foreign key column. You have viewed all columns in a table with *. You can pick columns by putting in the column name instead of *. Use SELECT to view the character_id column from the characters table.
> SELECT character_id FROM characters;

That list of numbers doesn't really help. Use SELECT again to display both the character_id and name columns from the characters table. You can separate the column names with a comma to view both.
SELECT character_id, name FROM characters;



That's better. You can see Mario's id there. Here's some more info for him:

birthday	height	weight
1981-07-09	155	64.5

Add a row to more_info with the above data for Mario using the INSERT INTO and VALUES keywords. Be sure to set his character_id when adding him. Also, DATE values need a string with the format: 'YYYY-MM-DD'.
> INSERT INTO more_info (more_info_id, birthday, height, weight, character_id) VALUES (1, '1981-07-09', 155, 64.5, 1); 


You can see Luigi's id there. Here's his info:

birthday	height	weight
1983-07-14	175	48.8
Add a row in more_info for Luigi using the above info. Be sure to add his character_id as well.
> INSERT INTO more_info (more_info_id, birthday, height, weight, character_id) VALUES (2, '1983-07-14', 175, 48.8, 2); 


Here's the additional info for Peach:

birthday	height	weight
1985-10-18	173	52.2
Add a row for Peach using the above info. Be sure to add her character_id as well.

> INSERT INTO more_info (more_info_id, birthday, height, weight, character_id) VALUES (3, '1985-10-18', 173, 52.2, 3); 


Toad is next. Instead of viewing all the rows to find his id, you can just view his row with a WHERE condition. You used several earlier to delete and update rows. You can use it to view rows as well. Here's an example:
```sql
SELECT columns FROM table_name WHERE condition;
```
A condition you used before was username='Samus'. Find Toad's id by viewing the character_id and name columns from characters for only his row.

> SELECT character_id, name FROM characters WHERE name='Toad';


Here's what Toad's info looks like:

birthday	height	weight
1950-01-10	66	35.6
Add the above info for Toad. Be sure to add his character_id.

> INSERT INTO more_info (more_info_id, birthday, height, weight, character_id) VALUES (4, '1950-01-10', 66, 35.6, 4); 

Bowser is next. Find his id by viewing the character_id and name columns for only his row.
> SELECT character_id, name FROM characters WHERE name='Bowser';

Here's what Bowser's info looks like:

birthday	height	weight
1990-10-29	258	300
Add the above info for Bowser. Don't forget to add his character_id.

> INSERT INTO more_info (more_info_id, birthday, height, weight, character_id) VALUES (5, '1990-10-29', 258, 300, 5); 

Daisy is next. Find her id by viewing the character_id and name columns for only her row.
> SELECT character_id, name FROM characters WHERE name='Daisy';


The info for Daisy looks like this:

birthday	height	weight
1989-07-31	NULL	NULL
Add the above info for Daisy to more_info. Be sure to add her character_id as well. You can use NULL or simply not include the null columns when inserting.
> INSERT INTO more_info (more_info_id, birthday, height, weight, character_id) VALUES (6, '1989-07-31', NULL, NULL ,6); 

Yoshi is last. Find his id by viewing the character_id and name columns for only his row.
> SELECT character_id, name FROM characters WHERE name='Yoshi';

The info for Yoshi looks like this:

birthday	height	weight
1990-04-13	162	59.1
Add the above info for Yoshi to more_info. Be sure to include his character_id.
> INSERT INTO more_info (more_info_id, birthday, height, weight, character_id) VALUES (7, '1990-04-13', 162, 59.1 ,7); 

There is something you can do to help out though. What units do the height and weight columns use? It's centimeters and kilograms, but nobody will know. Rename the height column to height_in_cm.
> ALTER TABLE more_info RENAME COLUMN height TO height_in_cm;

Rename the weight column to weight_in_kg.
> ALTER TABLE more_info RENAME COLUMN weight TO weight_in_kg;

Next, you will make a sounds table that holds filenames of sounds the characters make. You created your other tables similar to this:
```sql
CREATE TABLE table_name();
```
Inside those parenthesis you can put columns for a table so you don't need to add them with a separate command, like this:
```
CREATE TABLE table_name(column_name DATATYPE CONSTRAINTS);
```
Create a new table named sounds. Give it a column named sound_id of type SERIAL and a constraint of PRIMARY KEY.
> CREATE TABLE sounds(sound_id SERIAL PRIMARY KEY);

Add a column to it named filename. Make it a VARCHAR that has a max length of 40 and with constraints of NOT NULL and UNIQUE. You can put those constraints at the end of the query to add them all.
> ALTER TABLE sounds ADD COLUMN filename VARCHAR(40) NOT NULL UNIQUE;

You want to use character_id as a foreign key again. This will be a "one-to-many" relationship because one character will have many sounds, but no sound will have more than one character. Here's the example again:
```sql
ALTER TABLE table_name ADD COLUMN column_name DATATYPE CONSTRAINT REFERENCES referenced_table_name(referenced_column_name);
```
Add a column to sounds named character_id. Give it the properties INT, NOT NULL, and set it as a foreign key that references character_id from characters
> ALTER TABLE sounds ADD COLUMN character_id INT NOT NULL REFERENCES characters(character_id);

The first file is named its-a-me.wav. Insert it into the sounds table with Mario's id as the character_id.
> INSERT INTO sounds (filename, character_id) VALUES ('its-a-me.wav', 1);

Add another row with a filename of yippee.wav. Use Mario's character_id again for the foreign key value.
> INSERT INTO sounds (filename, character_id) VALUES ('yippee.wav', 1);

Add another row to sounds for Luigi named ha-ha.wav. Use his character_id this time. Take a look at the data in characters to find his id if you need to.
> INSERT INTO sounds (filename, character_id) VALUES ('ha-ha.wav', 2);

Add another row with a filename of oh-yeah.wav. This one is for Luigi as well so use his character_id again.
> INSERT INTO sounds (filename, character_id) VALUES ('oh-yeah.wav', 2);

Add two more rows for Peach sounds. The filenames are yay.wav and woo-hoo.wav. Don't forget her character_id. Try to do it with one command.
> INSERT INTO sounds (filename, character_id) VALUES ('yay.wav', 3), ('woo-hoo.wav', 3);


Add two more rows. The filenames are mm-hmm.wav and yahoo.wav. The first one is for Peach again, the second is for Mario, so use the correct foreign key values. Try to do it with one command.
> INSERT INTO sounds (filename, character_id) VALUES ('mm-hmm.wav', 3), ('yahoo.wav', 1);

Create another new table called actions. Give it a column named action_id that's a type of SERIAL, and make it the PRIMARY KEY. Try to create the table and add the column with one command.
> CREATE TABLE actions (action_id SERIAL PRIMARY KEY);

Add a column named action to your new table. Give it a type of VARCHAR that is a max length of 20 and has UNIQUE and NOT NULL constraints.
> ALTER TABLE actions ADD COLUMN action VARCHAR(20) UNIQUE NOT NULL;

The actions table won't have any foreign keys. It's going to have a "many-to-many" relationship with the characters table. This is because many of the characters can perform many actions. You will see why you don't need a foreign key later. Insert a row into the actions table. Give it an action of run.
> INSERT INTO actions (action) VALUES ('run');

Insert another row into the actions table. Give it an action of jump
> INSERT INTO actions (action) VALUES ('jump');

Add another action row with an action of duck.
> INSERT INTO actions (action) VALUES ('duck');

Create a new table called character_actions. It will describe what actions each character can perform.
> CREATE TABLE character_actions();

Your junction table will use the primary keys from the characters and actions tables as foreign keys to create the relationship. Add a column named character_id to your junction table. Give it the type of INT and constraint of NOT NULL.
> ALTER TABLE character_actions ADD COLUMN character_id INT NOT NULL;

The foreign keys you set before were added when you created the column. You can set an existing column as a foreign key like this:
```sql
ALTER TABLE table_name ADD FOREIGN KEY(column_name) REFERENCES referenced_table(referenced_column);
```
Set the character_id column you just added as a foreign key that references the character_id from the characters table.
> ALTER TABLE character_actions ADD FOREIGN KEY(character_id) REFERENCES characters(character_id);

Add another column to character_actions named action_id. Give it a type of INT and constraint of NOT NULL.
> ALTER TABLE character_actions ADD COLUMN action_id INT NOT NULL;


This will be a foreign key as well. Set the action_id column you just added as a foreign key that references the action_id column from the actions table.
> ALTER TABLE character_actions ADD FOREIGN KEY(action_id) REFERENCES actions(action_id);


Every table should have a primary key. Your previous tables had a single column as a primary key. This one will be different. You can create a primary key from two columns, known as a composite primary key. Here's an example:
```sql
ALTER TABLE table_name ADD PRIMARY KEY(column1, column2);
```
Use character_id and action_id to create a composite primary key for this table.
> ALTER TABLE character_actions ADD PRIMARY KEY(character_id, action_id);

Insert three rows into character_actions for all the actions Yoshi can perform. He can perform all of them in the actions table. View the data in the characters and actions table to find the correct id's for the information.
> INSERT INTO character_actions (character_id, action_id) VALUES (7,2),(7,3),(7,4);


Add three more rows into character_actions for all of Daisy's actions. She can perform all of the actions, as well.
> INSERT INTO character_actions (character_id, action_id) VALUES (6,2),(6,3),(6,4);

Bowser can perform all the actions. Add three rows to the table for him.
> INSERT INTO character_actions (character_id, action_id) VALUES (5,2),(5,3),(5,4);

Next is Toad. Add three more rows for his actions.
> INSERT INTO character_actions (character_id, action_id) VALUES (4,2),(4,3),(4,4);

You guessed it. Peach can perform all the actions as well, so add three more rows for her.
> INSERT INTO character_actions (character_id, action_id) VALUES (3,2),(3,3),(3,4);

Add three more rows for Luigi's actions.
> INSERT INTO character_actions (character_id, action_id) VALUES (2,2),(2,3),(2,4);

Last is Mario, add three rows for his actions.
> INSERT INTO character_actions (character_id, action_id) VALUES (1,2),(1,3),(1,4);

That was a lot of work. View all the data in character_actions to see the rows you ended up with.
> SELECT * FROM character_actions;

You can see the character_id there so you just need to find the matching id in the characters table to find out who it's for. Or... You added that as a foreign key, that means you can get all the data from both tables with a JOIN command:
```sql
SELECT columns FROM table_1 FULL JOIN table_2 ON table_1.primary_key_column = table_2.foreign_key_column;
```
Enter a join command to see all the info from both tables. The two tables are characters and more_info. The columns are the character_id column from both tables since those are the linked keys.

> SELECT * from characters FULL JOIN more_info ON characters.character_id = more_info.character_id;

Now you can see all the info from both tables. If you recall, that's a "one-to-one" relationship. So there's one row in each table that matches a row from the other. Use another JOIN command to view the characters and sounds tables together. They both use the character_id column for their keys as well.
> SELECT * from characters FULL JOIN sounds ON characters.character_id = sounds.character_id;

This shows the "one-to-many" relationship. You can see that some of the characters have more than one row because they have many sounds. How can you see all the info from the characters, actions, and character_actions tables? Here's an example that joins three tables:
```SQL
SELECT columns FROM junction_table
FULL JOIN table_1 ON junction_table.foreign_key_column = table_1.primary_key_column
FULL JOIN table_2 ON junction_table.foreign_key_column = table_2.primary_key_column;
```
Congratulations on making it this far. This is the last step. View all the data from characters, actions, and character_actions by joining all three tables. When you see the data, be sure to check the "many-to_many" relationship. Many characters will have many actions.

> select * from character_actions FULL JOIN characters ON character_actions.character_id = characters.character_id FULL JOIN actions ON character_actions.action_id = actions.action_id;
