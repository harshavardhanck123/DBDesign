# Guvi Zen Class Database Design

## Introduction

The Guvi Zen Class project requires a database to manage various aspects of a learning management system, including students, instructors, courses, class sessions, assignments, grades, attendance, CodeKata exercises, topics, tasks, and company drives. The following document explains the database schema designed to fulfill these requirements.

## Entities and Attributes

### 1. Students
- **student_id**: Unique identifier for each student.
- **name**: The student's name.
- **email**: The student's email address.
- **phone_number**: The student's phone number.

### 2. Instructors
- **instructor_id**: Unique identifier for each instructor.
- **name**: The instructor's name.
- **email**: The instructor's email address.
- **phone_number**: The instructor's phone number.

### 3. Courses
- **course_id**: Unique identifier for each course.
- **title**: The title of the course.
- **description**: A brief description of the course.
- **instructor_id**: References the instructor teaching the course (Foreign Key).

### 4. Class Sessions
- **session_id**: Unique identifier for each class session.
- **course_id**: References the course being taught in this session (Foreign Key).
- **date**: The date of the class session.
- **time**: The time when the class session starts.
- **duration**: The duration of the class session in minutes.

### 5. Assignments
- **assignment_id**: Unique identifier for each assignment.
- **course_id**: References the course for which the assignment is given (Foreign Key).
- **title**: The title of the assignment.
- **description**: A brief description of the assignment.
- **due_date**: The due date for the assignment submission.

### 6. Grades
- **grade_id**: Unique identifier for each grade record.
- **student_id**: References the student who received the grade (Foreign Key).
- **assignment_id**: References the assignment for which the grade is given (Foreign Key).
- **grade**: The grade received by the student.

### 7. Attendance
- **attendance_id**: Unique identifier for each attendance record.
- **session_id**: References the class session (Foreign Key).
- **student_id**: References the student attending the session (Foreign Key).
- **status**: The attendance status (e.g., Present, Absent).

### 8. CodeKata
- **kata_id**: Unique identifier for each CodeKata exercise.
- **title**: The title of the CodeKata exercise.
- **description**: A brief description of the exercise.
- **difficulty_level**: The difficulty level of the exercise (e.g., Easy, Medium, Hard).

### 9. Topics
- **topic_id**: Unique identifier for each topic.
- **course_id**: References the course to which the topic belongs (Foreign Key).
- **title**: The title of the topic.
- **description**: A brief description of the topic.

### 10. Tasks
- **task_id**: Unique identifier for each task.
- **course_id**: References the course to which the task belongs (Foreign Key).
- **title**: The title of the task.
- **description**: A brief description of the task.
- **due_date**: The due date for the task completion.

### 11. Company Drives
- **drive_id**: Unique identifier for each company drive.
- **company_name**: The name of the company conducting the drive.
- **date**: The date of the drive.
- **time**: The time when the drive starts.
- **location**: The location where the drive is conducted.
- **eligibility_criteria**: The criteria for students to be eligible for the drive.

### 12. CodeKata_Grades
- **id**: Unique identifier for each CodeKata grade record.
- **student_id**: References the student who received the grade (Foreign Key).
- **kata_id**: References the CodeKata exercise (Foreign Key).
- **grade**: The grade received by the student for the CodeKata exercise.

## Relationships

1. **Instructors and Courses**: An instructor can teach multiple courses, establishing a one-to-many relationship.
2. **Courses and Class Sessions**: Each course can have multiple class sessions, forming a one-to-many relationship.
3. **Courses and Assignments**: Each course can have multiple assignments, forming a one-to-many relationship.
4. **Students and Grades**: A student can receive multiple grades, creating a one-to-many relationship.
5. **Assignments and Grades**: Each assignment can have multiple grades associated with it, forming a one-to-many relationship.
6. **Class Sessions and Attendance**: Each class session can have multiple attendance records, forming a one-to-many relationship.
7. **Students and Attendance**: Each student can have multiple attendance records, forming a one-to-many relationship.
8. **Courses and Topics**: Each course can have multiple topics, forming a one-to-many relationship.
9. **Courses and Tasks**: Each course can have multiple tasks, forming a one-to-many relationship.
10. **Courses and Company Drives**: Each course can have multiple company drives, forming a one-to-many relationship.
11. **Students and CodeKata**: Students can have multiple grades for different CodeKata exercises, creating a many-to-many relationship via the `CodeKata_Grades` table.
12. **CodeKata and CodeKata_Grades**: Each CodeKata exercise can have multiple grades associated with it, forming a one-to-many relationship.

## Summary

This database design effectively captures the necessary entities and their relationships for managing a learning management system. The tables and their relationships ensure data integrity and support the various functionalities required by the Guvi Zen Class project, including tracking students, instructors, courses, sessions, assignments, grades, attendance, CodeKata exercises, topics, tasks, and company drives.
