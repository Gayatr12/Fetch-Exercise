# Fetch-Exercise <br/>

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
The following is the output for the above query:<br/></b>
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

## Q3. Evaluate Data Quality Issues in the Data Provided.<br/>
-> There are Different Data Quality issues some of them are as follow:<br/>
Missing values or Null values in data, Duplicated Data, Inconsistent formats, Incorrect Data etc.<br/>
I have identified Missing values in data using python. The following is the code:<br/>
<b>import json<br/>
import pandas<br/>
with open('users.json') as f:<br/>
    data = pd.DataFrame(json.loads(line) for line in f)<br/>
print(data.isnull().sum())<br/></b>
The above code will return total number of cells that have missing or null values for each columns in data.<br/>
The following will be the output for USERS data. <br/>
![Data Quality]( https://github.com/Gayatr12/Fetch-Exercise/blob/master/Diagram4.JPG )<br/>
The output shows count of cells that have missing values for each column.<br/>

## Q4. Communicate with Stakeholders<br/>

->
<b>1.<br/></b>
Hello,
I have some question about Data, It would be great if I can get some more detail information about it. Following are the questions about data:<br/>
1.I would like to know where did the data come from, how was it collected, which tools were used?<br/>
2. What could be done with this information?<br/>
3. What’s the next action step to take as a result of the data<br/>
This will help me to understand and document the source of values for each required attribute and relationship.<br/><br/>

Hope to hear from you soon.<br/><br/>

Regards,<br/>
Gayatri<br/>

<b>2,3,4,5. </b> <br/>
Hello,
I am happy to answer your all questions.<br/>
2. There are Different Data Quality issues some of them are as follow: Missing values or Null values in data, Duplicated Data, Inconsistent formats, Incorrect Data etc <br/>
To discover missing value or null values we can run a code on data to find null values or missing values. This code will give us if any column has any columns have missing values if they do, we can handle this values column vise. <br/>
Sometimes we may find duplicate data in data base. This can be because of many reasons like human error, an application bug, and many other. We can check if database have duplicates entry or not using SQL query.<br/>
To find duplicates values in SQL comprises two key steps:<br/>
Using the GROUP BY clause to group all rows by the target column(s) – i.e. the column(s) you want to check for duplicate values on.<br/>
Using the COUNT function in the HAVING clause to check if any of the groups have more than 1 entry; those would be the duplicate values.<br/>

3.To optimize the data we need following information:<br/>
* We need to know how the process and system work. This will help us to collect information about the primary systems and who uses them. <br/>
* We need to share data for use so to share the data we need to ask few questions to departments or project leads.<br/>
1. What data are we generating?<br>
2. Who needs access to this data?<br/>
3. How will data be shared or accessed?<br/>
4. Does the data contain private or confidential information?<br/>
5. How will access be restricted or managed?<br/>
* The quality of data is not low. For example if data is not having any null values or any duplicate entries in data.<br/>

4. According to me, the ability of a system to offer a specific reaction time is referred to as performance for example service a predetermined number of people or handle a predetermined amount of data. So we can say that, performance is a metric for software quality.<br/>
And, the ability of a system to scale up its performance by adding more resources is referred to as scalability. People frequently believe that their systems are scalable right out of the box. “If we need to service more users, we just add another server,” is a common response to performance issues.<br/>
Whether your system is scalable or not depends on your architecture. we can say that if we want our systems to be scalable we have to take this into consideration right from the beginning of development and also monitor throuhout the lifecycle.  If we have to ensure it, we have to monitor it. This means that performance management must then treated equally relevant than the management of functional requirements.

I hope I answer all your question.
Please let me know if you have any other question.

Regards,
Gayatri.



























