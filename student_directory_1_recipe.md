Single Table Design Recipe Template

Copy this recipe template to design and create a database table from a specification.

1. Extract nouns from the user stories or specification

As a coach
So I can get to know all students
I want to see a list of students' names.

As a coach
So I can get to know all students
I want to see a list of students' cohorts.

students, names, cohorts

2. Infer the Table Name and Columns

Put the different nouns in this table. Replace the example with your own nouns.

Record - Properties
student - name, cohort

Name of the table (always plural): students

Column names: name, cohort

3. Decide the column types.

id: SERIAL
name: text
cohort: text

4. Write the SQL.

-- file: students_table.sql

CREATE TABLE students (
  id SERIAL PRIMARY KEY,
  name text,
  cohort text
);
5. Create the table.

psql -h 127.0.0.1 database_name < albums_table.sql
