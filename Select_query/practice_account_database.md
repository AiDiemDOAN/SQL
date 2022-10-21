# Manipulate the student table
## The diagram
![image](https://user-images.githubusercontent.com/98060506/197301983-f9c82821-f88f-4d81-b688-731a47a5f062.png)

***
### Question 1: Count number of all business customer
#### Input
```python
Select count(*) as total
From CUSTOMER
Where CUST_TYPE_CD = 'B'
group by CUST_TYPE_CD
```
#### Output
![image](https://user-images.githubusercontent.com/98060506/197302552-1eca7bf5-3755-41ec-a10d-3e45750923f1.png)

***
### Question 2: Select all accounts which have Avail_balance different pending_balance
#### Input
```python
Select *
From ACCOUNT
Where AVAIL_BALANCE != PENDING_BALANCE
```
#### Output
![image](https://user-images.githubusercontent.com/98060506/197302762-66771443-bed2-4d0e-bb42-160faf9f5f52.png)

***
### Question 3: Select all customers
#### Input
```python
Select C.CUST_ID, C.CUST_TYPE_CD, (I.FIRST_NAME + I.LAST_NAME) as Name
From INDIVIDUAL I join CUSTOMER C
on I.CUST_ID = C.CUST_ID
union
Select C.CUST_ID, C.CUST_TYPE_CD, b.NAME as Name
From BUSINESS B join CUSTOMER C
on b.CUST_ID = C.CUST_ID
```
#### Output
![image](https://user-images.githubusercontent.com/98060506/197302862-141a59b6-816b-4f9b-adf6-ad2a346203ac.png)

***
### Question 4: Count all accounts of each employee
#### Input
```python
Select e.EMP_ID, (e.FIRST_NAME + e.LAST_NAME) as Name, count(a.account_ID) as number
From ACCOUNT a right join EMPLOYEE e
on a.OPEN_EMP_ID = e.EMP_ID
Group by e.EMP_ID, e.FIRST_NAME, e.LAST_NAME
```
#### Output
![image](https://user-images.githubusercontent.com/98060506/197302914-3b35c324-cc62-4b48-a6ec-60b473c1190e.png)

***
### Question 5: List all accounts which have 1 Customer
#### Input
```python
Select CUST_ID
From ACCOUNT
Group by CUST_ID	
Having count(account_id) = 1
```
#### Output
![image](https://user-images.githubusercontent.com/98060506/197302985-96a5bb40-8275-4725-ba80-cfde2246200a.png)




