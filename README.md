# An Analysis of Kickstarter Campaigns
Performing analysis on Kickstarter data to uncover trends, using Excel built-in functions and pivot charts. <br>
This project is focused on utilizing Excel functions and solution to analyze a big set of data, and the analysis report <br> is centered around deployed Excel skills and techniques. 

## Overview of Project
Louise is an up-and-coming playwright, who wants to start a crowdfunding campaign to help fund her play, ***Fever***. <br>
She has estimated a budget of over $10,000 and is understandably hesitant about jumping into her first fundraising campaign. <br>

Louise has provided us with an Excel data file that contains details about crowdfunding campaigns based majorly in the <br> the United States. <br>

Using Excel to analyze Kickstarters data will help us understand campaigns from start to finish and enable us to help Louise set her campaign to mirror other successful ones in the same category.

### Purpose 
We aim to organize, sort, and analyze crowdfunding data to determine whether there are specific factors that make a project's campaign successful. 

We will focus on comparing kickstarters concerning interest, finances, timing, location, and other confounding factors that may influence the trajectory of a campaign. Furthermore, we will provide visual representations of the data in full and of campaigns' outcomes, plus chronological and statistical analyses. 

The insights gained from this comprehensive analysis will help Louise plan her Kickstarter campaign and set it up for success. 

## Objectives
We will be performing data analysis on several thousands crowdfunding projects to uncover any hidden trends. <br>
1. Inspect data in the Excel file (crowfunding_StarterBook.xlsx).
2. Filter and sort the campaings based on their funds and outcomes. 
3. Provide visual aid to interpret outcomes quickly and efficiently.
4. Calculate the percentage funded for each campaign and create a color-graded reference.
5. Find the average donation for each campaing.  
6. Visualize campaigns' outcomes based on category.
7. Impact of country on fundraising interest and success.
8. Study the effects of timing and duration on outcomes.
9. Visualize campaigns' outcomes based on subcategory.

### Challenge Deliverables

## Resources
- Data sources: crowdfunding_StarterBook.xlsx, 
- Programs: Microsoft Excel.
- Online Tools: GitHub.

## Analysis & Code
The steps of our analysis of the crowdfunding campaign data along with code snippets are displayed below.   
1. Start the analysis by inspecting the dataset; looking at the extent, formatting and readability of the data.
2. Louise estimates that her play will cost about $10,000, so we apply **filters** on data in the *pledged* and *goal* columns <br>
to research projects with a similar monetary goal.
3. Color-code the *outcomes* column using one of the conditional formatting options called **Highlight Cells Rules**, and <br>
set each unique outcome `equal to` a color of choice.  
4. Create a new column of data called *Percentage Funded*, and <br>
  a. use the ROUND formula to find the percentage of a campaign's funding from the *pledged* and *goal* columns, as such `=ROUND(E2/D2*100,0)`.<br> 
  b. apply a color scale conditional formatting onto the *Percentage Funded* column, and format cells based on their <br>
  values from red for minimum to blue for maximum.
5. Create a new column called *Average Donation*, and use data from the *pledged* and *backers_count* columns. <br>
Employ the ROUND formula again, but modifying it to output 2 decimal points instead of none: `=ROUND(E2/L2,2)`.
6. In order to provide visualization of outcomes for the theater category in comparison with other categories in the dataset, divide the *Category and Subcategory* column into *Parent Category* and *Subcategory* columns, then we built a pivot table classifying outcomes per parent category that could also be filtered based on country as well. The specifics of the pivot table are as follows: *outcomes* in Columns, *Parent Category* in Rows, *outcomes* in Values, *country* in Filters.  Finally, we create a stacked column chart that shows which parent categories performed well and which ones did not. 
    - It is note-worthy that pivot charts in Excel are interactive if viewed inside the workbook and will adapt to the chosen filter as we use look through outcomes in different countries.
7. Filter the category-outcomes pivot table based on country, and create a stacked column chart for top two countries. 
8. Create a new pivot table in a new worksheet "Subcategory Statistics" and choose *country* and *Parent Category* to Filters, *outcomes* to Columns, *Subcategory* to Rows, and "outcomes* to Values. Then, choose a stacked column chart type.
9. The dates provided in the workbook need to be converted from UNIX timestamp to (mm/dd/yyyy) format; this is achievable through such formula `=(((J2/60)/60)/24)+DATE(1970,1,1)`
10. 

  
  
  ### Challenges and Solutions
  - **Percentage Funded** graded-color scale: after applying the conditional formatting, we noticed that we had to scroll through <br>
  a lot of data before spotting a color transition, which indicated the presence of one or more outliers in the dataset. 
      - **Solution**: Highlight the column again and click *Conditional Formatting* followed by *Manage Rules*, then <br> 
      *Edit* the current rule and adjust the *Maximum Type* to *Percentile*, then manually enter 90 as the value. 
  - **Average Donation** #DIV/0! Error: When scrolling through the average donations, we noticed an error occurring: `#DIV/0!` because every campaign would require a fundraising goal but wouldn't necessarily get any backers, and so naturally dividing by 0 would give an error result.
      - **Solution**: We fixed the #DIV/0 error by wrapping our ROUND formula with the IFERROR formula to output value of 0 instead of an error in the average column, like this `=IFERROR(ROUND(E2/L2,2),0)`.
  - 

## Results
1. The preliminary inspection of the Excel file (crowfunding_StarterBook.xlsx) reveals: 
    - There are 4,114 crowdfunding campaign records in 14 columns and 4,115 rows.
    - Out of 4,114 kickstarters, 3,038 (74%) were originated in the United States .
    - For each campaign, there are information about its name and description, category and subcategory, goal and pledged funds, outcome and number of backers, launch and end dates, in addition to country and currency.
    - Few examples of the information provided in the data file are: how much money each campaign will need to succeed in the *goal* column, and how much each campaign actually made in the *pledged* column. Furthermore,  the *outcomes* column shows us if the campaing met its goal; and finally, the *country* column lists the country in which the campaign was started. 
    - Data in the *goal* and *pledged* columns are appropriately formatted as currency; however, the date columns are in UNIX timestamp, and the category and subcategory information are attached. 
    
2. After filtering and sorting the data based on funds and outcomes we found that:
    -   The highest goal set for a crowdfunding campaign was ($100,000,000.00). 
    -   The highest pledged amount for a crowdfunding campaign was ($2,344,134.67).
    -   The highest successful goal set for a crowdfunding campaign was ($400,000.00). 

3.  The ability to visually process outcomes at a glance is very useful to campaign organizers. Hence, we have color-coded outcomes "successful" in green, "failed" in red, "live" in blue, and "canceled" in yellow.

4.  Many of the campaigns missed their goal amount by a small margin. By calculating the percentage funded for each campaign and applying a color scale, we could easily judge the outcome and determine how close a campaign came to reaching -and in some cases, exceeding their funding goal.   

5.  We looked through donations to determine how much money people have pledged to campaigns historically, and we calculated the average donation for each to estimate the appropriate incentive that should be advertised with the *Fever* kickstarter.

6.  Louise's focus is on fundraising for the theater. Hence, we analyzed the outcomes of 1,393 theater campaigns out of 4,114 records, and found that theater kickstarters were the most popular in all countries.<br>
   
      <img src="https://github.com/Magzzie/Kickstarter-analysis/blob/main/Images/parent_category_outcomes.png" width=45% height=45% align="center">
      
7. Then, we checked the impact of the country of origin on fundraising:
    - The two most prolific countries were the United States with 3,038 campaigns, and Great Britain with 604. 
    - Although theater kickstarters were the most popular in both countries, there was more diverse interest in the US.
    - Theater campaings in Great Britain were drastically more successful that all other campaigns.  
    - Theater fundraising success rate was higher in Great Britain than in the United States with 72% (258 of 359) and 58% (525 of 912), respectively. <br>

      <img src="https://github.com/Magzzie/Kickstarter-analysis/blob/main/Images/parent_category_outcomes_US.png" width=45% height=45%><img src="https://github.com/Magzzie/Kickstarter-analysis/blob/main/Images/parent_category_outcomes_GB.png" width=47.1% height=55%>
 
 8. We looked more deeply into subcategories and focused our tables and charts on **plays** since theatrial productions is the area of most relevence to the playwright out of all the theater subcategories. overall, campaigns to support plays were the most prevelant across countries. <br>
     
 
 
 9. Time considerations are very valuable when planning a public effort such as a fundraising; therefore, we analyzed campaigns dates to assess duration and time of year. <br>
    - 
 
 10. we apply extra filters: only "theater" in Category Statistics, only "plays" in Subcategory Statistics, only "theater" in Outcomes Based on Launch Date. 
- Do you notice trends between all the categories and subcategories?
-- Just by glancing at the data, we can determine that theater is a popular and successful type of campaign overall. 
-- By using filters, we can see that theater follows the overall trend: there is a spike of successful campaigns that began in June, by that tapers off by the end of the year.
-- By comparison, the data around technology campaigns reveals a different story; instead of one large spike, their trend lines are a bit all over the place and lest predictable. June seems to be a good month to launch a campaign!
The month that launched the most successful Kickstarter campaigns was May.
We create line charts to examine the trends in outcomes based on the time of the year. 
-- first we examine the outcomes of all campaigns in our dataset over the years, and we see that the months of May and June have a greater success rate overall. 
-- Second, we filter the chart to reflect only theater campaigns, and we notice that the above is true again for theater campaigns. 
-- ![Theater Campaigns Had Greater Success in May & June Months.](./Images/theater_outcomes_on_launchdate.png)
-- a line chart is best to reflect any trends in outcomes of campaings over time, and when examined in the Excel file, it's interactive and can be filtered in the same way you would filter the data table. 
-- 
-- ![May Month Launched Most Successful Campaigns.](./Images/outcomes_on_launchdate.png)
-- However, January, June, July and October all had roughly the same number of failed campaigns launched. 
--- This can be determined by examining the points along the trend lines of the chart. 






## Conclusions & Recommendations




























