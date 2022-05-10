<h1 align="center">Corporate Employee Weekly Evaluation Dashboard</h1>

<h2>Business Problem</h2>
<p>The challenge for this data analyst project is outlined below. This has been used continuously to ensure that the right data has been selected, transformed and used
in the data visualization which is meant to be passed on to the business users.</p>
<br/>

  >**"As a data analyst working at a big corporation within the Compliance Operations Team you are asked to visualize data that will help managers and Subject Matter Experts understand how associates are performing at a weekly level by taking a 30-minute evaluation of business updates.**
>**The main task is to Have an overview of the employees' weekly evaluation results for each type of task and seniority level, to further make decisions based on these metrics ( such as reward employees who have a repetitive weekly score of 100% for at least the latest 5 weeks in a row; organize refresher sessions for those who don't meet the required target)."**

<h2>Data Collection and Table Structure</h2>

The necessary data was first imported from a weekly updated Excel file and then modelled directly into Power BI (using DAX measures):

![image](https://user-images.githubusercontent.com/83698238/167680139-40de782f-5235-41be-bf3f-a4a32e0ac003.png)

<h2>Data Model</h2><br/>
As the data source is simply an Excel file, the data model mainly consists of the imported Excel file, a DAX measures table and two other tables that hold the user's login and photo URL (1 for managers, 1 for employees). <br/>

![corporate_tables_relationship](https://user-images.githubusercontent.com/83698238/167676670-f80683d7-c5fa-42e7-9962-94436af1943d.png)

<h2>Calculations</h2>

The following calculations were created in the Power BI report using DAX(Data Analysis Expressions). To lessen the extent of coding, the re-use of measures (measure branching) was emphasized:

```
1) filter_assoc = CALCULATE ( IF ( ISFILTERED ( 'Corporate Score'[UserId] ), 1, 0 ), ALLSELECTED ( 'Corporate Score' ) )
2) filter_mngr = IF(HASONEFILTER('Corporate Score'[manager_login]),1,2)
3) Todays week = CONCATENATE("Current week: ",WEEKNUM(TODAY(),1)-1)
```
<h2>Corporate Employee Evaluation Dashboard Analysis</h2></br>
The finished dashboard consists of visualizations and filters that gives an easy option for the end users to navigate the employees performance (scores vs target) for each task. Some possibilities are to filter by ManagerID, UserID, Month, Week, Quarter, Task, Type of Evaluation, Achievement, No of errors. Based on these filters and the data pulled by the dashboard, decisions can be taken at a higher level within the organization.

![image](https://user-images.githubusercontent.com/83698238/167682788-4458354f-178b-4a6c-9964-affa0fede517.png)

The interactiveness can also be seen at either the manager or employee sections, where the end user can select a user name and see their picture (thus putting a face to the name and getting to know their colleagues in the current WFH environment).



https://user-images.githubusercontent.com/83698238/167684001-1686a506-66cf-4e67-824d-bb71393ec764.mp4



<h5>Click below to open the dashboard and try it out (or download the .pbix file in this repository)</h5>

[Corporate Employee Evaluation Power BI Dashboard](https://app.powerbi.com/groups/me/reports/b70b2b3d-fe33-4f50-8c5b-33bc6e1b2728/ReportSection)
