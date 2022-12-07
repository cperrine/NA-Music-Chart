# North American Music Chart
## Christian Perrine

### Description
##### This code begins with a large CSV containing a variety of information regarding country's top 200 music charts over the past several years, including the song title, artist, position on the chart, country, and total streams at the time. Then, using a csv reader the large csv is broken into 3 separate files, one for Canada, Mexico, and the United States. Using pymysql, the data is then imported into MySQL and stored within a table that can be queried. With all the information in the SQL table I performed some simple queries that could show simple statistical data like the most streamed artist in countries over a specific year, the most streamed artist or song, and then on an individual level you could search the number of top songs by a specific artist.
### Process
#### First, I found a large data set that held Spotify's music charts for various countries over the past 5 years. Seeing that the data file contained nearly 70 million rows worth of data, I decided to create subsets of the North American charts (Canada, United States, and Mexico). This was done using the csv function in python and iterating through the rows of data to find which ones listed the country as the ones above. I then had 3 separate subsets, one for each country, and then needed to combine them into one table within MySQL. Each CSV was uploaded to MySQL using pymysql and iterating over the csv and leaving out certain columns and specifying within the python code that each CSV was representative of the specific country. After all the data was uploaded to SQL, I queried a variety of things  from most streamed artists over a period of time, to the number 1 ranked songs by an artist.and then displayed them visually using pandas and matplolib.
### SQL Table Creation
#### CREATE TABLE `perrince_North America Charts` (
`Title` VARCHAR(50) NOT NULL,
`Rank` INT(3) NOT NULL,
`Date` DATETIME NOT NULL,
`Artist` VARCHAR(100) NOT NULL,
`Country` VARCHAR(30) NOT NULL,
`Chart` VARCHAR(10) NOT NULL,
`Number of Streams` INT(8) NOT NULL
) ENGINE=MyISAM DEFAULT CHARSET=latin1 AUTO_INCREMENT=1;

Data Insertion:
sql = '''INSERT INTO `perrince_North America Charts` (`Title`, `Rank`, `Date`, `Artist`, `Country`, `Chart`, `Number of Streams`)
VALUES(%s, %s, %s, %s, %s, %s, %s);'''
for row in data:
    tokens = (row['title'], row['rank'], row['date'], row['artist'], "Canada", row['chart'], row['streams'])
    cur.execute(sql,tokens)
*The country value is changed with each CSV
### Results
#### From this database one could query a variety of information. One thing that could be most interesting to compare is the differences in streaming preferences within each country in North America. 
