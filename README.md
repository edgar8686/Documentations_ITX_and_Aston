## ***Запросы SQL***
## ***Примеры работ***
___
### Aston QA Manual corse
+ [Ссылка на запросы 1](https://docs.google.com/document/d/1qgtsQADpiN2kTNGLhQNlOyX41pKlKYc0iVzsqbClBJE/edit?usp=sharing)
+ [Ссылка на таблицу](https://docs.google.com/spreadsheets/d/1ZUd4lX-wsgzd8rZbye36HBwY1hLvbyiPKsQLZMDhsjk/edit?usp=sharing)
___
**Запросы по заданию.**

Задание 1.
```sql
SELECT
number, (SELECT name FROM courses WHERE courses.id = streams.course_id) AS course_name,
number_of_students 
FROM streams
WHERE number_of_students >= 40;

number  course_name  number_of_students
------  -----------  ------------------
210     Базы данных  41



SELECT
(SELECT number FROM streams WHERE streams.id = grades.stream_id) AS number,
(SELECT name FROM courses WHERE courses.id = (SELECT course_id FROM streams WHERE streams.id = grades.stream_id)) AS course_name,
(SELECT name ||''|| surname FROM teachers WHERE teachers.id = grades.teacher_id) AS teacher,
grade
FROM grades
ORDER BY grade
LIMIT 2;

number  course_name             teacher          grade
------  ----------------------  ---------------  -----
165     Linux. Рабочая станция  ЕленаМалышева    4.7
203     Базы данных             НиколайСавельев  4.8



SELECT id FROM teachers WHERE surname = 'Савельев' AND name = 'Николай'
UNION
SELECT AVG(grade) FROM grades WHERE teacher_id = (SELECT teachers.id FROM teachers WHERE surname = 'Савельев' AND name = 'Николай');

id
----
1
4.85



SELECT id, name ||''|| surname FROM teachers WHERE  name = 'Наталья' AND surname = 'Петрова'
UNION
SELECT id, name ||''|| surname FROM teachers WHERE teachers.id = (SELECT teacher_id FROM grades WHERE grade < 4.8);

2|НатальяПетрова
3|ЕленаМалышева
```

Задание 2
```sql
SELECT
name, number_of_students, COUNT(number_of_students) OVER(PARTITION BY courses.id)
FROM courses
LEFT JOIN streams
ON course_id = courses.id;

Базы данных|35|2
Базы данных|41|2
Основы Python|37|1
Linux. Рабочая станция|34|1



SELECT
stream_id, name, AVG(grade) OVER(PARTITION BY teachers.id)
FROM teachers
LEFT JOIN grades
ON teachers.id = teacher_id;

3|Николай|4.85
4|Николай|4.85
2|Наталья|4.9


CREATE INDEXacademic_performance_performance_idx ON academic_performance(performance);
CREATE INDEX streams_number_idx ON streams(number) WHERE number >= 200;
```
Задание 3
```sql
SELECT number, name, started_at
FROM streams JOIN courses
ON course_id = courses.id;

165|Linux. Рабочая станция|2020-08-18
178|Основы Python|2020-10-02
203|Базы данных|2020-11-12
210|Базы данных|2020-12-03



SELECT name, number_of_students, SUM(number_of_students)
FROM courses
JOIN streams GROUP BY course_id;
name number_of_students SUM(number_of_students)

Базы данных 35 228
Базы данных 37 111
Базы данных 34 102



SELECT name, surname, teachers.id, AVG(grade)
FROM teachers LEFT JOIN grades
ON teachers.id = grades.stream_id
GROUP BY teachers.id;

name     surname   id  AVG(grade)
-------  --------  --  ----------
Николай  Савельев  1   4.7
Наталья  Петрова   2   4.9
Елена    Малышева  3   4.8
```
Задание 4.
```sql
CREATE VIEW teachers_info AS
SELECT courses.name, streams.started_at, AVG(grade), MAX(number), MAX(started_at)
FROM courses
LEFT JOIN streams
ON streams.id = course_id
LEFT JOIN grades
ON stream_id = streams.id
GROUP BY courses.id;

Базы данных|2020-10-02|4.9|178|2020-10-02
Основы Python|2020-10-02|4.9|178|2020-10-02
Linux. Рабочая станция|2020-10-02|4.9|178|2020-10-02



BEGIN TRANSACTION;
DELETE FROM grades WHERE teacher_id = 3;
DELETE FROM teachers WHERE teachers.id =3;
COMMIT;
SELECT * FROM teachers;

id  name     surname   email
--  -------  --------  -------------------
1   Николай  Савельев  saveliev.n@mai.ru
2   Наталья  Петрова   petrova.n@yandex.ru



CREATE TRIGGER check_grade_value BEFORE INSERT
ON grades
BEGIN
SELECT CASE
WHEN
NEW.grade NOT BETWEEN 0 AND 5
THEN
RAISE(ABORT, 'Wrong format for grade')
END;
END;
```