# Patient Waitlist- Dashboard


## Background

The healthcare industry is constantly striving to improve patient care and operational efficiency. One critical aspect of managing a hospital effectively is the efficient handling of patient waitlists. Whether it's for scheduling surgeries, consultations or admissions, a well-organized patient waitlist system ensures timely access to healthcare services while optimizing resource utilization.

In this project, we aim to utilize Power BI, a powerful business intelligence tool, to analyze and visualize patient waitlist data for a hospital. The dataset includes various attributes such as patient age, diagnosed diseases, and patient status (day case, inpatient, outpatient). By harnessing the capabilities of Power BI, healthcare administrators and decision-makers can gain valuable insights into waitlist dynamics, identify bottlenecks, and streamline processes to enhance patient satisfaction and operational efficiency.

## Problem Statement

#### Optimizing Patient Prioritization:

- How can we prioritize patients on the waitlist based on factors such as severity of illness, age, and medical urgency?
- Are there specific diseases or conditions that consistently lead to longer wait times? How can we address this issue?

#### Resource Allocation and Capacity Planning:

- Are there certain times of the day, week, or month when the hospital experiences higher demand for services?
- How can we allocate resources more effectively to reduce wait times without compromising quality of care?

#### Monitoring and Performance Evaluation:

- What key performance indicators (KPIs) should be tracked to measure the effectiveness of the waitlist management system?
- How can we use real-time data analytics to monitor waitlist status, identify trends, and make proactive adjustments to improve performance?
By addressing these problem statements through data-driven insights and actionable strategies, we aim to enhance the overall efficiency and effectiveness of the hospital's patient waitlist management system, ultimately improving patient outcomes and satisfaction.


### Steps followed 

- Step 1 : Load data into Power BI Desktop, dataset is a csv file.
- Step 2 : Open power query editor & in view tab under Data preview section, check "column distribution", "column quality" & "column profile" options.
- Step 3 : Checked the default settings of all the columns
- Step 4 : Due to large number of diseases names we created a new Table 'Mapping Speciality , where all the diseases were categorised into groups .
- Step 5 : For Latest month waitlist and Previous Month waitlist following Dax queries were used :

                Latest Month Waitlist = CALCULATE(SUM(AppendTable[Total]),AppendTable[Archive_Date]= MAX(AppendTable[Archive_Date])) + 0
                PY Latest Month Waitlist = CALCULATE(SUM(AppendTable[Total]), AppendTable[Archive_Date] = EDATE(MAX(AppendTable[Archive_Date]),-12)) + 0
Snapshot of KPI:

![Capture](https://github.com/paso2004/patientWaitlist/assets/161154534/9320ddf9-8828-4fbf-846f-10883f13aa74)

        
- Step 6 : To switcg between Average and Median value of the data a switch was created . First simple DAX function was used to find Avergae and Median of Total column and then DAX was used to make the Button switch between Median and Average :
                
                Average Waitlist = AVERAGE(AppendTable[Total])
                Median Waitlist = MEDIAN(AppendTable[Total])
                Avg / Median waitlist = SWITCH(VALUES('Calculation Method'[Calc Method]),"Average" , [Average Waitlist], "Median", [Median Waitlist])

Snapshot of Button:

![Capture2](https://github.com/paso2004/patientWaitlist/assets/161154534/2302c9d6-5999-4bda-b52b-97f8b481c651)


- Step 7 : Average and Median Waitlist by Case type was represented using a Donut chart . 

- Step 8 : To find the distribution over time period we used a stacked Column chart while using Age profile as legend.
- Step 9 : Line Chart was used to show the distribution of Inpatients , Out patients and Day case over time.



# Snapshot of Dashboard (Power BI DESKTOP)

![Capture3](https://github.com/paso2004/patientWaitlist/assets/161154534/4d92682a-a6d3-48ff-992b-5aa16ad71c56)


 
