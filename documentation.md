<p>For this project, to generate the tables in .CSV format, we have used python (3.6 version).</p>
<p>After generating the tables (account_master, account_name, transaction_details), I have moved them to the downloads folder in the cloudera (location: /home/cloudera/Downloads).</p>

<p><strong>Environment (Virtual machine setup) cloudera used for performing the below tasks:</strong></p>

[comment]: <> (Image-1 here)

<p>RAM used: 4096 MB.</p>

<p><strong>1.Creating Account_master table with below columns.&nbsp;</strong></p>
<p><strong>&nbsp; &nbsp;Account number&nbsp;</strong></p>
<p><strong>&nbsp; &nbsp;Account Opening Balance&nbsp;</strong></p>
<p><strong>&nbsp; &nbsp;Ledger Balance&nbsp;</strong></p>
<p><strong>&nbsp; &nbsp;Clearing Hold&nbsp;</strong></p>
<p><strong>&nbsp; &nbsp;Account status code&nbsp;</strong></p>
<p><strong>&nbsp; &nbsp;Country Code</strong></p>
<p><strong>&nbsp; &nbsp;Account Currency&nbsp;</strong></p>
<p><strong>&nbsp; &nbsp;Simulate the data for 1000 Account numbers.&nbsp;</strong></p>
<p>&nbsp; &nbsp;<strong>Account number&nbsp;- 10-digit number&nbsp;</strong></p>
<p><strong>&nbsp; &nbsp;Account Opening Balance&nbsp;- random number between 100 to 1000000</strong></p>
<p><strong>&nbsp; &nbsp;Ledger Balance&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;- random number between 100 to 1000000</strong></p>
<p><strong>&nbsp; &nbsp;Clearing Hold&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; - random number between 100 to 1000</strong></p>
<p><strong>&nbsp; &nbsp;Account status code&nbsp; &nbsp; &nbsp; - Allowable values 1/8/5&nbsp;</strong></p>
<p><strong>&nbsp; &nbsp;Country Code&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;- 3 Char</strong></p>
<p><strong>&nbsp; &nbsp;Account Currency&nbsp; &nbsp; &nbsp; &nbsp; &nbsp;- USD/INR/CAD</strong>&nbsp;</p>

<p><span style="text-decoration: underline;">Code to create table account_master in hive:</span></p>
<p>CREATE TABLE account_master (&nbsp;<br /> account_number BIGINT ,<br /> account_opening_balance INT ,<br /> ledger_balance INT,<br /> clearing_hold INT ,&nbsp;<br /> account_status_code INT,&nbsp;<br /> country_code STRING ,&nbsp;<br /> account_currency STRING)&nbsp;<br /> row format delimited&nbsp;&nbsp;<br /> fields terminated by ","&nbsp;<br /> stored as textfile<br /> TblProperties("skip.header.line.count" = "1");&nbsp;<br /> load data local inpath '/home/cloudera/Downloads/account_master.csv'&nbsp;<br /> overwrite into table account_master;&nbsp;</p>

<p><strong>2.Create account_name table with below columns&nbsp;</strong></p>
<p><strong>&nbsp; &nbsp;Account Number&nbsp;</strong></p>
<p><strong>&nbsp; &nbsp;First name&nbsp;</strong></p>
<p><strong>&nbsp; &nbsp;Middle Name&nbsp;</strong></p>
<p><strong>&nbsp; &nbsp;Last name&nbsp;</strong></p>
<p><strong>&nbsp; &nbsp;Date of birth&nbsp;</strong></p>
<p><strong>&nbsp; &nbsp;Joint account or not&nbsp;</strong></p>
<p><strong>&nbsp; &nbsp;Joint Account Number&nbsp;</strong></p>
<p><strong>&nbsp; &nbsp;Similar to above.</strong></p>

<p><span style="text-decoration: underline;">Code to create table account_name in hive:</span></p>
<p>CREATE TABLE account_name (&nbsp;<br /> account_number BIGINT ,<br /> first_name STRING ,<br /> middle_name STRING ,<br /> last_name STRING,<br /> date_of_birth DATE,&nbsp;<br /> joint_account_or_not STRING,&nbsp;<br /> joint_account_number BIGINT)&nbsp;<br /> row format delimited&nbsp;&nbsp;<br /> fields terminated by ","&nbsp;<br /> stored as textfile<br /> TblProperties("skip.header.line.count" = "1");&nbsp;<br /> load data local inpath '/home/cloudera/Downloads/account_name.csv'&nbsp;<br /> overwrite into table account_name;</p>

<p><strong>3.Create transaction_details table with below columns&nbsp;</strong></p>
<p><strong>&nbsp; &nbsp;Account number&nbsp;</strong></p>
<p><strong>&nbsp; &nbsp;Transaction Posting date&nbsp;</strong></p>
<p><strong>&nbsp; &nbsp;Transaction capture date&nbsp;</strong></p>
<p><strong>&nbsp; &nbsp;Transaction amount&nbsp;</strong></p>
<p><strong>&nbsp; &nbsp;Debit or Credit&nbsp;</strong></p>
<p><strong>&nbsp; &nbsp;Transaction code&nbsp;</strong></p>
<p><strong>&nbsp; &nbsp;Transaction Currency (USD/INR/CAD/HKD)&nbsp; &nbsp;</strong></p>
<p><strong>&nbsp; &nbsp;Simulate the data for 3000 records.&nbsp;</strong></p>
<p><strong>&nbsp; &nbsp;Account number&nbsp; &nbsp; - Should be valid account number from account number list</strong></p>
<p><strong>&nbsp; &nbsp;Transaction Posting date&nbsp;- The date can be anything from 01-July-2017 to current date</strong></p>
<p><strong>&nbsp; &nbsp;Transaction capture date&nbsp;- The date can be anything from 01-July-2017 to current date</strong></p>
<p><strong>&nbsp; &nbsp;Transaction amount&nbsp; &nbsp; &nbsp; &nbsp; &nbsp;- 100 to 1500 any random number</strong></p>
<p><strong>&nbsp; &nbsp;Debit or Credit&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;- D for debit or C for Credit&nbsp;&nbsp;</strong></p>
<p><strong>&nbsp; &nbsp;Transaction code&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; - 10001 for debit or 2001 for debit&nbsp;</strong></p>

<p>Code to create table transaction_details in hive:</p>
<p><br /> CREATE TABLE transaction_details (account_number BIGINT,<br /> transaction_posting_date DATE,<br /> transaction_capture_date DATE,<br /> transaction_amount INT,<br /> debit_or_credit CHAR(1),<br /> transaction_code BIGINT,<br /> transaction_currency CHAR(3))<br /> row format delimited fields terminated by ","<br /> stored as textfile<br /> tblproperties ("skip.header.line.count"="1");<br /> load data local inpath '/home/cloudera/Downloads/transaction_details.csv'<br /> overwrite into table transaction_details;</p>

<p><strong>Requirement:&nbsp;</strong></p>
<p><strong>Perform exploratory data analysis on the data which was created and loaded into Hive table.</strong></p>
<p><strong>What are the social&nbsp;and business values of those insights?&nbsp;</strong></p>
<p>After the data tables were generated, I went through all the information(using the .csv files) and found the following details.</p>
<ul>
<li>In Account_master table, I see that the account holders were maintaining the balance in their local currency. Most of the account holders maintain the currencies in Canadian dollars, US dollars or Indian Rupees. From this we can say that bank has account holders from 3 different countries mainly India, United States and Canada, and also can guess that bank/institution is located in these 3 countries.</li>
<li>In Account_name table, I see that 496 out of 1000 account holders were having the joint_account, which is 49.6% of the sample data, we took for this project. On observing the year of birth of the account holders, we can see that people born between 1990&amp;1999 &ndash; 363 accounts, 1980 -1989 &ndash; 407 accounts &amp; 1975-1979 &ndash; 230 accounts. From this we can say that people in between the age of 19-38years account to 77.0% of total accounts in the bank (according to sample data).</li>
<li>In Transaction_details table, I see that even though the account holders are from the 3 countries as predicted from the account_master table, account holders were doing transactions to another country China. Out of the 3000 transactions 1465 were made by credit card and 1535 were made by debit card.</li>
</ul>

<p><strong>Skill Set to be used:&nbsp;</strong></p>
<p>SQL skills to join multiple table, aggregations and other operations.&nbsp;</p>

<ul>
<li>Code to get the distinct country codes (account holders from different locations) present in the account_master table.</li>
</ul>

<p>select distinct(country_code)</p>
<p>from account_master;</p>

[comment]: <> (Image-2 here)

<p>It took me 41.086 seconds to execute the code, and fetched 3 rows &ldquo;USA&rdquo;, &ldquo;IND&rdquo;, &ldquo;CAN&rdquo;. It means there are account holders from the 3 countries United States of America, India and Canada.</p>
<ul>
<li>Code to get data where country code = &ldquo;USA&rdquo; from account_master table;</li>
</ul>
<p>select * from account_master</p>
<p>where country_code = &ldquo;USA&rdquo;;</p>

[comment]: <> (Image-3 here)

<p>It took 1.63 seconds to execute the above code and fetched 329 rows. It means there are 329 account holders in the country USA.</p>
<ul>
<li>Code to get details of joint_account holders from the data we used.</li>
</ul>
<p>select * from account_name</p>
<p>where joint_account_or_not = &ldquo;yes&rdquo;;</p>

[comment]: <> (Image-4 here)

<p>After executing the above code, it fetched 496 rows of data. It means there are 496 account holders with the joint account.</p>
<ul>
<li>For account holders whose date of birth falls between 1974 to 1980.</li>
</ul>
<p>select * from account_name</p>
<p>where date_of_birth &gt; 1974 and date_of_birth &lt;1980;</p>

[comment]: <> (Image-5 here)

<p>After executing the above code, it fetched 230 rows of data. It means there are 230 account holders in between age of 39-43years.</p>
<ul>
<li>Query to get details of account holders born between 1980 and 1990.</li>
</ul>
<p>select * from account_name</p>
<p>where date_of_birth &gt;= 1980 and date_of_birth &lt;1990;</p>

[comment]: <> (Image-6 here)

