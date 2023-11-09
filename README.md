# Project-III.

## Overview

This repository is designed to find the ideal location for a Gaming company anywhere in the world taking into account the employees requirements. The company has 87 employees and this following scheme:

- Everyone in the company is between 25 and 40 and needs after-office venues.
- 30% of the employees have at least one kid.
- 20 Designers would like to work near Design companies for meetups and workshops.
- 20 Account Managers: they need to travel a lot.
- 15 Data Engineers.
- 10 Frontend Developers, 5 Backend Developers: they like to be near successful tech startups that have raised at least 1 million dollars.
- 10 Executives: they love Starbucks.
- 5 UI/UX Engineers
- 1 Maintenance manager who would like to be no more than 10km away from a Basketball Stadium.
- 1 CEO/President, he is vegan.
- Dog of the office, Dobbie needs a trim once a month.

## Table of Contents

1. [Data Source](#data-source)
2. [Methodology](#methodology)
3. [Objective and Weighting Criteria](#objective-and-weighting-criteria)
4. [Analysis](#analysis)
5. [Results](#results)
6. [Conclusions](#conclusions)
7. [Next Steps](#next-steps)
8. [Links](#links)

## Data Source

Mongo DB Dataset: This dataset contains all the information about companies arround the world that will be use to select the ideal office for the gaming company. The fields that will be use for this project are: Name of the company, Category code,  Number of employees, Total money raised, Country, City, Address, Zip code, Latitude and Longitude.
- [companies.json](data/companies.json)

Foursquare API: To find and collect venues like Starbucks, schools, restaurants, basketball stadiums, etc. 

Geocode API: To collect the longitude and latitude data from companies in the Dataset that didn't have this information and that were needed for the map plots.

## Methodolgy

- Problem Understanding and Criteria Weighting: decide how to approach the project and declare what are the requirements that will be more important to make the decision process more structured and easy to make. 
- Data Extraction: from the Mongo DB dataset, the Foursquare API and the Geocode API.
- Data Transformation: clean the data retrieved from databases and APIs to ensure consistency and accuracy.
- Data Analysis and Visualization: to decide the best neighborhood for the new office and visualize the data on a map.
- Decision Making:  Use the weighted criteria to score each potential location and select the one with the best score.
- Documentation and Reporting
- Libraries: 

    - MongoClient
    - Pymongo
    - Json
    - Pandas
    - Requests
    - Dotenv
    - Geopandas
    - Folium
    - Time

## Objective and Weighting Criteria:

- **Objective:**  choose one company to install the new office into their current venue  by making queries and filtering the database based on previously defined criteria.

- **Weighting Criteria:** I used the Moscow Prioritization method that helped me to categorize and weight my criteria. Finally, my goal was to  fulfill at least 90% of the requirements and not less than 60%.

    !['Moscow'](../project-III-geospatial-data/images/Moscow.png)

## Analysis:

1) Assumptions:

- **Startups:** for this project I am considering any company that has information in the total_money_raised field as they normally participate in funding rounds (the years of the company were not taken into account). 

- **Size of the office:** for this project I considered that the size of the company should be for a staff between 90 to 120 employees. 
According to IBIS world, a research firm, the number of people employed in the Video Games industry in the US increased 3.5% on average over the five years between 2017 and 2022. I will apply this criteria only after selecting the city, in case I get less than 10 companies to choose from or none of the options fulfill at least 60% of the employees requirements, the criteria will be discarded. 

2) Country Analysis:

For this part of the analysis I focused on answering the 3 following questions: 

    - What are the top 5 countries with most gaming companies?

    - What are the top 5 countries with most well-funded Startups (over $1M)

    - What are the top 5 countries with most design companies?

 Understanding where the gaming industry thrives can benefit the company with market opportunities, talent acquisition, benchmarking, partnerships and investment. 

 Additionaly, answering the other two questions can help to narrow the decision making process if they reinforce the results of the first and increases the possibilities of fulfilling the requirements of 63% of the company's employess (the developers and the design teams).

 The USA had the most companies in the three scenarios by far. For this reason, this was the selected country. 

3) City Analysis

Running a city analysis was highly beneficial to establish where were located all these companies that were find in the previous analysis. The USA is a very big country so selecting the right city was very important to fulfill all or most of the employees' requirements. 

Same questions were asked but this time they were focused on the  US cities. New York and San Francisco were the top 2 cities with more companies in the three scenarios. Palo Alto was the 3rd city with most companies in 2 of the 3 scenarios. 

New York, San Francisco and Palo Alto passed to the next stage.

4) Companies Analysis

After selecting the city, I applied the first filter criteria that was mentioned previously. The filters applied were the following: 

    - 1º Filter: Number of Employees (90 - 120)

 As mentioned before the number was calculated according to historical data of employment growth rate (IbisWorld).

    - 2º Filter: Category_Code = games_video

This fitler was applied with the logic that these offices would be already arranged in a way that is optimal for us, having to make minimal adaptations.

    -3º Filter: Number of companies of interest for employees in each city + Big Int Airport + Good transport system with connection to the Airport

For the last filter, the motivation was to increase the probabilities of finding the most locations to fulfill the employees requirements. Even when I was not looking for a location close to an Airport I wanted to guarantee a good access to a big international airport. 

6) Selected City

Finally, the selected city taking into account all the considerations described previously, was San Francisco. San Francisco is an important tech hub, cosmopolitan and well connected city. Moreover, it hosts one of the best airports in the US according to the Wall Street Journal ranking.

## Results

After the analysis, the pre-selected companies where located in the map. They were located in the same neighborhood, this wasn't necessarily expected. Then, all the venues of interest were added to the map as well and I added the circle polygon to the folium map to established first a 1000 meter radius for each company and then a 500 meter radius to visualize which option concentrated more venues close to it's location. 

In this case, I could find the company that meet all the requirements that were established at the beggining. The company selected was: Hi 5, located in the SoMa neighborhood in San Francisco.

## Conclusions

After a thorough analysis incorporating a multi-criteria decision-making approach, we have identified the optimal location for our new gaming company's office. 

Our decision was guided by a combination of critical factors such as proximity to schools and tech hubs, accessibility to travel infrastructure for our account managers, and the availability of amenities that align with our team's lifestyle preferences, such as nearby design communities for our designers, Starbucks for our executives, and recreational areas for our staff's wellbeing.

The chosen location not only supports our current operational needs but also positions us for future growth in the dynamic gaming industry landscape. It provides a strategic advantage by situating us in a vibrant community with access to a rich talent pool and potential collaborative opportunities.

## Next Steps
For a more accurate decision process, once I've selected the preferred city or cities, I would need to use geospatial libraries to calculate distances between points of interest and potential office locations. 

Creating a 2dsphere index allows to perform complex geospatial queries efficiently, such as finding the nearest companies, amenities, or services within a certain radius of a point.  

In a next step I would like to  create heatmaps to visualize the density the amenities in different locations.

Handdling the data within the MongoDB database would ensure that the geospatial coordinates I am working with are compatible with a wide range of geospatial databases and APIs, which makes it easier to integrate data from various sources and to use standard libraries for processing.

Finally, I would like to encapsulate and modularized my code.

## Links

Project Presentation (Canva): 
https://www.canva.com/design/DAFzfqbrDPc/19BTtDWsCogrjL4vtdMlpg/edit?utm_content=DAFzfqbrDPc&utm_campaign=designshare&utm_medium=link2&utm_source=sharebutton

SFO Airport information:
https://www.sfchronicle.com/sf/article/Why-SFO-was-just-ranked-the-top-large-airport-in-17601550.php#















