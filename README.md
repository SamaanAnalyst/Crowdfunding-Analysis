# An Analysis of Kickstarter Campaigns
Performing analysis on Kickstarter data to uncover trends, using Excel built-in functions and pivot charts. <br>
This project is focused on utilizing Excel functions and solutions to analyze an extensive set of data, and the analysis report <br> is centered around deployed Excel skills and techniques. 

## Overview of Project
Louise is an up-and-coming playwright, who wants to start a crowdfunding campaign to help fund her play, ***Fever***. <br>
She has estimated over $10,000 as a budget and is understandably hesitant about jumping into her first fundraising campaign. <br>

Louise has provided us with an Excel data file that contains details about crowdfunding campaigns based majorly in the <br> the United States. <br>

Using Excel to analyze Kickstarters data will help us understand campaigns from start to finish and assist Louise in setting her campaign to mirror other successful ones in the same category.

### Purpose 
We aim to organize, sort and analyze crowdfunding data to determine the specific factors that make a campaign successful. 

We will focus on comparing kickstarters concerning interest, finances, timing, location, and other confounding factors that may influence the trajectory of a campaign. Furthermore, we will provide visual representations of the dataset, precisely the campaigns' outcomes, and chronological and statistical analyses. 

The insights gained from this comprehensive analysis will help Louise plan her Kickstarter campaign and set it up for success. 

## Objectives
We will be performing data analysis on several thousand crowdfunding projects to uncover any hidden trends. <br>
1. Inspect data in the Excel file (crowfunding_StarterBook.xlsx).
2. Filter and sort the campaigns based on their funds and outcomes. 
3. Provide visual aid to interpret outcomes quickly and efficiently.
4. Calculate the percentage funded for each campaign and create a color-graded reference.
5. Visualize campaigns' outcomes based on category.
6. Impact of the country on fundraising interest and success.
7. Visualize campaigns' outcomes based on subcategories.
8. Study the effects of timing and duration on outcomes.
9. Visualize outcomes of plays' campaigns based on goal amounts.
10. Examine a few plays' kickstarters that are similar to the projected *Fever* campaign.
11. Study campaigns from the Edinburgh Festival Fringe for Theatrical Production.
12. Perform basic statistical analysis on US-based kickstarters to support *plays*.
13. Find the average donation for each campaign and visualize donations for plays in the United States.  
14. Create a Box and Whisker plot for British musical productions.

## Resources
- Data sources: crowdfunding_StarterBook.xlsx. 
- Programs: Microsoft Excel.
- Online Tools: GitHub.

## Analysis & Code
The steps of our analysis of the crowdfunding campaign data, along with code snippets, are displayed below.   
1. Start the analysis by inspecting the dataset, looking at the data's extent, formatting, and readability.
2. Louise estimates that her play will cost about $10,000, so we apply **filters** on data in the *pledged* and *goal* columns to research projects with a similar monetary goal.
3. Color-code the *outcomes* column using one of the conditional formatting options called **Highlight Cells Rules**, and set each unique outcome `equal to` color of choice.  
4. Create a new column of data called *Percentage Funded*, and <br>
  a. Use the ROUND formula to find the percentage of a campaign's funding from the *pledged* and *goal* columns, as such: `=ROUND(E2/D2*100,0)`.<br> 
  b. Apply a color scale conditional formatting onto the *Percentage Funded* column, and format cells based on their <br>
  values from red for the minimum to blue for the maximum.
5. A stacked column chart is best to visualize the outcomes of the theater category versus other categories in the dataset. We first divide the *Category and Subcategory* column into *Parent Category* and *Subcategory* columns. Then build a pivot table classifying outcomes per parent category that could also be filtered based on country. The specifics of the pivot table are as follows: *outcomes* in Columns, *Parent Category* in Rows, *outcomes* in Values, *country* in Filters. Finally, we create a stacked column chart showing which parent categories performed well and which did not. 
    - It is noteworthy that pivot charts in Excel are interactive if viewed inside the workbook and will adapt to the chosen filter as we look through outcomes in different countries.
6. Filter the category-outcomes pivot table based on country, and create a stacked column chart for the top two countries. 
7. Create a new pivot table in a new worksheet named *Subcategory Statistics*, and choose *country* and *Parent Category* to Filters, *outcomes* to Columns, *Subcategory* to Rows, and "outcomes* to Values. Then, choose a stacked column chart type.
8. The dates provided in the workbook need to be converted from UNIX timestamp to (mm/dd/yyyy) format; this is achievable through such formula `=(((J2/60)/60)/24)+DATE(1970,1,1)`, and outputting the dates in two new columns. Then, calculating the length of each campaign in days as such: `=DATEDIF(S2,T2,"D")`, followed by the average `=ROUND(AVERAGE($H:$H),0)`. Next is building a pivot table in a new worksheet, *Outcomes Based on Launch Date*, where Filters: *Parent Category* and years, Columns: *outcomes*, Rows: *Date Created Conversion* without years or quarters, and Values: *outcomes*. Then, using line charts to examine the trends in outcomes based on the time of the year. 
9. To visualize the percentage of successful, failed, and canceled, plays based on the funding goal amount, use the Excel function **COUNTIFS**. This function accepts more than one conditional criterion. Start by creating a new sheet called *Outcomes Based on Goals*, then create the columns to hold the counts and percentages. Additionally, create dollar-amount ranges so we can group projects on their goal amount. Next, use COUNTIFS() to populate the *Number Successful*, *Number Failed*, and *Number Canceled* columns by filtering on the Kickstarter *outcomes* column, on the *goal* column using the prespecified ranges, and on the *Subcategory* column using *plays* as the criteria. For example, `=COUNTIFS(Kickstarter!$D:$D, "<1000",Kickstarter!$F:$F, "successful", Kickstarter!$R:$R, "plays")`. Finally, select the *Goal* column and the percentages columns and insert a line chart. 
10. To look up specific campaigns by their names, use the Excel **Find** function by pressing **CTRL+F**. Alternatively, type the play's name into Excel's search bar. For Louise's request, filter the *Kickstarters* sheet for the *plays* subcategory, search for *Foresight*, *Walken on Sunshine*, and *We Play Chekhov*. 
11. To help Louise learn more about the GB's market using the VLOOKUP Excel function. First, create a new sheet called *Edinburgh Research* containing *Name* and *blurb* headers, and fill in the names of the plays of interest in the *Name* column. Then, in the first cell of the *blurb* column, insert the VLOOKUP formula to look for the play's data in the *Kickstarter* sheet, using the value in the name cell: `=VLOOKUP(A2,Kickstarter!$B:$C,2,FALSE)`. Next, adjust the table array and the third parameter to get the goal, pledged, percentage funded, average donation, backers' count, and the dates. 
12. To determine whether data points are clustered around one value or more spread out, find out the measures of central tendency and spread for the successful, US-based plays' campaigns. First, filter the workbook for *plays* (total of 1,066 plays), then *country* for US-based (total of 671), and lastly for a successful outcome (only 412 plays). Next, gather the successful US-based plays' campaigns in a new worksheet called *Successful US Kickstarters*. Next, filter for the failed campaigns for plays in the US (only 250 records) and collect them into a new worksheet called *Failed US Kickstarters*. In the new worksheet, create a table to hold all the descriptive statistical analysis results, facilitating the comparison between goals and pledges for failed and successful campaigns. The basic formulas used for the goal analysis: 
      - `=AVERAGE('Successful US Kickstarters'!D:D)`, `=AVERAGE('Failed US Kickstarters'!D:D)`
      - `=MEDIAN('Successful US Kickstarters'!D:D)`, `=MEDIAN('Failed US Kickstarters'!D:D)`
      - `=STDEV.P('Successful US Kickstarters'!D:D)`, `=STDEV.P('Failed US Kickstarters'!$D:$D)`
      - `=QUARTILE.EXC('Successful US Kickstarters'!$D:$D, 3)`, `=QUARTILE.EXC('Failed US Kickstarters'!$D:$D, 3)`
      - `=QUARTILE.EXC('Successful US Kickstarters'!$D:$D, 1)`, `=QUARTILE.EXC('Failed US Kickstarters'!$D:$D, 1)`
      - `IQR = Q3 - Q1`
      - The reference array was then adjusted to get the pledged analysis accordingly.
13. In the *Kickstarter* sheet, create a new column called *Average Donation* and use data from the *pledged* and *backers_count* columns and employ the ROUND formula again: `=ROUND(E2/L2,2)`. Next, transfer the average donations of successful and failed US plays' campaigns to a new sheet *Average Donation Box - US*, and insert a box-and-whisker plot to understand the spread of the average donations for plays in the United States more clearly. 
14. To build a box-and-whisker plot for British musicals, filter the Kickstarter dataset for crowdfunding campaigns in Great Britain (total of 604), then for *musicals* in the theater category, and copy them into a new worksheet named *Musicals GB*. Next, select the Goal and Pledged columns in the new sheet and insert a Box and Whisker into a separate sheet. 
 
### Challenges and Solutions
  - **Percentage Funded** graded-color scale: after applying the conditional formatting, we noticed that we had to scroll through <br>
  many data points before spotting a color transition, which indicated the presence of one or more outliers in the dataset. 
      - **Solution**: Highlight the column again and click *Conditional Formatting* followed by *Manage Rules*, then <br> 
      *Edit* the current rule and adjust the *Maximum Type* to *Percentile*, then manually enter the value as 90. 
  - **Average Donation** #DIV/0! Error: When scrolling through the average donations, we noticed an error occurring: `#DIV/0!` because every campaign would require a fundraising goal but would not necessarily get any backers, so naturally, dividing by 0 would give an error result.
      - **Solution**: We fixed the #DIV/0 error by wrapping the ROUND formula with the IFERROR formula. As a result, the output in the *Average Donation* column is a zero instead of an error. `=IFERROR(ROUND(E2/L2,2),0)`.
  - **VLOOKUP**: it was challenging to accurately update the range for different columns without shifting the source frame.
      - **Solution**: After selecting the table array source in the *Kickstarter* sheet, press F4 to change the reference from relative to absolute. Additionally, revise the third parameter in the VLOOKUP formula and maintain the same left-most column in the table-array reference when looking for different outputs. 
  - **COUNTIFS()**: When populating the function to include two criteria for the goal amount, `=COUNTIFS(Kickstarter!$D:$D, ">=1000", Kickstarter!$D:$D, "=<4999", Kickstarter!$F:$F, "successful", Kickstarter!$R:$R, "plays")`, it would result in a zero. To confirm that this was an erroneous output, we manually filtered the *Kickstarter* sheet for successful campaigns with a goal amount between $1,000 and $4,999, and we found 388 records. 
      - **Solution**: After many attempts to arrange the criteria, it became clear that the logical operator was the problem, where "<=1000" was functioning correctly while "=<4999" was not. Hence, we reversed the order of the logical operators to be less than or equal to (<=). `=COUNTIFS(Kickstarter!$D:$D, ">=1000", Kickstarter!$D:$D, "<=4999", Kickstarter!$F:$F, "successful", Kickstarter!$R:$R, "plays")`.
  - **Percent sign**: We want the y-axis tickers to include the percent sign in the *Outcomes Based on Goal* line chart;  however, when using the formula `=ROUND(B2/E2*100,0)` to calculate percentages, then changing the formatting of the percentage column from *General* to *Percentage*, the percent sign was then included in the y-axis tickers, but the numbers were multiplied by a 100.  
      - **Solution**: We changed the formula used to calculate the percentages to be `=ROUND(B2/E2,2)`, then formatted the column as *Percentage*. Note that the calculation must be rounded to 2 decimal points before formatting it to percentage; otherwise, it will round up the ratio and output inaccurate numbers. 
  - **Box and Whisker** plot: When filtering the main *Kickstarters* sheet to country and musicals and inserting the chart into a new sheet, if filters were to be cleared from the original reference sheet, then the musicals chart would change.
      - **Solution**: After filtering the *Kickstarters* sheet for GB's musicals, copy and paste these records into a new sheet designated for British musicals only, then build the box-and-whisker plot based on columns from that new sheet. 

## Results
1. The preliminary inspection of the Excel file (crowfunding_StarterBook.xlsx) reveals the following: 
    - There are 4,114 crowdfunding campaign records in 14 columns and 4,115 rows.
    - Out of 4,114 kickstarters, 3,038 (74%) originated in the United States.
    - For each campaign, there is information about its name and description, category and subcategory, goal and pledged funds, outcome and number of backers, launch and end dates, and country and currency.
    - Few examples of the information provided in the data file are: how much money each campaign will need to succeed in the *goal* column and how much each campaign made in the *pledged* column. Furthermore,  the *outcomes* column shows us if the campaign met its goal; finally, the *country* column lists where it started. 
    - Amounts in the *goal* and *pledged* columns are appropriately formatted as currency or accounting; however, the date columns are in UNIX timestamp, and the category and subcategory information is attached. 
    
2. After filtering and sorting the data based on funds and outcomes, we found that:
    -   The highest goal set for a crowdfunding campaign was ($100,000,000.00). 
    -   The highest pledged amount for a crowdfunding campaign was ($2,344,134.67).
    -   The highest successful goal set for a crowdfunding campaign was ($400,000.00). 

3. The ability to visually process outcomes quickly and efficiently is advantageous to campaign organizers. Hence, we set a color code for outcomes: "successful" in green, "failed" in red, "live" in blue, and "canceled" in yellow.

4. Many of the campaigns missed their goal amount by a small margin. By calculating the percentage funded for each campaign and applying a color scale from red (minimum) to blue (maximum), we could easily judge the outcome and determine how close a campaign came to reaching -and in some cases, exceeding their funding goal.<br> [Crowdfunding Excel file.](Data/crowdfunding_StarterBook.xlsx)   

5. Louise's focus is on fundraising for the theater. Hence, we analyzed the outcomes of 1,393 theater campaigns out of 4,114 records and found that theater kickstarters were the most popular in all countries.<br>
   
      <img src="https://github.com/Magzzie/Kickstarter-analysis/blob/main/Resources/parent_category_outcomes.png" width=45% height=45% align="center">
      
6. Then, we checked the impact of the country of origin on fundraising:
    - The two most prolific countries were the United States with 3,038 campaigns and Great Britain with 604. 
    - Although theater kickstarters were the most popular in both countries, there was higher diversity of interest in the US.
    - Theater campaigns in Great Britain were drastically more successful than all other campaigns.  
    - Theater fundraising success rate was higher in Great Britain than in the United States, with 72% (258 of 359) and 58% (525 of 912), respectively. <br>

    <img src="https://github.com/Magzzie/Kickstarter-analysis/blob/main/Resources/parent_category_outcomes_US.png" width=45% height=45%> <img src="https://github.com/Magzzie/Kickstarter-analysis/blob/main/Resources/parent_category_outcomes_GB.png" width=47% height=55%>

7. Theatrical productions are the area of most relevance to the playwright out of all the theater subcategories. So, we looked into subcategories in-depth and focused our tables and charts on **plays** since there may be large funding goals for theater-building proposals that would skew the theater fundraising analysis and impair our purpose. This analysis showed that kickstarters supporting plays were the chief interest across countries. <br>
     
      <img src="https://github.com/Magzzie/Kickstarter-analysis/blob/main/Resources/subcategory_outcomes.png" width=45% height=45%> <img src="https://github.com/Magzzie/Kickstarter-analysis/blob/main/Resources/subcategory_outcomes_US.png" width=45% height=45%> <img src="https://github.com/Magzzie/Kickstarter-analysis/blob/main/Resources/subcategory_outcomes_GB.png" width=45% height=45%>
  
8. Time considerations are valuable when planning a public effort such as a fundraiser; therefore, we analyzed campaigns' dates to assess trends. A line chart is best to reflect any trends in outcomes of campaigns over time, and when examined in the Excel file, it is interactive, and we can filter it in the same way we filter the data table. <br>
    - After converting the dates into a readable format and filtering the dataset for successful theater campaigns, we found the average length was 30 days, generally.  
    - The month that launched the most successful Kickstarter campaigns was May.
    - Theater followed the overall trend: a spike of successful campaigns began in June but tapered off by the end of the year.
    - The months of May and June had a greater success rate overall. However, January, June, July, and October had roughly the same number of failed campaigns.<br>
    
      <img src="https://github.com/Magzzie/Kickstarter-analysis/blob/main/Resources/outcomes_on_launchdate.png" width=45% height=45%> <img src="https://github.com/Magzzie/Kickstarter-analysis/blob/main/Resources/outcomes_on_launchdate_theater.png" width=45% height=45%> 
      
    - The data around technology campaigns revealed a different story; instead of one large spike, their trend lines were mostly overlapping, thus less predictable. <br>
    
      <img src="https://github.com/Magzzie/Kickstarter-analysis/blob/main/Resources/outcomes_on_launchdate_technology.png" width=45% height=45%>
      
9. Louise had estimated a $10,000 budget for her play, Fever, and is interested in knowing her success chances with such a budget. Therefore, we examined the relationship between the outcomes of theatrical production kickstarters and their monetary goal amounts. <br>
    - We found that the highest percentage of successful campaigns (76%) had goals closer to a thousand dollars. 
    - The success rate tapered down as the goal went higher until about $15,000, where failure was dominant. 
    - Campaigns with a goal of $10K-$15K faired at a 54% success rate.
    - A small group of successful campaigns (only 6) caused a break in the trendline, where 67% of campaigns with goals of $35K - $50k had succeeded. <br>
    
      <img src="https://github.com/Magzzie/Kickstarter-analysis/blob/main/Resources/Outcomes_vs_Goals.png" width=45% height=45%>

10. Louise has stated interest in specific plays from the United States and Great Britain that could be an example for her campaign. 
    - ***Foresight***: was a play from GB that Louise enjoyed. By looking at the color of the outcome, we can quickly determine that it was a successful campaign; it reached slightly over 100% of its goal - £2,004 pledged for a £2,000 goal, and the average donation of £117.88 was surprisingly high considering there were only 17 backers. Finally, we noticed that the campaign was not active for very long, just under a month (4/22/2016 - 5/16/2016). 
    - ***Walken on Sunshine*** was a successful US-based campaign that was active for only one month (4/13/2016 – 5/13/2016) and had a goal of ($10,000). However, it had achieved 123% of its goal with the pledged amount of ($12,325) from (173) backers who donated ($71.24) on average. 
    - ***We Play Chekhov*** was a successful US-based campaign that was active for less than a month (7/21/2014 – 8/13/2014) and had a goal of ($4,500). The campaign achieved 102% of its goal with the pledged amount of ($4,569) from (57) backers who donated ($80.16) on average.
    
11. Louise was inspired by five plays she saw at the Edinburgh Festival Fringe: *Be Prepared*, *Checkpoint 22*, *Cutting Off Kate Bush*, *Jestia and Raedon*, and *The Hitchhiker's Guide to the Family*. Using VLOOKUP to look up the plays, we found that: <br>
    - All these were successful plays campaigns based in Great Britain, and their goals ranged between $1,000 and $4,000. 
    - The percentage funded was (101% - 172%), the average donation range was ($33.03 - $51.79), and they had between 26 to 113 backers.
    - All but one campaign had lasted for about a month. The one exception was ten days; however, that campaign had the lowest goal in the group ($1,000).

12. The descriptive statistical analysis of 412 successful and 250 failed campaigns supporting plays in the United States: 
    -  Failed Kickstarter campaigns had much higher fundraising goals than successful Kickstarter campaigns.
    -  Louise is asking for more than twice the average successful Kickstarter goal, so this is concerning for the *Fever* campaign. 
    -  The mean and median pledged amounts for failed campaigns were much lower than the successful pledges, which indicates that failed Kickstarters were unsuccessful for reasons other than asking for too much money. The high asking price would have been a culprit in the failure of a campaign if the median pledged amount for the failed projects was around $3,000. Since the median is much lower, there must be another factor that kept people from pledging to those unsuccessful projects. 
    -  The mean of each distribution is around the third quartile, so the data follows similar distributions in each subset.
    -  The standard deviation is greater than the mean, which means everything below the mean is considered "close" to the center. 
    -  Some large values seem to be driving these distributions; all the standard deviations are over two folds of the IQR, except in the failed Kickstarters, where the standard deviation is closer to three times the IQR. Hence, there must be some failed Kickstarters with really high goals. 
    -  By filtering the designated Excel sheets for the failed and successful US campaigns, we found that the highest failed goal was $180,000 versus $100,000 for the highest successful goal. <br>
  
          | | Successful | Failed|
          |--- | --- | --- |
          **Mean Goal** | $5,049 | $10,554 |
          **Median Goal** | $3,000 | $5,000 |
          **Standard Deviation of Goal** | $7,749 | $21,968 |
          **Upper Quartile of Goal** | $5,000 | $10,000 |
          **Lower Quartile of Goal** | $1,500 | $2,000 |
          **IQR of Goal** | $3,500 | $8,000 |
          |  |  |  |  |
          **Mean Pledged** | $5,602 | $559 |
          **Median Pledged** | $3,168 | $103 |
          **Standard Deviation of Pledged** | $8,335 | $1,331 |
          **Upper Quartile of Pledged** | $5,699 | $501 |
          **Lower Quartile of Pledged** | $1,717 | $9 |
          **IQR of Pledged** | $3,982 | $492 |

13. We looked through donations to determine how much money people have pledged to campaigns historically and calculated the average donations based on the number of backers for each campaign to estimate the appropriate incentive to use in the *Fever* Kickstarter advertisement.The median of average donations for successful US plays' campaigns was $69 (Q3 = $105, Q1 = $52). <br>
    
      <img src="https://github.com/Magzzie/Kickstarter-analysis/blob/main/Resources/average_donations_box.png" width=50% height=50%>

14. While Louise is committed to creating a play in the United States, she is also interested in researching musicals in Great Britain for a future project with an estimated budget of £4,000. To present Louise with the big picture, we have created a box plot for the 26 British musicals, and it shows that:
      - The mean is considerably higher than the median of the campaign goals, which signifies that the distribution is heavily skewed to the right. 
      - The lower quartile of the pledges starts on the x-axis, indicating that 25% of the Kickstarter campaigns for musicals in Great Britain got no funding. 
      -  The mean campaign goal is around £4,000; this is outside the range of outliers for the amount pledged, so Louise should probably try to get her play produced for less than £4,000. 
      -  Half of the campaign goals are less than £2,000, which is just over the third quartile for amounts pledged. <br>
      
         <img src="https://github.com/Magzzie/Kickstarter-analysis/blob/main/Resources/musicals_boxplot_GB.png" width=50% height=50%>
  
## Conclusions & Recommendations
In conclusion, the crowdfunding dataset was extensive and provided valuable information about the different types of fundraising campaigns and their path to success. <br>The main takeaways from our analysis are: 
- Overall, theater-supporting fundraisers are the most popular, successful, and predictable type of campaign.
- Fundraisers to produce plays are the highest performing subcategory of theater, especially in the United States and Great Britain. 
- The best time of the year to initiate a theater-related campaign is between May and June.
- The average duration of successful fundraising was 30 days for theater across countries and 29 days for plays in the United States.
- Fundraising goals of less than $10,000 for plays hold better chances of success. 
- *Fever's* fundraising advertisement should encourage people to donate more than $70 to support this production.
- We stated that the failure of campaigns to support plays' production was probably not too high goals; however, the limited extent of the dataset did not allow for further identification of the causes of failure. 
- This dataset was limited to countries' information. It would be helpful to include further details about states and cities inside the United States where kickstarters took place to study the difference in support for theatrical productions based on the city. 

---
