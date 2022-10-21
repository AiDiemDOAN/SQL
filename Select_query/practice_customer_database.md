# Manipulate the customer table
## The diagram
![image](https://user-images.githubusercontent.com/98060506/197299406-2be25fda-a475-405b-82cb-099a8d9dffb8.png)
***
### Question 1: Write a query to display all customers who are “Consumer”, their citys start with “a”, their citys end with "a", then display result by descending order of customer name
#### Input
```python
Select * 
From Customer 
where Segment = 'consumer'
and city like 'a%'
and State like '%a'
order by CustomerName desc
```
#### Output
![image](https://user-images.githubusercontent.com/98060506/197299842-e5e90b34-4f5e-47ef-b1dd-4dfd23ebac51.png)

***
### Question 2:Display all customers having CustomerName starting with  B and placed orders in December 2017. Display the result by descending order of Segment and then by ascending order of CustomerName
#### Input
```python
Select c.*
From Customer c join Orders o 
on c.ID = o.CustomerID
where c.CustomerName like 'B%' and 
month(o.OrderDate) = 12 and year(o.OrderDate) = 2017
order by c.Segment desc, c.CustomerName asc
```
#### Output
![image](https://user-images.githubusercontent.com/98060506/197300112-a59f29c6-a189-4146-ab57-727406fb51da.png)

***
### Question 3:Display SubcategoryID, SubCategoryName and the corresponding number of products in each sub-category having the number of products greater than 100, by descending order of NumberOfProducts
```python
Select p.SubCategoryID, s.SubCategoryName, count(p.id) as NumberOfProduct
from Product p join SubCategory s
on p.SubCategoryID = s.ID
group by p.SubCategoryID, s.SubCategoryName, SubCategoryID
Having count(p.id) > 100
Order by NumberOfProduct desc
```
#### Output
![image](https://user-images.githubusercontent.com/98060506/197300439-cbfaa9c8-60cf-49c7-b62a-a56e8c65232a.png)

***
### Question 4:Display ProducID, ProductName, and Quantity of all products, which have the highest Quantity in one order
```python
Select o.ProductID, p.ProductName, o.Quantity
from OrderDetails o join Product p
on o.ProductID = p.ID
where o.Quantity =
(select max(quantity) from OrderDetails)
```
#### Output
![image](https://user-images.githubusercontent.com/98060506/197300758-c9744ec6-f904-4f35-a162-e5aef69b7b83.png)

***
### Question 5:Display CustomerID, CustomerName and the number of orders of customers to have the highest number of orders
```python
With rs as
(Select o.CustomerID, c.CustomerName, count(o.id) as NumberOfOrder
from Orders o join Customer c
on o.CustomerID = c.ID
group by c.CustomerName, o.CustomerID)
Select * from rs
where rs.NumberOfOrder = 
(Select max(NumberOfOrder) from rs)
```
#### Output
![image](https://user-images.githubusercontent.com/98060506/197300943-2f30daa6-8d75-4715-959b-d258f9c86759.png)

***
### Question 6: Display 5 products with the highest unit prices and 5 products with the smallest unit prices 
```python
With rs as
(Select top 5 *
from Product
order by Unitprice desc
union
Select top 5 *
from Product
order by Unitprice asc)
select * from rs
order by rs.UnitPrice desc
```
#### Output
![image](https://user-images.githubusercontent.com/98060506/197301200-fc0e6ae7-6314-45a2-b7e5-74c635717e8e.png)






