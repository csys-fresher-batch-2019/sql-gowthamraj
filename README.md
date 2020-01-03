# Super Market Management

## Features
  * Login: Admin and employee 
  ```sql
create table login (user_name varchar2(50) not null,
passwords varchar2(50) not null,
constraint user_name_uq unique(user_name)
);
```
* Adding  login user details:
```sql
insert into login (user_name,passwords)
values ('gowtham','raj');
insert into login (user_name,passwords)
values ('kennedy','kannan');
insert into login (user_name,passwords)
values ('mercy','grace');
```
* Verify the username and password :
```sql
select * from login where user_name ='gowtham' and passwords ='raj';
```
#### Table

| user_name | password |
|-----------|----------|
| gowtham   | raj      |
| kennedy   | kannan   |
| mercy     | grace    |



  ## Features II
  *Product Table:Display the product and price
```sql
create table product(product_id number ,
product_name varchar2(25) not null,
price number not null,
constraint product_id_pk1 primary key(product_id),
constraint product_name_uq1 unique(product_name),
constraint price_ck1 check(price >=1)
);
```
* Adding product details:
```sql
insert into product( product_id,product_name,price)
values(1,'dall',125);
insert into product( product_id,product_name,price)
values(2,'stationary',38);
insert into product( product_id,product_name,price)
values(3,'decoration',300);
insert into product( product_id,product_name,price)
values(4,'biscut',25);
insert into product( product_id,product_name,price)
values(5,'chocolate',99);
```
*Display the product:
```sql
 select * from product;
```
#### TABLES

| product_id | product_name | price |
|------------|--------------|-------|
| 1          | dall         | 125   |
| 2          | stationary   | 38    |
| 3          | decouration  | 300   |
| 4          | biscut       | 25    |
| 5          | chocolate    | 99    |


##Features III
*product_Stock:display about the product(quantity,expiry_date)
  ```sql
create sequence pro_no start with 100 INCREMENT by 1;
create table product_stock (product_no number ,
stock_id number not null,
quantity number,
product_arrival date not null,
expery_date date not null,
constraint product_no_pk primary key (product_no),
constraint stock_id_fk foreign key(stock_id) references product(product_id),
constraint expery_date_ck check (expery_date > product_arrival)
);
```

* Adding the product stock details:
```sql
insert into product_stock (product_no,stock_id,quantity,product_arrival,expery_date)
values(pro_no.nextval,1, 59,'10-jan-2019','12-dec-2021');
insert into product_stock (product_no,stock_id,quantity,product_arrival,expery_date)
values(pro_no.nextval,2, 92,'10-feb-2019','12-feb-2021');
insert into product_stock (product_no,stock_id,quantity,product_arrival,expery_date)
values(pro_no.nextval,4, 89,'10-mar-2019','12-mar-2021');
insert into product_stock (product_no,stock_id,quantity,product_arrival,expery_date)
values(pro_no.nextval,3, 109,'10-apr-2019','12-apr-2021');
insert into product_stock (product_no,stock_id,quantity,product_arrival,expery_date)
values(pro_no.nextval,5, 19,'10-jun-2019','12-jun-2021');
```
* Display the stocks:
```sql
select * from product_stock;
```
#### Tables


| product_no | stock_id | quantity | product_arriavl | expiry date |
|------------|----------|----------|-----------------|-------------|
| 1          | 1        | 59       | 10-jan-2019     | 12-dec-2021 |
| 2          | 2        | 92       | 10-feb-2019     | 12-feb-2021 |
| 3          | 4        | 89       | 10-mar-2019     | 12-mar-2021 |
| 4          | 3        | 109      | 10-apr-2019     | 12-apr-2021 |
| 5          | 5        | 19       | 10-jun-2019     | 12-jun-2021 |


##Features IV
  *Customer_Card:add and display the regular customer details
  ```sql
create table customer_card(
Customer_name varchar2(40) not null,
mobile_number char(10) not null,
address varchar2(50),
constraint customer_name_uq unique(customer_name),
constraint mobile_number_ck check(mobile_number >999999999 and mobile_number <10000000000)
);
```
* Adding the customer card holder details:
```sql
 insert into customer_card(customer_name,mobile_number,address)
 values('raj',8122688402,'2/2079 A Anna salai, Sivakasi');
  insert into customer_card(customer_name,mobile_number,address)
 values('kannan',9788941516,'28/3 mani nagar, Sivakasi');
 insert into customer_card(customer_name,mobile_number,address)
 values('kennedy',9952374336,'48/6 Babu nagar, Madurai');
 insert into customer_card(customer_name,mobile_number,address)
 values('Shiva',9791627426,'tuticori'); 
 insert into customer_card(customer_name,mobile_number,address)
 values('Mani Maran',7708164739, 'chennai');
```
* Display the customer card holder details:
```sql
 select * from customer_card;
```
#### Tables
| customer_name | mobile-number | address                       |
|---------------|---------------|-------------------------------|
| raj           | 8122688402    | 2/2079 A Anna salai, Sivakasi |
| kannan        | 9788941516    | 28/3 mani nagar, Sivakasi     |
| kennedy       | 9952374668    | 48/6 Babu nagar, Madurai      |
| shiva         | 9791627426    | tuticorin                     |
| mani maran    | 7708164739    | chennai                       |


  ## Features V
  *bills:display and provide invoice bill to the customer
  ```sql
create sequence bill_no_sq  start with 1  INCREMENT by 1;

create sequence cus_no_sq  start with 100  INCREMENT by 1;

create table bills(bill_no number ,
bill_date date not null,
cus_no number not null unique,
customer_name varchar2(30)not null,
product_name VARCHAR2(35) not null,
quantity number not null,
price number not null,
total number not null,
status varchar2(20) not null,
constraint bill_no_pk primary key (bill_no),
constraint product_name_fk foreign key (product_name) references product(product_name)
);

```
* Adding the billing details:
```sql
insert into bills(bill_no,bill_date,cus_no,customer_name,product_name,quantity,price,total,status)
values(bill_no_sq.nextval,'02-jan-2020',cus_no_sq.nextval,'mani maran','dall',3,450,450,'delivered');
insert into bills(bill_no,bill_date,cus_no,customer_name,product_name,quantity,price,total,status)
values(bill_no_sq.nextval,'02_jan_2020',cus_no_sq.nextval,'gowtham','decoration',2,120,240,'delivered');
insert into bills(bill_no,bill_date,cus_no,customer_name,product_name,quantity,price,total,status)
values(bill_no_sq.nextval,'01-jan-2020',cus_no_sq.nextval,'shiva','stationary',3,12,36,'delivered');
insert into bills(bill_no,bill_date,cus_no,customer_name,product_name,quantity,price,total,status)
values(bill_no_sq.nextval,'01-jan-2020',cus_no_sq.nextval,'kannan','chocolate',3,450,450,'delivered');
```
* Display the bills

```sql
select * from bills;
```
#### Table

|bill_no|bill_date |cus_no|customer_name | product_name | quantity | price | total |  status   |
|-------|----------|------|--------------|--------------|----------|-------|-------|-----------|
| 61    | 02-01-20 | 100  | mani maran   | dall         | 3        | 450   | 450   | delivered |
| 62    | 02-01-20 | 101  | gowtham      | decoration   | 2        | 120   | 240   | delivered |
| 63    | 01-01-20 | 102  | shiva        | stationary   | 3        | 12    | 36    | delivered |
| 64    | 01-01-20 | 103  | kannan       | chocolate    | 3        | 450   | 450   | delivered |

 # Features VI
   employee details: display the employee details.
```sql   
create sequence emp_idd start with 1 increment by 1;
create table employee(employee_id number not null,
employee_name varchar2(50) not null,
dob date not null,
doj date,
mobile_no number not null,
address varchar2(75) not null,
constraint employee_id_pk primary key (employee_id)
);
```
 * Adding the employee details
 ```sql
insert into employee(employee_id,employee_name,dob,doj,mobile_no,address)
values( emp_idd.nextval,'raj','12-jan-1982','02-feb-2018',9043023579,'rayapuram_peter');
insert into employee(employee_id,employee_name,dob,doj,mobile_no,address)
values( emp_idd.nextval,'peter','02-mar-1986','17-mar-2019',9043023579,'solinganallur');
insert into employee(employee_id,employee_name,dob,doj,mobile_no,address)
values( emp_idd.nextval,'philips','29-jun-1989','15-apr-2018',9043023579,'vandalur');
insert into employee(employee_id,employee_name,dob,doj,mobile_no,address)
values( emp_idd.nextval,'gowtham','09-sep-1989','02-dec-2017',9043023579,'goa');
```

* Display the employee details

```sql
select * from employee;
```
#### Table

| Employee_id | Employee_name | D.O.B     | D.O.J    | Mobile_no  | Address         |
|-------------|---------------|-----------|----------|------------|-----------------|
| 1           | raj           | 12-01-82  | 02-02-18 | 9043023579 | rayapuram_peter |
| 2           | peter         | 02-03-86  | 17-03-19 | 9043023579 | solinganallur   |
| 3           | philips       | 29-06-89  | 15-04-18 | 9043023579 | vandalur        |
| 4           | gowtham       | 09-09-89  | 02-12-17 | 9043023579 | goa             |


 # Feature VII
   * display the product price 100 and 250
     
     ```sql
     select * from product where price  between 100 and 250;
     ```
#### Table     
     
| Product_id | product_name | price |
|------------|--------------|-------|
| 1          | dall         | 125   |



# Feature VIII
 * display the customer card holder purchase details(sub query)

     ```sql
     select customer_name,
     (select product_name from bills where customer_name=c.customer_name )
     as customer_card_holder_purchase from customer_card c;
     ```
#### Table
| customer_name | customer_card_holder purchase_details |   
|---------------|---------------------------------------|
| raj           | (null)                                |
| kannan        | chocolate                             |
| kennedy       | (null)                                |
| shiva         | stationary                            |
| mani maran    | dall                                  |



# Features IX
 * display the quantity in ascending order for monitor the fast moving product
 
```sql
select p.product_no,p.stock_id,p.quantity 
from product_stock p
left JOIN bills o on p.quantity = o.quantity order by quantity asc;
```
#### Table

| product_no | stock_id | quantity |
|------------|----------|----------|
| 104        | 5        | 19       |
| 100        | 1        | 59       |
| 102        | 4        | 89       |
| 101        | 2        | 92       |
| 103        | 3        | 109      | 

# Features X
  * Employee count:
  ```sql
  
select count(*)  as employee_count from employee;
  ```
  #### Table
| Employee_count |
|----------------|
| 4              |    


# Features XI
 * calculate daily income
 ```sql
 select sum(total)as daily_income from bills;
```
#### Table

| Daily_income |
|--------------|
| 1176         | 

# Features XII
* calculate the income any date(functions)
```sql
CREATE OR REPLACE FUNCTION GET_TOTAL_AMOUNT( i_date DATE)  RETURN NUMBER AS 
v_total number;
BEGIN

select sum(total) INTO v_total from bills where bill_date ='02-jan-2020';
  RETURN v_total;
END GET_TOTAL_AMOUNT;
```

* display the income 
```sql
select GET_TOTAL_AMOUNT(SYSDATE)as income_on_date from dual;
```
#### Table

| Income_on_date | 
|----------------|
| 690            | 

# Features XIII
 * number of customer purchase on date
 ```sql
 select count(*) as number_of_customer,bill_date from bills group by bill_date;
 ```
 #### Table
| Number_of_customer | bill_date |
|--------------------|-----------|
| 2                  | 01-01-20  |
| 2                  | 02-01-20  |


# features XIV
 * which items did customer 101 purchase
 ```sql
select o.product_id,o.price,o.quantity from bill_order o where o.customer_no=101 ;  
```

#### Table
| Product_id  |price  |quantity| 
| 1           | 400   | 3      | 
| 1           | 300   | 4      | 

# Features XV
* calculate the bill amount of purchase product id=101
```sql
update bills set total=(select sum(price) from bill_order where customer_no=101) where cus_no=101;

select * from bills where cus_no=101;
```

#### Table

| bill_no | bill_date | cus_no | customer_name | total | status    |
|---------|-----------|--------|---------------|-------|-----------|
| 2       | 02-01-20  | 101    | gowtham       | 700   | delivered |
 
# Features XI
 *display the customer card holder purchase details(sub query)
```sql
select customer_name,
(select product_name from bills where customer_name=c.customer_name)as customer_card_holder_purchase from customer_card c;
select * from bills;
```

#### Table

| bill_no | bill_date | cus_no | customer_name | total |
|---------|-----------|--------|---------------|-------|
| 1       | 02-01-20  | 100    | mani maran    | 0     |
| 2       | 02-01-20  | 101    | gowtham       | 700   |
| 3       | 01-01-20  | 102    | shiva         | 0     |
| 4       | 01-01-20  | 103    | kannan        | 0     |
| 5       | 03-01-20  | 105    | rajan         | 0     |
