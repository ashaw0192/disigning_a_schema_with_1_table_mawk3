Two Tables Design Recipe Template

1. Extract nouns from the user stories or specification

As a coach
So I can get to know all students
I want to see a list of students' names.

As a coach
So I can get to know all students
I want to see a list of cohorts' names.

As a coach
So I can get to know all students
I want to see a list of cohorts' starting dates.

As a coach
So I can get to know all students
I want to see a list of students' cohorts.

Nouns:
students, student names, cohort names, cohort starting dates, student cohorts

2. Infer the Table Name and Columns

Record - Properties
students - names, cohort
cohorts - names, start dates

Name of the first table (always plural): students

Column names: name, cohort

Name of the second table (always plural): cohorts

Column names: name, start date

3. Decide the column types.

Table: students
id: SERIAL
name: text
cohort: text

Table: cohorts
id: SERIAL
name: text
start_date date

4. Decide on The Tables Relationship

Can one [STUDENTS] have many [COHORTS]? NO
Can one [COHORTS] have many [STUDENTS]? YES
You'll then be able to say that:

[COHORTS] has many [STUDENTS]
And on the other side, [STUDENTS] belongs to [COHORTS]
In that case, the foreign key is in the table [STUDENTS]


4. Write the SQL.

-- EXAMPLE
-- file: students_table.sql

CREATE TABLE cohorts (
  id SERIAL PRIMARY KEY,
  name text,
  start_date date,
);

CREATE TABLE students (
  id SERIAL PRIMARY KEY,
  name text,
  cohort text,
  cohort_id int,
  constraint fk_cohort foreign key(cohort_id)
    references cohorts(id)
    on delete cascade
);
5. Create the tables.

psql -h 127.0.0.1 database_name < albums_table.sql
