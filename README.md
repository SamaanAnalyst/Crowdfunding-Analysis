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
6. Visualize campaigns' outcomes based on category and subcategory.

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
6. 

  
  
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

6.   The focus of the Louise is fundraising for theater in general, and plays specifically. In order to provide visualization of outcomes for the theater category in comparison with other categories in the dataset, we divided the *Category and Subcategory* column into *Parent Category* and *Subcategory* columns, then we built a pivot table classifying outcomes per parent category and  could be filtered based on country as well. We found that: 
    - There were 1,393 theater campaigns from all countries.
    - There were 525 successful theater kickstarters out of 912, in the United States. 
    - There were 258 successful theater kickstarters out of 359, in Great Britain. <br>
    ![Outcomes of Fundraising Campaigns in the United States Based on Main Category.](/Images/parent_category_outcomes_US.png)
8.   








## Conclusions & Recommendations




























