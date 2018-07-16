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
