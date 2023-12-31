# Cyclistic Bike-Share Analytics: Uncovering Rider Behaviors


## Project Overview

This project utilizes a **spreadsheet** as the main tool for analysis and visualization. In the conclusion, a slideshow visualization for stakeholders will be provided.

### Preliminary Notes

Before diving into the analysis, please note:
1. This file represents an analysis case study of my approach, with visualizations for stakeholders presented at the end.
2. Due to the large volume of data, the analysis is confined to January 2023 data (19,032 rows).
3. The data, provided by the course, is presumed reliable. In practice, we must avoid for bias and make sure data integrity.

## Step 1: Background Information

Key information includes:
- **Cyclistic**: A bike-share company based in Chicago with a range of bicycles, including accessible options.
- **Users**: Primarily Casual Riders (single-ride or full-day pass users) and Members (annual membership holders).
- **Goal**: To convert Casual Riders into annual Members, enhancing growth and profitability.

## Step 2: Ask

The guiding question for the analysis is:
- How do annual members and casual riders utilize Cyclistic bikes differently?

Note: The focus is on usage patterns, not on the reasons for purchasing memberships.

## Step 3: Prepare

Considerations for the analysis include:
- **User Type**: Distinguishing between Member and Casual users.
- **Trip Duration**: Calculating average ride length for **both** user types, based on start and end times.
- **Day of the Week**: Analyzing weekday usage patterns for both user groups(Exclude weekend).

Limitations: The analysis is constrained by the dataset provided. For instance, ride frequency and location data, which could offer further insights, are not available. In real world, we need conisder those factors, too.

## Step 4: Process

Assuming data reliability(provided by course), we need data cleansing to rectify mismatches, empty cells, and capitalization errors, etc. For example, cleaning the casual_member columns can be done using the formula `=IF(ISBLANK(M2), "unknown", IF(OR(LOWER(M2)="casual", LOWER(M2)="member"), LOWER(M2), "invalid"))`. Additionally, start and end times are reformatted for clarity and ease of analysis.

## Step 5: Analyze

The analysis begins with calculating trip durations and categorizing days of the week into weekdays or weekends. 

#### Trip Duration
The start time is column C and end time is in column D.

I use `=MINUS(D2, C2)` to find trip duration, and apply them to all data, name Trip Duration in column R.

Next, I use `=IF(N2 = "casual", MINUS(D2, C2), "")` to find Trip Duration for Casual Riders, and apply to all data, name "Trip Duration(Casual)".

And, use `=IF(N2 = "member", MINUS(D2, C2), "")` to find Trip Duration for Member riders, and apply to all data, name "Trip Duration(Member)".

#### Day of the week

I use `=WEEKDAY(C61872, 1)` to find which days a user rides a bike and apply it to all data.

Next, Exclude Weekend: `=IF(OR(W2=1, W2=7), "weekend", "weekday")`, create a new columns name “Day of week(Exclude weekend)”

Next, Separate Day of the Week for Casual and Member

create a new columns names “Day of Week (Casual)”: `=IF(AND(N2 = "casual", X2 = "weekday"), W2, "")`

create a new columns names “Day of Week (Member)” : `=IF(AND(N2 = "member", X2 = "weekday"), W2, "")`


Now, we have complete calculate data, and we have following columns:
- Member_casual(Cleaned)    
- Trip Duration	
- Trip Duration(Casual)	
- Trip Duration(Member)		
- Day of week	
- Day of week(Exclude weekend)	
- Day of Week(Casual)	
- Day of Week(Member)

### Creating a Pivot Table

A pivot table is created to facilitate data visualization, structured as follows:
- Rows: "Day of Week(Exclude weekend)"
- Columns: User Type("member_casual(Cleaned)")
- Values: "Trip Duration" (sorted by average)
- Filters: "Day of Week(Exclude weekend)" column, and only show “weekday”

## Step 6: Share

Here is the pivot table:

<img src="./Pivot Table.png" width="900" alt="Sample Output"/>

From the pivot table, we can see that: 

- Casual riders have an average trip duration of 00:12:52 (12 minutes and 52 seconds).
- Members have an average trip duration of 00:09:59 (9 minutes and 59 seconds).
- The overall average trip duration across both user types is 00:10:37 (10 minutes and 37 seconds).

From the pivot table results, we can conclude the following about the usage of Cyclistic bikes by annual members and casual riders during weekdays in January 2023:

**Casual riders have longer average trip durations than members.** This could indicate that casual riders may use bikes for leisure activities or less frequent but longer exploratory rides.
Members have shorter average trip durations, which might suggest more routine and possibly utilitarian use of the bikes, such as for commuting or running errands.

Suppose we want to take a further step. In that case, Exploring data for other months can reveal whether these patterns hold throughout the year or are specific to January (which can be affected by weather, holidays, etc.). Repeat steps in this docs.

**Note:** Because GitHub can’t upload files more than 25MB, so I will attach my spreadsheet [here](https://docs.google.com/spreadsheets/d/1l3l_s-4j9nLB470mk7upWz7-7tcDf6BK1gQl8j9GnWE/edit?usp=sharing).

Also, I use HTML files instead of CSV and upload them to Git Hub. Clink <a href="./Jan 2023.zip" download>here</a> to view.

### Solution
The analysis shows that the average trip duration for casual riders is longer than that of members; here are some suggestions we can consider: 
- Targeted marketing campaigns
- Enhanced user experience
- Enhanced user experience
- Data monitoring

## Step 7: Act

It’s visualization time!

The final step involves presenting the findings to stakeholders. The presentation will be available in both presentation and PDF formats, with links to be added.

Presentation mode: click [here](https://gamma.app/docs/Cyclistic-Rides-Unveiling-the-Journey-Patterns-of-Casual-Riders-v-bi4laouaw9tbfj3).

PDF mode: <a href="./Cyclistic-Rides-Unveiling-the-Journey-Patterns-of-Casual-Riders-vs-Members.pdf" download>here</a>.

## Step 8: What's Next...
If we need to go into a deeper exploration, we can:

- Why would casual riders buy Cyclistic annual memberships? 

- How can Cyclistic use digital media to influence casual riders to become members?


## End of Analysis