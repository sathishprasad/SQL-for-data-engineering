# SQL Building Blocks
## Basic commands
### 1. SELECT
In SQL, the SELECT statement is used to retrieve data from one or more tables in a database. It is one of the fundamental SQL commands and is often the first step in querying and analyzing data. Here's a basic syntax of the SELECT statement:
<br>
```(sql)
SELECT column1, column2, ...
FROM table_name;
```
To select all columns in a table, simply use '*' symbol
```sql
SELECT * FROM table_name;
```
### 2. WHERE
In SQL, the WHERE clause is used to filter rows from a table based on a specified condition. It allows you to retrieve only the rows that meet the specified criteria. Here is the basic syntax of the WHERE clause in a SELECT statement:
```sql
//example 1
SELECT * FROM table_name
WHERE col_name = 'value';

//example 2
SELECT * FROM table_name
WHERE col_name > value;
```
## Data Types

### Numeric Data Types

Numeric data types are employed for the storage of various numbers, each with distinct size and precision specifications.

- __smallint:__ Designed for the storage of small integers within the range of -32768 to +32767.
- __integer:__ Intended for the storage of whole numbers up to 2^31.
- __bigint:__ Utilized for the storage of large integers spanning from -2^63 to 2^63-1.
- __decimal:__ Tailored for numbers with decimal points, capable of accommodating up to 131,072 digits preceding the decimal point and up to 16,384 digits following it.
- __numeric:__ Suited for numbers with decimal points, having a capacity of up to 131,072 digits before the decimal point and up to 16,384 digits after it.
- __real:__ Designed for the storage of floating-point numbers with a precision of 6 decimal digits.
- __double precision:__ Configured for the storage of floating-point numbers with a precision of 15 decimal digits.

### Example SQL query using Numeric Data Types

Suppose we want to store the total amount spent by a customer on a particular transaction. We can use the `decimal` data type to store the transaction amount with two decimal places:

```sql
CREATE TABLE temperature_logs (
    id integer,
    timestamp timestamp,
    temperature_celsius real
);

INSERT INTO temperature_logs (id, timestamp, temperature_celsius)
VALUES (1, '2022-01-01 12:00:00', 25.5);

```

## Character Data Types

Character data types are used to store textual data of different lengths.

- `char`: Used to store fixed-length strings up to a maximum of 255 characters.
- `varchar`: Used to store variable-length strings up to a maximum of 1GB.
- `text`: Used to store variable-length strings up to a maximum of 1GB.

### Example SQL query using Character Data Types

Suppose we want to store a customer's name in a database. We can use the `varchar` data type to store the name:

```sql
CREATE TABLE customers (
    id integer,
    name varchar(255),
    email varchar(255)
);

INSERT INTO customers (id, name, email)
VALUES (123, 'John Smith', 'john.smith@example.com');

```

## Date/Time Data Types

Date/time data types are used to store date and time values and perform various operations on them.

- `date`: Used to store dates ranging from 4713 BC to 5874897 AD.
- `time`: Used to store time values with up to 6 decimal digits of precision.
- `timestamp`: Used to store date and time values with up to 6 decimal digits of precision.
- `interval`: Used to store time intervals ranging from -178000000 years to 178000000 years.

### Example SQL query using Date/Time Data Types

Suppose we want to store a customer's date of birth in a database. We can use the `date` data type to store the date:

```sql
CREATE TABLE customers (
    id integer,
    name varchar(255),
    email varchar(255),
    date_of_birth date
);

INSERT INTO customers (id, name, email, date_of_birth)
VALUES (123, 'John Smith', 'john.smith@example.com', '1990-01-01');

```
## Boolean Data Type

Boolean data type is used to store true or false values.

- `boolean`: Used to store true or false values.

### Example SQL query using Boolean Data Type
Suppose we want to store whether a customer has opted in for marketing emails. We can use the `boolean` data type to store the value:
```sql
CREATE TABLE customers (
    id integer,
    name varchar(255),
    email varchar(255),
    opted_in_for_emails boolean
);

INSERT INTO customers (id, name, email, opted_in_for_emails)
VALUES (123, 'John Smith', 'john.smith@example.com', true);
```
