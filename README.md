# North American Music Chart
## Christian Perrine

### Description
##### This code begins with a large CSV containing a variety of information regarding country's top 200 music charts over the past several years, including the song title, artist, position on the chart, country, and total streams at the time. Then, using a csv reader the large csv is broken into 3 separate files, one for Canada, Mexico, and the United States. Using pymysql, the data is then imported into MySQL and stored within a table that can be queried by the user.
### Process
#### First, I found a large data set that held Spotify's music charts for various countries over the past 5 years. Seeing that the data file contained nearly 70 million rows worth of data, I decided to create subsets of the North American charts (Canada, United States, and Mexico). This was done using the csv function in python and iterating throuhg the rows of data to find which ones listed the country as the ones above. I then had 3 separate subsets, one for each country, and then needed to combine them into one table within MySQL.
