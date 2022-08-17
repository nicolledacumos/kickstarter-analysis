# kickstarter-analysis
Performing analysis on Kickstarter data to uncover trends

# Kickstarting with Excel

## Overview of Project
This analysis is meant to display the relationship between the outcomes of various kickstarter campaigns and their launch dates and funding goals--noting specifically whether theater and play campaigns succeeded, failed, or were canceled.

### Purpose
The purpose of this analysis was to find trends in how well a play fared based primarily off launch date, as well as to examine the number of plays that succeeded, failed, or were canceled. 

## Analysis and Challenges
For this project, I analyzed the outcomes based on plays' launch dates, and the outcomes based on the goal amount of pledged donations. Outcomes in this instance are referred to as 
>succeeded, failed, or canceled.

### Analysis of Outcomes Based on Launch Date

To analyze the outcomes of various plays based on their launch date, I had to first convert the dates based off the data in the launched_at column of the Kickstarter dataset. I used the formula
```
=(((J2/60)/60)/24)+DATE(1970,1,1)
```

From there, I created another column titled 
>Years


under which I listed solely the years the listed kickstarters were created. I used the following formula, which one may also convert through excel's date function.
```
=YEAR(S2)
```
I then created another sheet titled
>Theater Outcomes by Launch Date

Which holds the Pivot Table and Pivot Chart used to further display trends in success, failures and cancelations for various plays.

In this sheet, I filtered the data based on Years and the Parent Category and set the date created conversion on the x axis and the number of outcomes on the y-axis. I used the count of outcomes as the values for the Pivot Table and Pivot Chart. I then filtered the Parent Category to display only data related to theater kickstarters, displayed only the months for the date created conversion, and ensured that the data displayed in descending order: successful, failed, and canceled.

![Screen Shot 2022-08-17 at 1 03 29 PM](https://user-images.githubusercontent.com/110862583/185210668-933cbad1-cff8-46f2-9ee8-2ad10c0e9eb4.png)


From there, I created a Pivot line chart based off the data shown in the PivotTable. 

![Theater_Outcomes_vs_Launch](https://user-images.githubusercontent.com/110862583/185210448-121ac97a-919f-4220-97d8-b12a2553d755.png)


### Analysis of Outcomes Based on Goals
To analyze the outcomes of plays based on goal amount of pledged donations, I created another sheet titled 
>Outcomes Based on Goals.

In this sheet, I began by creating a column outlining various goal ranges:
![Screen Shot 2022-08-17 at 1 02 51 PM](https://user-images.githubusercontent.com/110862583/185210547-c52cf797-fad3-4f6d-9aba-a86695b43d93.png)


Then, I created columns titled
>Number Successful, Number Failed, Number Canceled, Total Projects, Percentage successful, Percentage Failed, and Percentage Canceled.

To calculate the number of plays that succeeded, I used the following formula:
```
=COUNTIFS(Kickstarter!$D:$D,"goal range",Kickstarter!$F:$F, "successful", Kickstarter!$R:$R, "plays")
```
The COUNTIFs function allowed me to view the number of plays that were successful based off the given goal range. For this, goal range was replaced with the corresponding range listed in the A column. Additionally, I made sure to set certain parameters to ensure my date only calculated successful plays. To do this, I included 
```
Kickstarter!$F:$F, "successful", Kickstarter!$R:$R, "plays"
```

in my formula in order to account for the plays that were successful.

As the goal ranges changed, I had to include different limits. For ranges that had start and end numbers, I included 
```
Kickstarter!$D:$D,">=lower bound",Kickstarter!$D:$D,"<=upper bound"
```
in which lower and upper bound were replaced by the corresponding numbers listed in the Goal column.

I used the same formulas for the Number Failed and Number Canceled columns; however, the term after
```
Kickstarter!$F:$F
```
changed based off of whether i was calculating failed or canceled plays.

I then calculated the total number of projects by using the sum formula:
```
=SUM(BX:DX)
```
In which X was replaced by the corresponding cell numbers. 

From there, I calculated percentage successful by using the following formula:
```
=BX/EX
```
with X as the cell number.

Because excel did not immediately change the result to percent, I used the percentage function found in the home toolbar to convert the decimal to a percent.

For Percentage Failed, I divided the C column by the E column; for Percentage Canceled, I divided the D column by the E column.

With this data, I created a line chart to display the percent of various outcomes based on the goals. 
![Outcomes_vs_Goals](https://user-images.githubusercontent.com/110862583/185210747-5041737e-3571-401e-83a3-90fda878ce7e.png)



### Challenges and Difficulties Encountered
My primary difficulty with this challenge was finding the number of outcomes based on goals. Because of how specific the data needed to be, I had to ensure that the data was limited to plays only. I also had to ensure that the upper and lower bounds were set correctly in order to ensure the charted data would be accurate. Additionally, charting the data was a bit difficult because I had to select certain columns to ensure that the chart would not be cluttered with extraneous information.

## Results

What are two conclusions you can draw about the Outcomes based on Launch Date?

- Theater kickstarters typically fare well in the summer months: May-July.
The number of canceled and failed theater kickstarters are proportionally high to the number of successful plays in the winter time: November-March.

What can you conclude about the Outcomes based on Goals?

- No plays were canceled based off pledge goals and plays that had lower goals were typically successful.

What are some limitations of this dataset?

- I believe including theater kickstarters from all years may have skewed the date slightly. Perhaps more specific data could be calculated for a single given year rather than all years. 

What are some other possible tables and/or graphs that we could create?

- We could perhaps create a pie chart to better show proportionality in regards to successful, failed, and canceled plays. 
