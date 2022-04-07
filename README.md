<h1><strong>Cryptocurrency Transaction System</strong></h1>

<h2><strong>Abstract:</strong></h2>
<p>
This project is aimed at developing a system which helps in storing the details of a transaction which happens during a cryptocurrency transaction. With the rising interest of people towards the new and fascinating world of cryptocurrency, more and more technologies are being developed to keep this transaction safe, secure and error proof. The most advanced systems which handle these transactions implement a technology known as blockchain. Since this technology is beyond the scope of the project, we will try building a simple system using databases. The system will consist of various tables which will help in keeping records of the prices of the coins, the transaction log between different users, etc.
 <br>
The project will create multiple entities to demonstrate a smooth transaction between two individuals dealing in cryptocurrency. 
</p>

<h2><strong>ER-Diagram for the System:</strong></h2>

<img src="https://user-images.githubusercontent.com/72780341/162255056-048bd351-358a-4eec-b171-57475428d5fd.jpeg" alt="ER-Diagram">

<h2><strong>Creating Tables for the System:</strong></h2>
<p>Using the above ER-Diagram we will create the tables for the system.</p>
<p>The tables which will be created are:</p>
<ol>
 <li>
  <h3><strong>reg_org:</strong></h3>
  create table reg_org(<br>
    reg_id varchar(3),<br>
    reg_name varchar(50),<br>
    region varchar(50),<br>
    members varchar(50),<br>
    primary key(reg_id)<br>
);<br>
insert into reg_org values("R01","European Union","Europe","France,Germany,Spain,UK");<br>
insert into reg_org values("R02","SCO","Asia","India,China,Russia,Japan");<br>
insert into reg_org values("R03","NAFTA","North America","USA,Canada,Mexico");<br>
insert into reg_org values("R04","AFCFTA","Africa","Nigeria,Egypt,South Africa,Morocco");<br>
<br>
<img width="476" alt="image" src="https://user-images.githubusercontent.com/72780341/162257606-a1e8a31f-8bdf-4cd5-9882-8d8d33900985.png">
 </li>
 <li>
 <h3><strong>company:</strong></h3>
  create table company(<br>
    com_id varchar(5),<br>
    com_name varchar(30),<br>
    com_market varchar(30),<br>
    com_reg_id varchar(3),<br>
    primary key(com_id),<br>
    foreign key (com_reg_id) references reg_org(reg_id)<br> 
);<br>
insert into company values('COM01','Company A','India','R02');<br>
insert into company values('COM02','Company B','USA,Canada','R03');<br>
insert into company values('COM03','Company C','China,Japan,Russia','R02');<br>
insert into company values('COM04','Company D','Nigeria,Egypt','R04');<br>
insert into company values('COM05','Company E','France,Germany,UK','R01');<br>
 <br>
  <img width="383" alt="image" src="https://user-images.githubusercontent.com/72780341/162258049-e14b6c5a-5cb8-4568-992a-c5ef1f398567.png">
 </li>
 <li>
  <h3><strong>crypto:</strong></h3>
  create table crypto(<br>
    cid varchar(3),<br>
    crypto_name varchar(30),<br>
    volume long,<br>
    price float,<br>
    crypto_issuer varchar(5),<br>
    primary key(cid),<br>
    foreign key(crypto_issuer) references company(com_id)<br>
);<br>
insert into crypto values('C01','Bitcoin',200000,30000.0,'COM02');<br>
insert into crypto values('C02','Ethereum',500000,15000.0,'COM04');<br>
insert into crypto values('C03','Tether',20000,1000.0,'COM03');<br>
insert into crypto values('C04','Cardano',50000,3500.0,'COM01');<br>
insert into crypto values('C05','Dogecoin',180000,20000.0,'COM05');<br>
  <br>
  <img width="406" alt="image" src="https://user-images.githubusercontent.com/72780341/162258471-b23abf47-34b5-4dde-a1d6-c7b48c23df88.png">
 </li>
 <li>
  <h3><strong>traders:</strong></h3>
  create table traders(<br>
    tr_id varchar(3),<br>
    tr_name varchar(30),<br>
    tr_market varchar(30),<br>
    tr_reg_id varchar(3),<br>
    primary key(tr_id),<br>
    foreign key(tr_reg_id) references reg_org(reg_id)<br>
);<br>
insert into traders values('T01','Trader A','USA,Canada,Mexico','R03');<br>
insert into traders values('T02','Trader B','France,UK','R01');<br>
insert into traders values('T03','Trader C','India,China,Japan','R02');<br>
insert into traders values('T04','Trader D','Nigeria,Morocco','R04');<br>
insert into traders values('T05','Trader E','Russia,China','R02');<br>
<br>
  <img width="355" alt="image" src="https://user-images.githubusercontent.com/72780341/162258819-c3c58994-ef1a-42a2-9553-a4c72258a934.png">
 </li>
 <li>
  <h3><strong>platform:</strong></h3>
   create table platform(<br>
    plt_id varchar(3),<br>
    plt_name varchar(30),<br>
    plt_mode varchar(30),<br>
    plt_trd_id varchar(3),<br>
    primary key(plt_id),<br>
    foreign key(plt_trd_id) references traders(tr_id)<br>
);<br>
insert into platform values('P01','PLatform A','Website','T02');<br>
insert into platform values('P02','PLatform B','Smartphone Application','T03');<br>
insert into platform values('P03','PLatform C','Website','T01');<br>
insert into platform values('P04','PLatform D','Smartphone Application','T05');<br>
insert into platform values('P05','PLatform E','Smartphone Application','T04');<br>
<br>
   <img width="391" alt="image" src="https://user-images.githubusercontent.com/72780341/162259459-9f5e2211-2d1f-43ad-b942-0ce0c89a85d4.png">
 </li>
   <li>
    <h3><strong>client:</strong></h3>
    create table client(<br>
    cl_id varchar(4),<br>
    cl_name varchar(30),<br>
    cl_address varchar(50),<br>
    cl_plt_id varchar(3),<br>
    primary key(cl_id),<br>
    foreign key(cl_plt_id) references platform(plt_id)<br>
);<br>
insert into client values('CL01','Shivaansh','123,ABC Apartments,Chennai','P04');<br>
insert into client values('CL02','Rajesh','456,DEF Apartments,New Delhi','P01');<br>
insert into client values('CL03','Simran','789,GHI Apartments,Mumbai','P02');<br>
insert into client values('CL04','Ravi','101,JKL Apartments,Banglore','P03');<br>
insert into client values('CL05','Riya','110,MNO Apartments,Kochi','P04');<br>
insert into client values('CL06','Ruchika','120,PQR Apartments,Lucknow','P05');<br>
<br>
    <img width="422" alt="image" src="https://user-images.githubusercontent.com/72780341/162259724-41125212-31e1-4ab4-9fc5-ba436632dff2.png">
   </li>
   <li>
    <h3><strong>contract:</strong></h3>
    create table contract(<br>
    cont_id varchar(5),<br>
    crypto_id varchar(3),<br>
    buy_id varchar(4),<br>
    own_id varchar(4),<br>
    primary key(cont_id),<br>
    foreign key(crypto_id) references crypto(cid),<br>
    foreign key(buy_id) references client(cl_id),<br>
    foreign key(own_id) references client(cl_id)<br>
);<br>
insert into contract values('CNT01','C02','CL01','CL03');<br>
insert into contract values('CNT02','C01','CL02','CL04');<br>
insert into contract values('CNT03','C02','CL06','CL05');<br>
insert into contract values('CNT04','C04','CL01','CL02');<br>
insert into contract values('CNT05','C05','CL05','CL03');<br>
insert into contract values('CNT06','C03','CL04','CL06');<br>
insert into contract values('CNT07','C01','CL05','CL03');<br>
<br>
    <img width="286" alt="image" src="https://user-images.githubusercontent.com/72780341/162260017-9175992d-4157-4fe4-8344-16f78ceba285.png">
   </li>
</ol>
