# pandas-challenge
I decided to do the Heroes of Pymoli homework because I am very interested in the marketing and business insights side of data analysis, and I thought this would be a good project to help get me started on that path.

My conclusions are written at the end of the file.

After importing dependencies and reading the csv file as purchase_data, the first thing I did was call the .columns function so knew what data I was working with and how to call it.

### Player Count

* Total Number of Players

- I calculated this by first counting the number of unique players using .value_counts on the SN column in purchase_data, then printing the length of that list.

### Purchasing Analysis (Total)

* Number of Unique Items
- I calculated this by counting the number of unique items using .value_counts on the Item ID column in purchase_data, then setting the length of that list as a variable called unique_items.

* Average Purchase Price
- I calculated this by finding the average price per item using .mean  on the Price column in purchase_data, then setting the result as a variable called avg_price.

* Total Number of Purchases
- I calculated this by counting the total number of purchases using .value_counts on the Purchase ID column in purchase_data, then setting the length of that list as a variable called total_purchases.

* Total Revenue
- I calculated this by finding the total amount spent on all items using .sum on the Price column in purchase_data, then setting the result as a variable called total_revenue.

- I then created a new data frame called pa_df with appropriate column titles, and plugged in the variables containing the results of my calculations.
- Finally, I cleaned up the formatting where appropriate.

### Gender Demographics

* Percentage and Count of Male Players
* Percentage and Count of Female Players
* Percentage and Count of Other / Non-Disclosed

- Since some players made multiple purchases, but I needed a list where no one was listed multiple times I first created a subset of purchase_data called subset, that consisted of only unique players by using .drop_duplicates in the SN column in purchase_data.
- I then used .groupby on the Gender column in subset creating gender_groups.
- I totalled the number of players in each group using .count on gender_groups, resulting in the number of players for each gender category being stored in the variable gender_totals.
- I found the percentage each gender group made up of the total number of players by dividing the gender_totals by the length of the total_players and multiplying by 100.

- I then created a new data frame called gender demographics with appropriate column titles, and plugged in the variables containing the results of my calculations.
- Finally, I cleaned up the formatting where appropriate.

### Purchasing Analysis (Gender)

* The below each broken by gender: 

- Since most of these calculations did not need a list of unique players, I used .groupby for Gender again, this time on purchase_data, creating purchases_by_gender (with accurate purchase totals, but some players listed multiple times).

  * Purchase Count
  - I found this by using .count on the Purchase ID column in purchase_data for each gender group, and stored the results as total_purchases_bg.
  * Total Purchase Value
  - I found this by using sum on the Price .column in purchase_data for each gender group, and stored the results as total_price_bg.
  * Average Purchase Price
  - I found this by using dividing total_price_bg by total_purchases_bg for each gender group, and stored the results as avg_price_bg.
  
 
  * Average Purchase Total per Person by Gender
  - For this last calculation I needed to go by unique player, so I divided total_price_bg by gender_totals and stored the results as avg_spent_bg.

- I then created a new data frame called purchasing_analysis_bg with appropriate column titles, and plugged in the variables containing the results of my calculations.
- Finally, I cleaned up the formatting where appropriate.

### Age Demographics

* The below each broken into bins of 4 years (i.e. <10, 10-14, 15-19, etc.):

- I first broke up the players into bins by age, using the .cut function on subset (containing only unique players).
- I created a new column called Age Range in subset, and grouped the players by it using .groupby, creating grouped_by_ar.

- I totalled the number of players in each group using the .count function on grouped_by_ar, resulting in the number of players for each gender category being stored in the variable age_totals.
- I found the percentage each age group made up of the total number of players by dividing the age_totals by the length of the total_players and multiplying by 100.

- I then created a new data frame called age_demographics with appropriate column titles, and plugged in the variables containing the results of my calculations.
- Finally, I cleaned up the formatting where appropriate.

### Purchasing Analysis (Age)
* The below each broken by Age Group:

- Since most of these calculations did not need a list of unique players, I repeated the binning, .cut, groupby Age Range process again, this time on purchase_data, creating purchases_by_age (with accurate purchase totals, but some players listed multiple times).

  * Purchase Count
  - I found this by using .count on the Purchase ID column in purchase_data for each age group, and stored the results as total_purchases_ba.
  * Total Purchase Value
  - I found this by using .sum on the Price column in purchase_data for each age group, and stored the results as total_price_ba.
  * Average Purchase Price
  - I found this by using dividing total_price_ba by total_purchases_ba for each age group, and stored the results as avg_price_ba.
  
 
  * Average Purchase Total per Person by Age Group
  - For this last calculation I needed to go by unique player, so I divided total_price_ba by age_totals and stored the results as avg_spent_ba.

- I then created a new data frame called purchasing_analysis_ba with appropriate column titles, and plugged in the variables containing the results of my calculations.
- Finally, I cleaned up the formatting where appropriate.

### Top Spenders
* Identify the the top 5 spenders in the game by total purchase value, then list (in a table):

  * SN
  - First I used .groupby on the SN column in purchase_data to create spenders_group, allowing me to run colculations on each spender that would encompass all of their purchases.

  * Purchase Count
  - I used .count on the Purchase ID column in spenders_group, and stored the results as total_purchases_bs.
  * Average Purchase Price
  - I used .mean on the Price column in spenders_group, and stored the results as avg_purchases_bs.
  * Total Purchase Value
  - I used .sum on the Price column in spenders_group, and stored the results as total_value_bs.

  - I then created a new data frame called top_spenders with appropriate column titles, and plugged in the variables containing the results of my calculations.
  - I then created a new dataframe called sorted_spenders using .sort_values that presents the same data but sorted by Total Purchase Value in descending order.
  - Finally, I cleaned up the formatting where appropriate.



### Most Popular Items

* Identify the 5 most popular items by purchase count, then list (in a table):
  * Item ID
  * Item Name
  * Purchase Count
  * Item Price
  * Total Purchase Value

### Most Profitable Items

* Identify the 5 most profitable items by total purchase value, then list (in a table):
  * Item ID
  * Item Name
  * Purchase Count
  * Item Price
  * Total Purchase Value

As final considerations:

* You must use the Pandas Library and the Jupyter Notebook.
* You must submit a link to your Jupyter Notebook with the viewable Data Frames.
* You must include a written description of three observable trends based on the data.
* See [Example Solution](HeroesOfPymoli/HeroesOfPymoli_starter.ipynb) for a reference on expected format.
