# SQL Practice

## Create Table 

*The CREATE TABLE statement is used to create a new table in a database.
The column parameters specify the names of the columns of the table.
The datatype parameter specifies the type of data the column can hold (e.g. varchar, integer, date, etc.).*

### Student Table
```SQL
CREATE TABLE student(
id INTEGER PRIMARY KEY AUTO_INCREMENT,
first_name TEXT NOT NULL,
last_name  VARCHAR(45) NOT NULL,
dob DATE NOT NULL,
doj DATE NOT NULL,
STATUS BOOLEAN NOT NULL,
last_class CHAR(2) NULL);
 ```

### Course Table
```SQL
CREATE TABLE course(
id INTEGER ,
course_code TEXT NOT NULL,
description TEXT NULL
);
```
### Student_course Table 
```Sql
CREATE TABLE student_course(
id INTEGER AUTO_INCREMENT PRIMARY KEY,
id_student INTEGER NOT NULL ,
id_course  INTEGER NOT NULL,
marks FLOAT NOT NULL,
rank TEXT NULL,
CONSTRAINT fk_student FOREIGN KEY (id_student) REFERENCES student(id));
```
## ALTER TABLE 
### Alter Table / Add Constraint
```SQL
ALTER TABLE course
ADD CONSTRAINT pk_id PRIMARY KEY (id); 
```
### Alter Table / Drop Contraint
```SQL
ALTER TABLE course
DROP PRIMARY KEY ;
```

### ALTER TABLE / Add Primary Key
```SQL
ALTER TABLE course
ADD PRIMARY KEY (id); 
```

### ALTER TABLE / Modify Column
```SQL
ALTER TABLE course
MODIFY COLUMN id INTEGER AUTO_INCREMENT;
```
### ALTER TABLE / Add Foreign key
```SQL
ALTER TABLE student_course
ADD CONSTRAINT fk_course FOREIGN KEY(id_course) REFERENCES course(id);
```

### ALTER TABLE  / Reset Auto Increment
```SQL
ALTER TABLE student AUTO_INCREMENT =1;
```

## Insert Data 
### Insert INTO course
```SQL
# run 8 times
INSERT INTO course(course_code,description) VALUES ('Maths','Fun learn maths');
```

## DELETE RECORDS
### DELETE DATA with WITH COMMAND
**Check your result after every delete**
```SQL
DELETE FROM course WHERE id = 1 ; #delete id 1
DELETE FROM course WHERE id in (3,5) ; #delete id 3 & 5 
DELETE FROM course WHERE id < 3 ; # delete id 2
DELETE FROM course WHERE id > 3 AND id < 5 ; #delete id 4
DELETE FROM course WHERE id not in ( 7 ,8); # delete id 6
DELETE FROM course WHERE id != 7; # delete id 8 
DELETE FROM course; #delete id 7
```

### TRUNCATE student
```SQL
TRUNCATE student_course;
```

```SQL
ALTER TABLE course AUTO_INCREMENT =1;
```
## INSERT SAMPLE DATA
### INSERT DATA student
```SQL
INSERT INTO student(first_name,last_name,dob,doj,`status`)
VALUES ('David	','Lassli','1995-01-02','2020-04-05',1),
('Tom','Potter','1989-10-23','2020-05-10',1),
('Joy','Sam','2000-08-15','2020-07-11',1);
```

### INSERT DATA course
```SQL
INSERT INTO course(course_code,description)
VALUES('Eng-001','English literature'),
('Urdu-002','Urdu literature'),
('Math-003','Mathematics'),
('Physics','physiological'),
('IT','Information Technology');
```

### INSERT WITH SELECT
```SQL
INSERT INTO student_course
SELECT NULL,1,id,0.0,NULL FROM course;

INSERT INTO student_course
SELECT NULL,2,id,0.0,NULL FROM course WHERE id in (1,2,3);

INSERT INTO student_course
SELECT NULL,3,id,0.0,NULL FROM course  WHERE id NOT in (2,4);
```