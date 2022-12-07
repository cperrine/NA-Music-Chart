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
#### From this database one could query a variety of information. One thing that could be most interesting to compare is the differences in streaming preferences within each country in North America. For example you can query the most streamed artist over the time frame, a chart is included below as a reference.
![image](https://user-images.githubusercontent.com/95774587/206231561-55f50d09-15c9-4c49-9085-305c4ae81599.png)
#### Another interesting result was the ability to compare the streaming numbers for certain years based off the different countries. The differences in overall number of streams and the different artists that were atop each country was very interesting, especially when comparing the US to Canada since they speak the same language and have very similar pop culture tastes. Below is the most streamed artists by country, note that the United States is listed in billions while the others are hundreds of millions.
![image](https://user-images.githubusercontent.com/95774587/206238314-73798a86-8fef-4413-9985-565cff3fa39a.png)
![image](https://user-images.githubusercontent.com/95774587/206239324-bd6f0702-376b-4a06-9998-4ff88b8549c4.png)
#### Something interesting to note is that Juice WRLD passed away in the end of 2019, so you can see a lot of people tend to listen to someones music who recently passed, and on top of that his record label released an album that he had been working on, so you can see how different events regarding artists could impact their overall streaming numbers within a single year.


