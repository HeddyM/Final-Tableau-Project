# Final-Project-Tableau

## Project/Goals
1. To demonstrate ability to use Tableau to create visualizations that are interesting and engaging.
2. To use features of Tableau including creating table relationships, calculated fields, parameters, and sets.
3. To explore details of a data set with Tableau and use the tools to answer some questions about the topic selected.

## Process
### 1. Select an Option and Dataset

I selected Option 2 and chose the dataset Causes of Death - Our World in Data from the Kaggle website.

### 2. Determine Questions to Explore

From the dataset I was interested in a number of questions:
a. What are the leading causes of death globally and how do these compare with the leading causes of death in Canada?
b. What are the leading causes of death in countries where this is widespread poverty?
c. How do the different causes of death impact different countries and areas of the world?
d. Are there any interesting patterns, trends or surprising findings?
e. Have the numbers of deaths based on various causes of death increased, decreased or stayed the same globally over the last 20-30 years?

### 3. Review and Understand the Data 

I reviewed the data set and found that it provided data on the total number of deaths in each country between 1990 and 2019 based on 33 different causes of death. While there was interesting and useful data here I felt the need to find additional data  in order to answer some of my questions. I found and imported two additional data sets from the kaggle website and created relationships with the Causes of Death dataset using country code and year to connect them. The additional data sets were a World Population data set (needed to determine deaths per capita) and one called Extreme Poverty which provided data on the percentage of a countries' population living below the poverty line.

### 4. Prepare Visualizations

I prepared 13 worksheets that I used to create 5 dashboards each addressing one of my five questions.

### 5. Prepare presentation

I added the five dashboards to one Tableau Story which I used for my presentation so that I could maintain the interactivity built into the Tableau worksheets that I created.

## Results
As I indicated above I chose Option 2 using the dataset Causes of Death - Our World in Data.

### Additional Data sets
The Causes of Death data set includes total number of deaths by Year, Country and Cause. While comparing these between countries, obviously countries with greater population will have a greater number of deaths, so for some of the visualizations I felt the need to show deaths per capita. I found a World Population dataset (from kaggle) that I could create a relationship with and access the total population of each country.

The World Population dataset had a column for each year included in the dataset with headings like "2000 population" so I opened the data set in Jupyter Notebook and used Pandas "melt" commands to create a column with year and a column with total population. I used the following code to do this and saved the dataset for use in Tableau:

columns_to_keep = ['Rank', 'CCA3', 'Country/Territory', 'Continent', 'Area (km²)', 'Density (per km²)', 'Growth Rate', 'World Population Percentage']
population_pivoted_df = pd.melt(population_df, id_vars=columns_to_keep, var_name='Year', value_name='Total Population')
population_pivoted_df['Year'] = population_pivoted_df['Year'].str.split(' ').str[0].astype(int)
population_pivoted_df.to_csv('world_pop_clean.csv', index=False)

I also found and used two additional datsets. One called "Extreme Poverty" (also from kaggle) with a measure of poverty for each country (percentage of population below the poverty line) and one (from National Geographic) with life expectancy in each country. 

### Tableau tools and functions used in the creation of visualizations

I experimented a lot with Tableau and enjoyed using it. This was the most fun project of the three we have had and I did a bit more that what was required in the assignment.

Worksheet 1 - World Causes and Canada
Although I did a bit of manual labelling here to put the rank of causes for Canada on the graph I thought this was a good way to show the top causes of death in the world and then highlight in a different colour the top ten causes in Canada and rank them in order at the end of each line just to compare Canada to the world. I did this by filtering on Canada, noting the top ten causes in Canada, removing the filter and then manually colouring and labelling the causes in Canada on the world bar chart.

Worksheet 2 - Top ten causes poverty
I created a calculated field to identify all the countries that had 95% or more of the population below the poverty line. I referred in my presentation to these countries as countries with extreme poverty. I used this new boolean type field as a filter for this chart choosing those countries for which this condition (extreme poverty) was true.

Worksheet 3 - Poverty and Life Expectency
This was a simple scatter plot and I just filtered on year to give the most recent data in the datasets (2019).

Worksheet 4 - Poverty Map
I created another calculated field to indicate those countries with a life expectancy below 70 years of age (true or false). I created a parameter for this map so that I could display either countries with extreme poverty (blue dots are for countries where this is true) or countries with life expectancy below 70 (again blue dots represent countries where this is true). It is interesting becauses when you switch between these two measures the map does not change very much.

Worksheet 5 - Higher causes/No extreme poverty 
This is simply a chart that shows those causes of death that have higher deaths per capita for countries that were not classified as ones with extreme poverty for this project (ie. 95% or higher of population below the poverty line). This was an arbitrary distinction I chose for the purposes of the project, ie. I could have chosen 905 or 85% as a cut off. In order to determine deaths per capita, I used the total population of each country from that World Population dataset to create a calculated field called 'Deaths per capita'. 

Worksheet 6 - Global Death/capita Map
On this map I used the death per capita in the most recent year available (2019) to show the impact on different countries of different causes. The map is intereactive and as one clicks different causes in the menu the map changes highlighting countries where the death per capita is higher due to that cause. I did not use all 33 causes on death for this visualization but instead created a set from the list of causes including only 16 of those that I wanted to focus on in the presentation.

Worksheets 7-12
These were created for use in one dashboard that highlights 6 interesting causes by showing the total number of deaths by country (filtering to show only the top ten) between 1999 and 2019. There were some findings here that I wanted to highlight in my presentation such as highest number of deaths for the top worldwide causes of death (cardiovascular disease) would obviosly be in the most populated countries. I also wanted to show how the conflict and terrorism graphs showed distinct peaks like 9-11 in the US. I included two graphs that showed high number of deaths for causes that we rarely see in our part of the world ie. tuberculosis and malaris and two graphs showing the number of deaths in the US based on interpersonal violence and drugs.

Worksheet 13 - Change since 1990
I ended my presentation with a graph that I also created a set of causes for as a filter. It shows the trends in some of the causes of death ie. some on the rise since 1990 (Alzheimers & Drug Use disorders) , some on the decline (nutritional deficiencies) and some fairly constant (interpersonal violence and self-harm). Toggling through each of these causes shows an interesting visual of the trends in these areas, where we are making good progress as a world and where things seem to be getting "worse". Of course some of these trends like increases in Alzheimers could also be tied to an overall aging population and increases in life expectancy over time, but these are questions for another more detailed analysis.

### Some select findings based on my questions:
a. What are the leading causes of death globally and how do these compare with the leading causes of death in Canada?

These results can be found in the Dashboard titled World Causes and Canada that consists of just worksheet 1.

b. What are the leading causes of death in countries where this is widespread poverty?

Dashboard 2 titled Poverty/Life expectancy uses worksheets 2, 3, and 4 to communicate the relationship between poverty and life expectancy and causes of death.

c. How do the different causes of death impact different countries and areas of the world?

The global map created in worksheet 6 and the table in worksheet 5 are used in dashboard 3 (Global Deaths) to display the varied impact of specific causes of death in different parts of the world. 

d. Are there any interesting patterns, trends or surprising findings?

Dashboard 4 (Interesting Cause Cases) was created with worksheets 7-12 to allow me to make some interesting observations in my presentation and highlight areas for further analysis. 

e. Have the numbers of deaths based on various causes of death increased, decreased or stayed the same globally over the last 20-30 years?

I used on worksheet 13 in dashboard 5 called Better/Worse to wrap up my presentation with some trends and also highlight areas for further analysis if this project was ongoing. 

## Challenges 
I didn't have any significant challenges with this project. I thought it was pretty straighforward and it was easy for me to find additional data sets to build a better picture and address the questions that I had about Causes of Death when I chose this option. I think the biggest challenge I had was getting the layout of each dashboard correct and then having to fiddle a great deal with some of the individual elements to get them to look okay in the Tableau Story for my presentation. Getting the layout and size and placement of each element consistant across the dashboards and the story was no small feat.

## Future Goals
If I had more time I would have looked for more recent data to round out what I presented (2020-2022). I would have looked in more detail at countries with extreme poverty but higher life expectancies to learn more about what those country was doing to improve health outcomes for their populations. I would look for more data to corraborate some of the finding for the US in particular related to drug related causes and interpersonal violence>

Related to Tableau in particular I experimented a lot trying to find some visualizations where I could demonstrate use of other tools such as applying a trand line or doing some clustering but could not come up with anything where in this case these tools would have enhanced any of the visualizations I was creating to answer the questions that I had. With more time I could probably have come up with some way to display use of these Tableau features.
