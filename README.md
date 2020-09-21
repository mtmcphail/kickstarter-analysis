# Kickstart Crowd Funding Analysis

## Overview

### Purpose
Louise, a promising new playwrite, launched a crowd funding campaign to finance her new play, *_FEVER_*.  While Louise raised funds quickly (28 days), she fell short of her goal (86% funded).

Now, Louise would like to understand how well other, similar campaigns did to gain insight into why her campaign was not fully funded.

## Analysis and Challenges

### Analysis of Campaign Outcomes Based on Launch Date
Crowd funding data from over 1,300 campaigns supporting a variety of Theater projects was used to astertain if any month(s) in particular yielded a higher percentage of successful outcomes.

By utlizing simple Excel formulas to convert the Unix timestamp for launch date, a traditional date format, followed by a second second conversion of the launch date (Date Created Conversion) to a year format (Years).  The Parent Catregory (Theater) and the Years fields are used as a filter for a Pivot Table summarizing Outcomes (Successful, Failed, and Canceled) by Launch Month. Please see Graph 1 below.

Graph 1: Outcome of "Theater" Campaigns Based on Launch Month

![Launch Chart](./Resources/Theater_Outcomes_Vs_Launch.png)

### Analysis of Campaign Outcomes Based on Goals

Data from over 1,000 crowd funding campaigns supporting "Plays" was analyzed to gain insight into the effect the goal amount may have on the outcome of the campaign.  

Again using Excel, the "Goal" field was grouped into the following 12 categories and charted based on "Outcomes" (Successful, Failed, Canceled) and the percetage of total campaigns in each category was calculated using simple division:   

* Less than 1000  
* 1000 to 4999   
* 5000 to 9999
* 10000 to 14999
* 15000 to 19999
* 20000 to 24999
* 25000 to 29999
* 30000 to 34999
* 35000 to 39999
* 40000 to 44999
* 45000 to 49999
* Greater than 50000

No campaigns had the outcome of "Canceled".  Please see Graph 2 below.

Graph 2: Outcome of "Play" Campaigns Based on Goal Amount
  
![Goal Chart](./Resources/Outcomes_Vs_Goals.png)

### **Challenges and Difficulties** Encountered
There are some minor items to note that caused further inspection of the dataset.  

Regardless of year, no campaign funding a "Theater" project launched in October was canceled; they all either met their fundraising goals or did not. You can see this depicted in Graph 1 as a gap in the treadline for "Canceled".  Additionla steps need to be taken to confirm that data was not missing or dropped.

As per instructions, campaigns with goals of exactly $50,000 were not included in the "Goal" categories; which resulted is the ommission of 4 data points which had an outcome of "Failed" and a "Goal" of $50,000.  Please refer to the Goal Categories above.  This approach is counterintuitive and so extra attention was needed to ensure instructions were being properly followed. 

## Results

###**Outcomes Based on Launch Dates**

Based on the above analysis involving **launch date**, it is clear that not only is **May** a very popular month to launch campaigns (highest total campaigns launched), but yeilds the highest percentage of "Successful" campaigns (67% of campaigns launched are "Successful").

Conversely, **December** has the fewest campaigns launched (75) and also has the lowest success rate of 49%.

Louise launched her kickstart campaign in June, which yielded the second highest number of successful outcomes and the second highest percentage of successful outcomes (65%).

*Louise did not pick the wrong month to launch her campaign.* 


###**Outcomes Based on Goal Amount**

Regarding outcomes based on goals, campaigns with goals **less than $1,000** has the highest rate of success, 76%.

Meanwhile, the goal range of **$45,000 - $49,999** had the fewest number of campaigns (1) and the lowest success rate of 0%.

Furthermore, as the goal amount increases its rate of success decreases, until the $30,000 range.  At which point the success rebounds, but then crashes back down at the $45,000+ range.

Louise's goal for *FEVER* was $2,885; and similar to the launch month, this goal range, **$1,000 - $4,999** reported the second highest success rate of 73%.

*Louise did not pick the wrong goal.*

##**Limitations of the Dataset**
While the dataset is a well-rounded collection of campaign data involving different genres of projects, different geographies, launch dates, campaign lengths, and fundraising targets, one data point missing is the number of contacts the ask was sent to, a participation rate.  

By collecting the number of potential donors the fundraising ask was sent to and comparing to actual number of backers, the rate of participation can be calculated (or at least estimated).  This data point may provide insight into a how the campaign is promoted and launched.

In addition, collecting data on how many times potential donors are contacted ("asked") during the length of the campaign would be helpful.  The frequency of communication can also provide insight into what makes a successful crowd funding campaign. 

Finally, the data set does not include data on how the campaign was communicated (social media, email, text) nor how many channels. 

##**Next Steps**

Since it appears that Louise launched her campaign in a "successful" month and set an attainable goal, similar to other campaigns that were fully funded, *what was the cause of her shortfall?*

Looking at other factors included in this original data set, like the number of backers or campiagn duration, may give Louise better insight into what went wrong.  
  
**Outcome Based on Duration of Campaign**:  
***Was Louise's campaign too short?***  Still working in Excel, a new data point, "Campaign Duration", can be calculated by subtracting the "Date Created Converstion" from the "Date Ended Conversion" and rounding to nearest whole number (=round([Date Ended]-[Date Created],0). Number of day ranges can be determined: [0 - 15], [16 - 30], [31 - 45], [46 - 60], [61+]; and with the help of a pivot table, the "Campaign Duration" can be summarized based on "Outcome".

**Outcome Based on Number of Backers**:  
***Did Louise not have enough donor base to support her goal?*** Similiar to the Outcome Based on Duration of Campaign chart, the number of backers can be summarized by specificed ranges and plotted against outcomes (Successful, Failed, Canceled) using a pivot table.

 
