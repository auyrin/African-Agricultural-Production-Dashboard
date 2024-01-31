# African-Agricultural-Production-Dashboard
A dashboard about African crop production. here i also clean and transform the dataset to be something usable.
the dataset was gotten from data.world

### metrics to be displayed:
- total production, area harvested, and yield   ----> total values displayed
- top 10 crops produced                         ----> bar chart
- top 5 crops with the highest yields           ----> bar chart
- production trend                              ----> line chart
- production by country                         ----> filled map   

## methodology:
#### data cleaning and transformation
- I filtered out the columns i didn't need
- then i replaced null values with zero using the replace values function
- each year was a different column. i unpivoted them to convert them to just two columns (year and values)
- i removed Y from the year column and converted to date format
- i grouped by each element (production, yield and area harvested) and made them their seperate tables
- I created a date table and connected it to my newly created tables.
- I realised that my dataset did not have enough geo data for for me to plot a choropleth map with, so i enriched my dataset with geolocation data that i scraped from geocountries.com.
- after scraping the data i loaded it on power query and realised that we had blanks and nulls for the both south sudan and ivory coast. i created conditional columns in other to manually fill their coordinates.
- then i connected it to my dataset via country name, then change them to there various data categories.
#### calculations
- I created a new table for my measures/calculations, in which i created the columns for the % change in production, yield and area harvested over the years using the switch function, and some variables.
  - variables 1: previous year value, which i got with the sameperiodlastyear function
  - variable 2: percentage change per year, which i got by dividing the difference of this year and last year by last year. then used the format function to display their values in percentages.
- then i created a field value to help me color code these changes (positive -> green, negative -> red, neutral -> gray). again using the switch function.
## problems
- some of the rows have names like roots and tubers instead of potatoes/cassavas/yams etc.
  - while i could change every other root and tuber to be be labeled as such instead of their respective names, I considered it as unnecessary for what i was trying to achieve
  - also changing every different crop to there respective blanket name would have been tiresome at the time of making this dashboard, so i decided to skip it.
- some countries have blank/zero production according to our dataset.
  - i could have removed those countries from our dataset, but decided not to. so as not to compromise the intergrity of my data by accident.
