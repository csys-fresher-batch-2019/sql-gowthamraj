# Super Market Management

* http://supermarket.in

## Features
  * Login: Admin and employee 
  ```sql
create table login (user_name varchar2(50) not null,
passwords varchar2(50) not null,
constraint user_name_uq unique(user_name)
);
```
* insert Query:
```sql
insert into login (user_name,passwords)
values ('gowtham','raj');
insert into login (user_name,passwords)
values ('kennedy','kannan');
insert into login (user_name,passwords)
values ('mercy','grace');
```
* Display Query:
```sql
select * from login;
```
  ##Features II
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
* insert query:
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
*Display Query:
```sql
 select * from product;
```
##Features III
*product_Stock:display about the product(quantity,expiry_date)
  ```sql
create sequence pro_no start with 100 INCREMENT by 1;
create table product_stock (product_no number ,
stock_id number not null,
quantity number,
product_arrival timestamp default systimestamp not null,
expery_date date not null,
constraint product_no_pk primary key (product_no),
constraint stock_id_fk foreign key(stock_id) references product(product_id),
constraint expery_date_ck check (expery_date > product_arrival)
);
```

* insert query:
```sql
insert into product_stock (product_no,stock_id,quantity,expery_date)
values(pro_no.nextval,1, 59,'12-dec-2021');
insert into product_stock (product_no,stock_id,quantity,expery_date)
values(pro_no.nextval,2, 92,'12-feb-2021');
insert into product_stock (product_no,stock_id,quantity,expery_date)
values(pro_no.nextval,4, 89,'12-mar-2021');
insert into product_stock (product_no,stock_id,quantity,expery_date)
values(pro_no.nextval,3, 109,'12-apr-2021');
insert into product_stock (product_no,stock_id,quantity,expery_date)
values(pro_no.nextval,5, 19,'12-jun-2021');
```
* Display query:
```sql
select * from product_stock;
```
  ##Features IV
  *Customer_Card:add and display the regular customer details
  ```sql
create table customer_card(
Customer_name varchar2(40) not null,
mobile_number char(10) not null,
address varchar2(50),
constraint customer_name_uq unique(customer_name)
);
```
* insert query:
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
* Display query:
```sql
 select * from customer_card;
```
  ##Features V
  *bills:display and provide invoice bill to the customer
  ```sql
create table bills(bill_no number ,
customer_name varchar2(30)not null,
product_name VARCHAR2(35) not null,
quantity number not null,
price number not null,
total number not null,
constraint bill_no_pk primary key (bill_no),
constraint product_name_fk foreign key (product_name) references product(product_name)
);
```
* insert query
```sql
insert into bills(bill_no,customer_name,product_name,quantity,price,total)
values(1,'mani maran','dall',3,450,450);
insert into bills(bill_no,customer_name,product_name,quantity,price,total)
values(2,'gowtham','decoration',2,120,240);
insert into bills(bill_no,customer_name,product_name,quantity,price,total)
values(3,'shiva','stationary',3,12,36);
insert into bills(bill_no,customer_name,product_name,quantity,price,total)
values(4,'kannan','chocolate',3,450,450);
```
* Display query

```sql
select * from bills;
```
