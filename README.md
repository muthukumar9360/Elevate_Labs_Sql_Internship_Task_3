# 📌 SQL Developer Internship – Task 3
**Topic:** Writing Basic SELECT Queries  

---

## 🎯 Objective  
To practice extracting data from one or more tables using:
- `SELECT`
- `WHERE`
- `ORDER BY`
- `LIMIT`

This helps in understanding **Filtering, Projection, Sorting, and Aliasing**.

---

## 🛠 Tools Used  
- **MySQL Workbench** / **DB Browser for SQLite**  
- SQL Scripts  

---

## 🗄 Database Setup & Queries  

Below is the **complete SQL script** for this task.  

```sql
-- Step 1: Create Database
CREATE DATABASE Task3DB;
USE Task3DB;

-- Step 2: Create Tables
CREATE TABLE Students (
    student_id INT AUTO_INCREMENT PRIMARY KEY,
    name VARCHAR(100) NOT NULL,
    age INT,
    department VARCHAR(50),
    gpa DECIMAL(3,2)
);

CREATE TABLE Courses (
    course_id INT AUTO_INCREMENT PRIMARY KEY,
    course_name VARCHAR(100) NOT NULL,
    credits INT
);

CREATE TABLE Enrollments (
    enrollment_id INT AUTO_INCREMENT PRIMARY KEY,
    student_id INT,
    course_id INT,
    semester VARCHAR(10),
    grade CHAR(2),
    FOREIGN KEY (student_id) REFERENCES Students(student_id),
    FOREIGN KEY (course_id) REFERENCES Courses(course_id)
);

-- Step 3: Insert Sample Data
INSERT INTO Students (name, age, department, gpa) VALUES
('Alice Johnson', 20, 'Computer Science', 3.8),
('Bob Smith', 22, 'Mathematics', 3.4),
('Charlie Lee', 21, 'Physics', 3.2),
('David Kim', 23, 'Computer Science', 3.9),
('Eva Brown', 20, 'Mathematics', 3.6);

INSERT INTO Courses (course_name, credits) VALUES
('Database Systems', 3),
('Algorithms', 4),
('Linear Algebra', 3),
('Quantum Mechanics', 4);

INSERT INTO Enrollments (student_id, course_id, semester, grade) VALUES
(1, 1, 'Fall', 'A'),
(1, 2, 'Fall', 'B'),
(2, 3, 'Spring', 'A'),
(3, 4, 'Fall', 'C'),
(4, 1, 'Spring', 'A'),
(5, 2, 'Fall', 'B');

-- Step 4: Queries

-- 1. Select all columns from Students
SELECT * FROM Students;

-- 2. Select specific columns (name, gpa)
SELECT name, gpa FROM Students;

-- 3. Filtering with WHERE (CS students only)
SELECT * FROM Students WHERE department = 'Computer Science';

-- 4. Filtering with AND (Math students with GPA > 3.5)
SELECT * FROM Students 
WHERE department = 'Mathematics' AND gpa > 3.5;

-- 5. Using LIKE (names starting with 'A')
SELECT * FROM Students WHERE name LIKE 'A%';

-- 6. Using BETWEEN (students aged between 20 and 22)
SELECT * FROM Students WHERE age BETWEEN 20 AND 22;

-- 7. Sorting results by GPA (descending order)
SELECT * FROM Students ORDER BY gpa DESC;

-- 8. Limiting output (Top 3 students by GPA)
SELECT * FROM Students ORDER BY gpa DESC LIMIT 3;

-- 9. Using DISTINCT (unique departments)
SELECT DISTINCT department FROM Students;

-- 10. Aliasing (rename columns in output)
SELECT name AS StudentName, gpa AS GradePoint FROM Students;

📊 Expected Outputs
✅ Students Table (after inserting data)
student_id	name	age	department	gpa
1	Alice Johnson	20	Computer Science	3.8
2	Bob Smith	22	Mathematics	3.4
3	Charlie Lee	21	Physics	3.2
4	David Kim	23	Computer Science	3.9
5	Eva Brown	20	Mathematics	3.6

```
---

📸 Output Screenshots:  

![Output Screenshot](Outputs/output1.png)

---

