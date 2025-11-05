
# 🧩 MongoDB Introduction & Database Relationships

## 🧠 What is MongoDB?

**MongoDB** is a **NoSQL (non-relational)** database.  
Unlike MySQL which stores data in **tables and rows**, MongoDB stores data in **collections and documents** — similar to **JSON objects** in JavaScript.  

It’s flexible, fast, and perfect for handling **unstructured** or **rapidly changing data**.

---

## 🏗️ Structure Overview

| SQL (MySQL) | MongoDB Equivalent |
|--------------|-------------------|
| Database | Database |
| Table | Collection |
| Row | Document |
| Column | Field |

---

## 💻 Example: MongoDB Document

```json
{
  "_id": 1,
  "name": "Anna Santos",
  "age": 21,
  "course": "Computer Science",
  "skills": ["HTML", "CSS", "JavaScript"]
}

📘 Explanation:

_id → automatically generated unique identifier

Fields (name, age, course) → like columns

skills → arrays or nested data are allowed



---

⚙️ Basic MongoDB Commands

🟢 Create (Insert)

db.students.insertOne({
  name: "Anna Santos",
  age: 21,
  course: "Computer Science"
});

🔍 Read (Find)

db.students.find();

✏️ Update

db.students.updateOne(
  { name: "Anna Santos" },
  { $set: { course: "Software Engineering" } }
);

❌ Delete

db.students.deleteOne({ name: "Anna Santos" });


---

🧠 Why Use MongoDB?

✅ Schema-less — no fixed structure
✅ Perfect for real-time apps like chat or analytics
✅ Scalable and flexible
✅ Easy to use for JSON-based applications


---

🔗 Relationships & Normalization

🧠 What Are Relationships?

Relationships define how data in one table (or collection) connects to another.
Example:
A student can enroll in many courses, and one teacher can teach many students.


---

🔗 Types of Relationships

Type	Example	Description

One-to-One	Each user has one profile	1 person → 1 ID card
One-to-Many	One teacher teaches many students	1 teacher → many students
Many-to-Many	Students can take many courses	many students ↔ many subjects



---

💻 Example in MySQL

One-to-Many (Teacher → Students):

CREATE TABLE teachers (
  teacher_id INT PRIMARY KEY,
  name VARCHAR(50)
);

CREATE TABLE students (
  student_id INT PRIMARY KEY,
  name VARCHAR(50),
  teacher_id INT,
  FOREIGN KEY (teacher_id) REFERENCES teachers(teacher_id)
);

📘 The FOREIGN KEY connects both tables.


---

💻 Example in MongoDB (Embedded Documents)

MongoDB doesn’t use JOIN — instead, you can embed related data directly.

db.teachers.insertOne({
  name: "Mr. Cruz",
  students: [
    { name: "Anna", age: 21 },
    { name: "Mark", age: 22 }
  ]
});

Each teacher document contains their students inside.
This is faster for reads and simple relationships.


---

🧠 What is Normalization?

Normalization means organizing data properly to reduce duplication and improve efficiency.
It keeps the database clean, fast, and consistent.


---

💡 Example (Without Normalization)

| id | student_name | course_name | teacher_name |
|----|---------------|--------------|---------------|
| 1 | Anna | Web Dev | Mr. Cruz |
| 2 | Mark | Web Dev | Mr. Cruz |

❌ “Mr. Cruz” is repeated — that wastes space and can cause inconsistencies.


---

💡 Example (With Normalization)

CREATE TABLE teachers (
  teacher_id INT PRIMARY KEY,
  name VARCHAR(50)
);

CREATE TABLE courses (
  course_id INT PRIMARY KEY,
  name VARCHAR(50),
  teacher_id INT
);

CREATE TABLE students (
  student_id INT PRIMARY KEY,
  name VARCHAR(50),
  course_id INT
);

✅ Data is now clean and organized using IDs instead of repeating names.


---

🔍 Levels of Normalization (Simplified)

Level	Meaning	Example

1NF	Each cell has one value only	No multiple data in one column
2NF	No partial dependency	Each field depends on the full key
3NF	No transitive dependency	Fields depend only on the key, not other fields



---

🧩 SQL vs NoSQL Summary

Concept	SQL	NoSQL (MongoDB)

Structure	Tables, Rows	Collections, Documents
Relationships	JOIN, Foreign Key	Embedded or Referenced
Schema	Fixed	Flexible
Normalization	Strong	Often denormalized
Scaling	Vertical (add power)	Horizontal (add servers)



---

🧠 Easy Analogy

SQL → Like a filing cabinet with labeled folders (organized, structured).

MongoDB → Like a big box of labeled envelopes (flexible and quick).



---

🧾 Summary

MongoDB stores data as JSON documents.

Relationships define how data connects between entities.

Normalization keeps data clean and avoids duplication.

Both SQL and NoSQL are powerful — you choose based on your app’s needs.



---
