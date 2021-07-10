# Fetch-Exercise <br/><br/>

## Q1. Review Existing Unstructured Data and Diagram a New Structured Relational Data Model <br/>

To make Diagram a New Structured Relational Data Model I created an ER diagram. <br/>
For making Structured ER diagram I looked if any data are connected with each other. User data and receipts data is connected with each other as receipts have User primary key as foreign key.  They have one to many relations. As one user can have many receipts. Brand Data is not connected with any of the Data. Such kind of ER diagram in which all the data are not connected with each other is called  <br/><br/>
The following diagram shows the ER diagram for all Data.<br/>
![ER diagram]( https://github.com/Gayatr12/Fetch-Exercise/blob/master/Diagram1.JPG)<br/><br/>

## Q2.Write a query<br/>
<b>1.What are the top 5 brands by receipts scanned for most recent month?<br/></b>
<b>2.How does the ranking of the top 5 brands by receipts scanned for the recent month compare to the ranking for the previous month?<br></b>
->The above two query cannot be solved as Brand and receipts data are not connected with each other.<br/>
<b>3. When considering average spend from receipts with 'rewardsReceiptStatus’ of ‘Accepted’ or ‘Rejected’, which is greater?<br/></b>
->In this rewardsReceiptStatus does not have any values as ACCEPTED, So I consider it for REJECTED and FINISHED. I use the following sql code:<br>
<b>SELECT rewardsReceiptStatus,AVG(totalSpent) <br/>
from receipts <br/>
group by rewardsReceiptStatus  
HAVING rewardsReceiptStatus = 'REJECTED' OR rewardsReceiptStatus = 'FINISHED'<br/>
ORDER BY AVG(totalSpent) desc<br/>
LIMIT 1<br/>
The following is the output for the above query1:<br/></b>
![SQL Query]( https://github.com/Gayatr12/Fetch-Exercise/blob/master/Diagram2.JPG )
<b>4. When considering total number of items purchased from receipts with 'rewardsReceiptStatus’ of ‘Accepted’ or ‘Rejected’, which is greater?<br/></b>
-> In this rewardsReceiptStatus does not have any values as ACCEPTED, So I consider it for REJECTED and FINISHED. I use the following sql code:<br/>
<b>SELECT rewardsReceiptStatus, SUM(purchasedItemCount)<br/> 
from receipts <br/>
group by rewardsReceiptStatus 
HAVING rewardsReceiptStatus = 'REJECTED' OR rewardsReceiptStatus = 'FINISHED'<br/>
ORDER BY SUM(purchasedItemCount) desc<br/>
LIMIT 1<br/></b>
The following is the output for the above query:<br/></b>
![SQL Query]( https://github.com/Gayatr12/Fetch-Exercise/blob/master/Diagram3.JPG )
<b>5.Which brand has the most spend among users who were created within the past 6 months?<br/>
Which brand has the most transactions among users who were created within the past 6 months?<br/></b>
-> The above two query cannot be solved as Brand and Users data are not connected with each other.<br/>













