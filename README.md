# Google_DA_CapstoneA_CaseStudy1
Title:  Case Study 1- How does a bike-share navigate speedy success? 
Author: Man Kit (Michael), Tsang 

Date Created : 6/2/2026
Last Updated : 8/2/2026

## Section 1: Ask 
[A clear statement of the business task]
### Basic Summary/Background of the Company 
Cyclistic is a bike-share program that features over 5,800 bicycles and 600 docking stations. It offers a large range of bicycles, including hand tricycles, cargo bikes, and reclining bikes, etc. Most riders or customers choose traditional bikes, with 8% choosing the assistive options. Users are more likely to ride for leisure, with 30% using the bikes to travel to work each day.

### Business Task 
Identifying the differences between annual members and casual riders in Cyclistic, supported with data and insights, and providing marketing strategies aiming to convert casual riders into annual members.

### Business Question: 
How do annual members and casual riders use Cyclistic bikes differently?

### Stakeholders: 
- Lily Moreno (Director of Marketing, responsible for the development of campaigns and initiatives to promote the bike-share program.) 
- Cyclistics Marketing Analytics Team (Responsible for collecting, analyzing, and reporting data that helps guide Cyclistic's marketing strategy.)
- Cyclistic executive team (Responsible for deciding whether to approve the recommended marketing program.)

## Section 2: Prepare 
[A description of all data sources used] 
### Description of Data Source and Data Organization 
The datasets that were being used in this case study were obtained from Motivate International Inc from the link: https://divvy-tripdata.s3.amazonaws.com/index.html

Only the data from the last 12 months were being used in this case study (2025 Feb to 2026 Jan). The downloaded files are monthly data in a zip file, which contains the CSV file with the information we needed for further analysis.

In each file, entries contain information as follows: "ride_id", "rideable_type", "started_at", "ended_at", "start_station_name", "start_station_id", "end_station_name", "end_station_id", "start_lat", "start_lng", "end_lat", "end_lng" and "member_casual".

### Credibity of Data
The data that is used is a fictional company data, however it is made for the purpose to appropriately answering the business question as mentioned. Also it is a primary data collected by the company, with comprehensive information of each entry. While the data being used in the case study is the data from the last 12 months, we are certain that the data is being current. And the data has been made available under the license https://divvybikes.com/data-license-agreement. We can confirm that the data being use agrees with the criteria or framework of ROCCC.

### Privacy of data 
The obtained data is public data where people are not able to connect pass purchases to credit card numbers to determine whether the casual riders live in the Cyclistic service area or they have purchased multiple single passes.

### Data Integrity 
To verify the integrity of data, numerical value of ride_length will be calculated and see if negative value or extreme values exist. Also, checking of missing value will be performed to ensure the quality of data.

### Use of Data 
Data cleaning and analysis will be performed to find out the differences in behaviors of different types of Cyclistic Users (members and casual), by grouping the same users type and compare the range and average of each riding session length in each group.

### Problem with Data
We have observed that there is inconsistency in the naming of file, for the 2026 Jan data, the file was faultily named as 2025. Also, missing data exist across all files, where data cleaning is needed before proceeding to the analyzing part of the case study.

## Section 3: Process 
[Documentation of any cleaning or manipulation of data] 
### Outline 
In this section, the tool used for the data processing is Microsoft Excel, for initial data exploration and transformation of all 12 datasets. Our primary focus in this case study is the behavior of casual riders and members. Therefore, we will ensure the consistency of the following columns: "ride_id", "started_at", "ended_at", and "member_casual". Entries with missing data in the mentioned columns will be removed since they are critical to our analysis.

### Documentation and Manipulaiton of Data
2 new columns are being created, which are 
- "ride_length", calculated by substracting the column "started_at" from column "ended_at", keeping the format as "hh:mm:ss", and 
- "day_of_week", calculated by using the weekday function on the "started_at" column. 

We created filters on all features, and entries with missing values that appears in "started_at", "ended_at", "member_casual" and "riders_id" will be removed from view. And we have removed the entries with "ride_length" less than 1 min, where 1 minute is set as a threshold, to eliminate the unwanted noise from the data, which can be caused by the unexpected events like flat tyres. 

The above filtering and column creation is performed on every excel file, while missing values in other columns will be ignore since they are not affecting the analysis of this case study. 


## Section 4: Analyze 
[A summary of your analysis] 
A python notebook has been created from scratch, for the analystics of the dataset.

### Organization of data
Dataset were being extracted using the pandas library. With the use of help functions, such as ride_len, reduce_cols, we have introduce new columns, filtering unwanted entries and removing columns that is not being used to save memories. 

New columns that were created are as follow: 
- Ride Length: Calculated by substractign the started_at from end_at, converting the data into minutes and removing entries with less than 1min duration. 

- Day of week: Introducing a new column that convert the datetime object into a Catrgorical data, that gives information of the day of week such as Monday, Tuesday etc. 

A for-loop is created to preprocess the data, creating new columns and removing unwanted data, then joining the datasets into a large single dataframe, named df_full. 

2 extra features were created after the datasets were being joined, which are month and hour data, directly extracted from the started_at feature. 

### Formatting of data 
We have encounter keyboard error in the convervation of datetime object, therefore the datatime object for start_at and end_at is converted using the format "ISO8601". 

### Discovery in data
We have noticed that there is a higher number of member count comparing to casual riders, however casual riders are more likely to have a longer average trip when compared to members. 

### Trends/ Relationship in data
We have created 6 plots in this section, which are the average duration and user counts on hourly data, weekly data and monthly data. 

We have observed that there are more member ride count on workdays (Monday - Friday) while the duration is conistent over the whole week. While there is a significant peak on Saturdays and Sundays for causal rders. These relationship suggested the different uses of bike hires for members and casual riders (work commute and leisure uses). 

There are also a significant spikes on the hourly data, where 8am and 6pm have a high number of member users of bike hiring, suggesting the work commute during rush hours. 

In the monthly data, we can observed a higher riders counts duration in summer months and sharp decrease in winter. This suggesting the seasonal behavior of bike hiring might have correlation with the season and weather. 

### Relationship with the Business Question 
With the above analysis, we have discovered some distinct behaviour of users, such as the purpose of bike hiring and the distribution of cycling preference or habit. With these, we can develope strategies that can target different users. 

## Section 5: Share 
[Supporting visualizations and key findings]
A Powerpoint presentation slide has been created for sharing insights and presentation purpose. 

## Section 6: Act 
[Your top three recommendations based on your analysis]

### Final Conclusion
The top 3 recommendation suggested based on our analysis are as follow: 
1. New member discount promotion event
Proposing a "New Member" discount event during the peak demand of Cyclistic bike for existing casual riders, which are summer season during July and August. In the event, offering discount rate or 2 weeks free membership for new members, would encourage more causal riders to convert into annual member. 

2. Member only perks 
Offering member-only perks such asdiscount rates for weekend rides, targeting the current casual rider who usually use Cyclistic bike for leisure and recreation purpose, would encourage the conversion into annual member. 

3. Bike reservation system 
Introduction of a bike reservation system, allowing members to book a bike  in advance to make the membership more attractive and convenient for members.

### Business Application of Insights and next action taken based on the findings 
From the data that have been processed and analyzed, the marketing team are able to find conclusions and insight from the data, and making better decision based on the evidence. 

The next step is to take the recommendation as suggested early, or review it and apply the best fitting policy that would benifit the company. 