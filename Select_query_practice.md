# Manipulate the student table
## The diagram
![image](https://user-images.githubusercontent.com/98060506/197295046-1d05c06e-7e80-4237-b19b-c7cfc9bce6a0.png)
### Question 1: Select all male students
#### Input
```js
Select * from Student
where studentGender = 'true'
```
#### Output
![image](https://user-images.githubusercontent.com/98060506/197295653-25a3315e-8551-4af8-9772-8c557e96495b.png)

### Question 2: Select all students with average score of each student
#### Input
```js
select s.studentFName, s.studentLName, AVG(e.examscore) as avg_score
from Exam e join Student s
on e.studentID = s.studentID
group by s.studentFName, s.studentLName, e.studentID
```
#### Output
![image](https://user-images.githubusercontent.com/98060506/197295994-7b12dc26-f767-4d34-9a00-3ed674aa5052.png)

### Question 3: Select all students who have average score between 5 and 6
#### Input
```js
select s.studentFName, s.studentLName, AVG(e.examscore) as avg_score
from Exam e join Student s
on e.studentID = s.studentID
group by s.studentFName, s.studentLName, e.studentID
Having AVG(e.examscore) between 5 and 6
```
#### Output
![image](https://user-images.githubusercontent.com/98060506/197296134-37e4d332-6b80-436e-8f98-cda58e4ee668.png)

### Question 4: Count all students in each class
#### Input
```js
Select c.classCode, count(studentid) as number_student
from Student_Class sc right join class c
on sc.classCode = c.classCode
group by c.classCode
```
#### Output
![image](https://user-images.githubusercontent.com/98060506/197296253-cf440a98-b4dc-4944-a14c-960b4b60e315.png)
 ### Question 5: List all male students who are elder than 20
 #### Input
 ```js
 Select * from Student
Where (YEAR(getdate()) - YEAR(studentDOB))  > 20
and studentGender = 1
 ```
 #### Output
 ![image](https://user-images.githubusercontent.com/98060506/197296331-b5767e78-bcb2-434e-872f-06c270df597f.png)
### Question 6: List all students and their class name
