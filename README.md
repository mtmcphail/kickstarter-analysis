![kickstarter logo](./Resources/kickstarter.png)

# **Kickstarter Crowdfunding Analysis**
## <span style="color:green"> Overview </span>

### Purpose
Louise, a promising new playwright, launched a Kickstarter campaign to finance her new play, *_FEVER_* in June of 2016.  While Louise raised funds quickly (28 days), she fell short of her goal of $2,885.00 (86% funded). 

Now, Louise would like to understand how well other, similar campaigns did with respect to their launch dates and funding goals to gain insight into why her campaign was not fully funded. Preparing for another campaign, Louise wants to hit her goal!  

With the use of Kickstarter data, which includes 4,114 campaigns (1,369 in the area of Theater and 1,066 in the subcategory of Plays) that were conducted between 2009 and 2017 with goals ranging from $1 to $100,000 in 21 countries, this analysis will focus on campaigns launched to support projects in the theater industry and specifically plays.  Let's see what we find! 

## <span style="color:green"> Analysis and Challenges </span>

### Analysis of Campaign Outcomes Based on Launch Date
Crowdfunding data from over 1,300 campaigns supporting a variety of Theater projects was used to ascertain if any month(s) in particular yielded a higher percentage of successful outcomes.

Utilizing simple Excel formulas, the Unix timestamp for the launch date ("launched_at") was converted to a traditional date format
```=(((J2/60)/60)/24)+DATE(1970,1,1)``` followed by a second conversion of the launch date [Date Created Conversion] to a year format [Years] ```=YEAR(S2)```.  The Parent Category ("Theater") and the Years fields are used as filters for a Pivot Table summarizing Outcomes (Successful, Failed, and Canceled) by Launch Month.  
 
Finally, the percentage of total campaigns that were "successful" is calculated using simple division to get insight into a simple success rate by month and apended to the Pivot Table.  
Please see Graph 1 and Chart 1 below.  
    
**<span style="color:green">Graph 1: "Theater" Campaign Outcomes Based on Launch Date</span>**
![Launch Graph](./Resources/Theater_Outcomes_Vs_Launch.png)


**<span style="color:green">Chart 1: "Theater" Campaign Outcomes Based on Launch Date</span>**  
![Launch Chart](./Resources/Chart_Launch_Date.png)


### Analysis of Campaign Outcomes Based on Goals

Data from over 1,000 crowdfunding campaigns supporting "Plays" was analyzed to gain insight into whether these specific campaigns have a higher success rate at certain goals levels.  

Again using Excel, the Goal field was grouped into the following 12 categories or bins using the COUNTIFS function  
```=COUNTIFS(Kickstarter!$F:$F,"successful",Kickstarter!$D:$D,"<1000",Kickstarter!$P:$P,"plays")```  
and then charted based on Outcomes ("Successful", "Failed", "Canceled").  The percentage of total campaigns ```=SUM(C3:E3)``` in each category was calculated using simple division ```=C3/F3```.  Please see Graph 2 and Chart 2 below.  
  
  
      
**<span style="color:green">Graph 2: "Plays" Campaign Outcomes Based on Goal Amount</span>** 
![Goal Graph](./Resources/Outcomes_Vs_Goals.png)

**<span style="color:green">Chart 2: "Plays" Campaign Outcomes Based on Goal Amount</span>**
![Goal Chart](./Resources/Chart_Goals.png)

 

### **Challenges and Difficulties** Encountered
There are some minor items to note that caused further inspection of the dataset.  

* Regardless of year, no campaign funding a "Theater" project launched in October was canceled; they all either met their fundraising goals or did not. You can see this depicted in Graph 1 as a gap in the trendline for "Canceled".  Additional steps needed to be taken to confirm that data points were not missing or dropped.

* As per instructions, campaigns with goals of exactly $50,000 were NOT included in the "Goal" categories; which resulted in the omission of 4 data points for this dataset (outcome of "Failed" and a "Goal" of $50,000).  Please refer to the Goal Categories above.  This approach is counterintuitive and so extra attention was needed to ensure instructions were being properly followed. 
  

## <span style="color:green">Results</span>  

### Outcomes Based on Launch Dates

Based on the above analysis involving **launch date**, it is clear that not only is **May** a very popular month to launch campaigns (highest total campaigns launched) but yields the highest percentage of "Successful" campaigns (67% of campaigns launched are "Successful" or fully funded).

Conversely, **December** has the fewest campaigns launched (75) and also has the lowest success rate of 49%.

Louise launched her Kickstart campaign in June, which yielded the second-highest number of successful outcomes and the second-highest percentage of successful outcomes (65%). Simply put, <mark style="background-color: Yellow">*Louise did not pick a bad month to launch*.</mark> 

  
### Outcomes Based on Goal Amount

Graph 2 and Chart 2 indicate that campaigns with **goals** of **less than $1,000** have the highest rate of success, 76%.  Meanwhile, the goal range of **$45,000 - $49,999** had the fewest number of campaigns (1) and the lowest success rate of 0%.

Furthermore, as the goal amount increases its rate of success decreases, until the $30,000 range.  At which point the success rebounds, but then crashes back down at the $45,000+ range. 

Louise's goal for *FEVER* was $2,885; and similar to the launch month, this goal range, **$1,000 - $4,999** reported the second-highest success rate (73%).  This range was also the most popular representing 51% of the all "play" campaigns in this dataset (534 of 1,043). Simply put, <mark style="background-color: Yellow">*Louise did not set a bad goal*.</mark> 


### Limitations of the Dataset  

While the dataset is a well-rounded collection of campaign data involving different genres of projects, different geographies, launch dates, campaign lengths, and fundraising targets, one data point missing is the number of contacts the donation ask was sent to: a participation or conversion rate.  

By collecting the **number of potential donors (i.e. reach)** the donation ask was sent to and comparing to actual number of backers, the rate of participation can be calculated (or at least estimated). *Does a succssful campaign have a certain participation percentage a fundraiser should target?*

In addition, collecting data on how many times potential donors are contacted (i.e. **frequency of the ask**) during the length of the campaign would be helpful.  Finally, the data set does not include data on how the campaign was communicated out (via social media, email, or text) nor how many channels (single or multi).  


### Next Steps

Since it appears that Louise launched her campaign in a "successful" month and set an attainable goal, similar to other "Theater" and "Play" campaigns that were fully funded, *what was the cause of her shortfall?*

Looking at other factors included in this original data set, like the number of backers or duration for similar campaigns, may give Louise better insight into what went wrong.  
  
**Outcome Based on Duration of Campaign**:   
*Was Louise's campaign too short?*  Still working in Excel and still looking at kickstarters involving plays, a new data point, "Campaign Duration", can be calculated by subtracting the "Date Created Conversion" from the "Date Ended Conversion" rounding to the nearest ones ```=ROUND(T2-S2,0)```. With the help of the COUNTIFS function, ```=COUNTIFS(Kickstarter!$F:$F,"successful",Kickstarter!$V:$V,"<30",Kickstarter!$P:$P,"plays")``` , the "Campaign Duration" for each Outcome ("Successful", "Failed, Canceled") can be grouped based on bins: "Less than 30", "30" and "Greater than 30". For this simple exercise, the ```=MODE()``` function was used to determine the 3 basic bins.  Please see Graph 3 and Chart 3 below.

**<span style="color:green"> Graph 3: "Plays" Campaign Outcomes Based on Duration (Days) </span>**
![Duration Graph](./Resources/Outcomes_Vs_Duration.png)

**<span style="color:green"> Chart 3: "Plays" Campaign Outcomes Based on Duration (Days) </span>**
![Duration Chart](./Resources/Chart_Duration.png)

Based on this quick analysis, while it appears that the **30 day** bin is the most popular (highest total campaigns), the **less than 30** day bin has highest number of successful campaigns and the highest success rate (76%).  Furthermore, at this level of analysis, the relationship appears to be negatively correlated: the longer the campaign, the lower the success rate. 

Louise's FEVER campaign was 28 days and this quick analysis confirms she picked an effective campaign duration. 

**Outcome Based on Number of Backers**:   
*Did Louise not have enough donor base to support her goal?* Similiar to the Outcome Based on Duration of Campaign chart, the number of backers can be summarized by specified ranges and plotted against outcomes (Successful, Failed, Canceled).  
 
  
    
**<span style="color:green">Graph 4: "Plays" Campaign Outcomes Based on Number of Backers</span>**  
![Backers Graph](./Resources/Outcomes_Vs_Backers.png)

**<span style="color:green">Chart 4: "Plays" Campaign Outcomes Based on Number of Backers</span>**  
![Backers Chart](./Resources/Chart_Backers.png)   

Based on this quick analysis, it appears that the **fail rate** is highest with **0-25 backers**; Louise only had 10.

Clearly furter investigation is needed; it appears that Louise may have launched her campaign in an appropriate month and set an appropriate goal and duration of campaign, but it fell short on number of backers.  Why this ocurred requires additional data outside the scope of this dataset. 