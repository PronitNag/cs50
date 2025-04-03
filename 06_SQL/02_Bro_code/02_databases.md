# How to create, alter and Drop a database?

```text
First think --> what is a database exactly??
Think of it as a folder 
it acts as a container,
 tables on the other 
hand would be the files found within the 
folder in this topic I'm going to show you 
how we can create the database 
itself  
```

# Database Operations in SQL

## 1. Create a Database

Database banane ke liye `CREATE DATABASE` ka use hota hai:

```sql
CREATE DATABASE myDatabase;
```

Agar aapko check karna ho ki database already exist karta hai ya nahi, toh `IF NOT EXISTS` ka use karein:

```sql
CREATE DATABASE IF NOT EXISTS myDatabase;
```

## 2. Alter a Database

Agar aapko database ka naam change karna hai toh `ALTER DATABASE` ka use karein (Note: Har RDBMS me ye command support nahi karti):

```sql
ALTER DATABASE myDatabase MODIFY NAME = newDatabase;
```

Lekin MySQL me direct rename nahi hota, uske liye naye database me tables copy karni padengi.

## 3. Drop a Database

Agar kisi database ko permanently delete karna hai toh `DROP DATABASE` ka use karein:

```sql
DROP DATABASE myDatabase;
```

Agar sure karna ho ki database exist karta hai tabhi delete ho, toh `IF EXISTS` ka use karein:

```sql
DROP DATABASE IF EXISTS myDatabase;
```

Isse poora database delete ho jayega, saari tables aur data bhi remove ho jayega, toh dhyan se use karein!
