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

<h2><strong>Various Commands performed on the Tables:</strong></h2>
<p>The different types of commands executed on the tables are listed here.</p>
<ol>
 <li>
  <h3><strong>Basic Select Commands:</strong></h3>
  <ul>
   <li>
   select crypto_name,price from crypto;
    <br>
    <br>
    <img width="164" alt="image" src="https://user-images.githubusercontent.com/72780341/162261365-e3f66678-73d5-4d97-bddd-74ef50c398df.png">
   </li>
   <li>
   select * from crypto where volume>100000;
    <br><br>
    <img width="391" alt="image" src="https://user-images.githubusercontent.com/72780341/162261623-289fde82-9ab4-4325-beb4-fd57ae8bf094.png">
   </li>
   <li>
   select cid,crypto_name,price from crypto order by price ASC;
    <br><br>
    <img width="227" alt="image" src="https://user-images.githubusercontent.com/72780341/162261788-1bda0897-debd-40b9-b7bd-30025e1e6da3.png">
   </li>
   <li>
   select com_name as Company from company where com_id='COM02';
    <br><br>
    <img width="91" alt="image" src="https://user-images.githubusercontent.com/72780341/162261913-29abd5d4-1b9e-4621-94c1-5f6d175150bb.png">
   </li>
   <li>
   select cont_id as Contract from contract where buy_id='CL01' and own_id='CL02';
    <br><br>
    <img width="100" alt="image" src="https://user-images.githubusercontent.com/72780341/162262052-f11083d5-e70b-4c1b-9957-d7ce952ecb6f.png">
   </li>
   <li>
   select distinct(cid) from crypto;
    <br><br>
    <img width="74" alt="image" src="https://user-images.githubusercontent.com/72780341/162262184-a2be9a85-7c10-4bcd-8e93-5795320d921f.png">
   </li>
  </ul>
 </li>
 <li>
 <h3><strong>Select Commands using In-Built Functions:</strong></h3>
  <ul>
   <li>
   select sum(price) from crypto;
    <br><br>
    <img width="79" alt="image" src="https://user-images.githubusercontent.com/72780341/162262492-af71c2ab-2804-4c58-8c19-50be208357e6.png">
   </li>
   <li>
   select count(*) from client;
    <br><br>
    <img width="66" alt="image" src="https://user-images.githubusercontent.com/72780341/162262644-8a3933e1-2be2-4a51-90d9-b24c55eae1a8.png">
   </li>
   <li>
   select count(*) from reg_org;
    <br><br>
    <img width="76" alt="image" src="https://user-images.githubusercontent.com/72780341/162262803-62cf8244-8831-407c-a676-23a19de7a734.png">
   </li>
   <li>
   select upper(cl_name) from client;
    <br><br>
    <img width="91" alt="image" src="https://user-images.githubusercontent.com/72780341/162262934-8bc830ac-860f-44d1-ab46-69b00303c767.png">
   </li>
   <li>
   select LOWER(cl_name) from client;
    <br><br>
    <img width="92" alt="image" src="https://user-images.githubusercontent.com/72780341/162263087-0c6fbeb8-4216-4400-aa99-ba45853b5e29.png">
   </li>
   <li>
   select round(price,2) from crypto;
    <br><br>
    <img width="89" alt="image" src="https://user-images.githubusercontent.com/72780341/162263280-246f0c62-63e9-4716-9af2-02b5dedb3ac4.png">
   </li>
   <li>
   select max(price) from crypto;
    <br><br>
    <img width="70" alt="image" src="https://user-images.githubusercontent.com/72780341/162263451-751ed9a8-4e6c-4646-9a50-547a0f66974a.png">
   </li>
   <li>
   select min(volume) from crypto;
    <br><br>
    <img width="86" alt="image" src="https://user-images.githubusercontent.com/72780341/162263615-96a77dd1-6f72-465c-8eea-f398fd48e2b1.png">
   </li>
  </ul>
 </li>
 <li>
 <h3><strong>Select Commands using Wildcard Characters:</strong></h3>
  <ul>
   <li>
   select reg_name from reg_org where reg_name like 'E%';
    <br><br>
    <img width="96" alt="image" src="https://user-images.githubusercontent.com/72780341/162265523-421e4bce-6bf7-4aea-a619-01634d8d96e3.png">
   </li>
   <li>
   select reg_name from reg_org where reg_name like '__O';
    <br><br>
    <img width="84" alt="image" src="https://user-images.githubusercontent.com/72780341/162265645-43140f38-be51-4be6-bd7b-c04f94f24564.png">
   </li>
   <li>
   select members from reg_org where members like 'India,%';
    <br><br>
    <img width="129" alt="image" src="https://user-images.githubusercontent.com/72780341/162265769-4ea452de-1de0-4314-bffb-7e54449fa2c2.png">
   </li>
   <li>
   select tr_market from traders where tr_market like '%Mexico';
    <br><br>
    <img width="114" alt="image" src="https://user-images.githubusercontent.com/72780341/162265875-23751260-6825-46f8-bccd-3edf9bdedd1e.png">
   </li>
  </ul>
 </li>
 <li>
 <h3><strong>Sub-Queries & Nested-Queries:</strong></h3>
  <ul>
   <li>
   select cont_id from contract where crypto_id in (
    select cid from crypto where cid='C01'
);
    <br><br>
    <img width="80" alt="image" src="https://user-images.githubusercontent.com/72780341/162266236-d2c4083b-ab15-48b8-b35c-1ac984c866d3.png">
   </li>
   <li>
   select com_name from company where com_reg_id in(
    select reg_id from reg_org where region in ('Europe','Asia')
);
    <br><br>
    <img width="76" alt="image" src="https://user-images.githubusercontent.com/72780341/162266343-b4ff41d7-6831-4a97-be56-a13c3c48b1b7.png">
   </li>
   <li>
   select tr_name from traders where tr_reg_id in (
    select com_reg_id from company where com_reg_id in(
        select reg_id from reg_org where region in ('North America','Africa','Asia')
    )
);
    <br><br>
    <img width="70" alt="image" src="https://user-images.githubusercontent.com/72780341/162266467-724ac322-a9ce-461f-9db0-d152392b23b0.png">
   </li>
  </ul>
 </li>
 <li>
 <h3><strong>Set-Operation Commands:</strong></h3>
  <ul>
   <li>
   select reg_id from reg_org union select com_reg_id from company;<br><br>
    <img width="59" alt="image" src="https://user-images.githubusercontent.com/72780341/162266741-47199d23-6ea0-4429-b159-e923239171f9.png">
   </li>
   <li>
   select reg_id from reg_org union all select com_reg_id from company;<br><br>
    <img width="79" alt="image" src="https://user-images.githubusercontent.com/72780341/162266864-cbaf60f3-91bd-4efa-a2fb-c24513d30ef6.png">
   </li>
  </ul>
 </li>
 <li>
 <h3><strong>Views:</strong></h3>
  <ul>
   <li>
   create view view1 as select * from crypto where volume>150000;
    select * from view1;
    <br><br>
    <img width="403" alt="image" src="https://user-images.githubusercontent.com/72780341/162267179-908bcf61-b635-4596-a0e9-45a79e247a17.png">
   </li>
   <li>
   select crypto_name as Name,volume from view1 where price>18000;<br><br>
    <img width="158" alt="image" src="https://user-images.githubusercontent.com/72780341/162267327-f69c9497-0bfc-40d0-bd70-9ef89ed77aed.png">
   </li>
   <li>
   drop view view1;
    select * from view1;<br><br>
    <img width="191" alt="image" src="https://user-images.githubusercontent.com/72780341/162267528-8a189822-b239-4cf2-bebe-aa47103cf7d7.png">
   </li>
  </ul>
 </li>
 <li>
 <h3><strong>Joins:</strong></h3>
  <ul>
   <li>
   select company.com_id,company.com_name,reg_org.reg_name from company 
inner join reg_org on company.com_reg_id=reg_org.reg_id;<br><br>
    <img width="268" alt="image" src="https://user-images.githubusercontent.com/72780341/162396843-4a4e7a32-3eaf-4010-8c97-767ff600466e.png">
   </li>
   <li>
   select client.cl_id, client.cl_name,platform.plt_name from client
left join platform on client.cl_plt_id=platform.plt_id;<br><br>
    <img width="238" alt="image" src="https://user-images.githubusercontent.com/72780341/162397094-8000e25d-e08b-46c6-9b55-0e872714b527.png">
   </li>
   <li>
   select platform.plt_name,traders.tr_name,traders.tr_market from platform
right join traders on platform.plt_trd_id=traders.tr_id;<br><br>
    <img width="286" alt="image" src="https://user-images.githubusercontent.com/72780341/162397261-c6e0950f-bee5-41de-9aa5-87bcbfa36fc7.png">
   </li>
  </ul>
 </li>
</ol>
