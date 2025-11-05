

🗄️ MySQL Basics — CRUD Operations for Beginners


---

🧠 What is MySQL?

MySQL is one of the most popular SQL (Structured Query Language) databases.
It’s used to store and manage data in rows and columns — just like a spreadsheet.

Think of it as the brain of your app that keeps all user data safe and organized.


---

⚙️ What is CRUD?

CRUD stands for:

Create → add new data

Read → get data

Update → modify existing data

Delete → remove data


Every database app (like Facebook, YouTube, or Shopee) does these four things!


---

💻 Step 1: Create a Database

CREATE DATABASE school;
USE school;

This creates a new database named school and tells MySQL to use it.


---

💻 Step 2: Create a Table

CREATE TABLE students (
  id INT AUTO_INCREMENT PRIMARY KEY,
  name VARCHAR(100),
  age INT,
  course VARCHAR(100)
);

📘 Explanation:

id — unique number for each student

AUTO_INCREMENT — adds +1 automatically for each new student

PRIMARY KEY — makes id the unique identifier

VARCHAR — stores text (letters, names, etc.)

INT — stores numbers



---

🧱 Step 3: CREATE — Insert Data

INSERT INTO students (name, age, course)
VALUES 
('Anna Santos', 21, 'Computer Science'),
('Mark Dela Cruz', 22, 'Information Technology');

✅ This adds two students into your table.


---

🔍 Step 4: READ — View Data

SELECT * FROM students;

📘 Explanation:

SELECT * means “get everything.”

You’ll see: | id | name | age | course | |----|------|-----|---------| | 1 | Anna Santos | 21 | Computer Science | | 2 | Mark Dela Cruz | 22 | Information Technology |


💡 You can also filter:

SELECT * FROM students WHERE course = 'Computer Science';


---

✏️ Step 5: UPDATE — Modify Data

UPDATE students
SET course = 'Software Engineering'
WHERE id = 1;

📘 Explanation:

SET changes values

WHERE makes sure you only update one specific student
✅ Always include a WHERE clause — otherwise you’ll update everyone by mistake!



---

🗑️ Step 6: DELETE — Remove Data

DELETE FROM students
WHERE id = 2;

📘 Explanation:

Removes only the record with id = 2.
⚠️ If you forget WHERE, it deletes all rows in your table!



---

🧩 Quick Summary

Action	SQL Command	Description

Create	INSERT INTO	Adds new data
Read	SELECT	Retrieves data
Update	UPDATE	Changes existing data
Delete	DELETE	Removes data



---

💡 Practice Task

Try these:

1. Add 3 more students


2. View only students under age 22


3. Update a student’s course


4. Delete one record


