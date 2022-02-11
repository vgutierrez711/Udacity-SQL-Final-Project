## Query 1
```sql
--Counting Number of tracks of each artist

SELECT Artist.Name AS 'Artist Name', Album.Title AS 'Album Title',count(Track.TrackId) AS 'No of Tracks' from Artist 
INNER JOIN Album ON Album.ArtistId = Artist.ArtistId
INNER JOIN Track ON Track.AlbumId = Album.AlbumId
GROUP BY Track.AlbumId
ORDER BY Artist.Name ASC LIMIT 10

```

## Query 2 
```sql

--Calculating Average spending of each customer

SELECT Customer.FirstName, Customer.LastName, AVG(Invoice.Total) AS 'Average Spending' from Invoice
INNER JOIN Customer on Customer.CustomerId = Invoice.CustomerId
GROUP BY Invoice.CustomerId
ORDER BY Customer.FirstName LIMIT 10


```

## Query 3
```sql

--Total Earnings

SELECT SUM(invl.UnitPrice) AS 'Earning of Album', Album.Title AS 'Album Title', Artist.Name AS 'Artist Name' FROM InvoiceLine invl
INNER JOIN Track ON Track.TrackId = invl.TrackId
INNER JOIN Album ON Album.AlbumId = Track.AlbumId
INNER JOIN Artist ON Artist.ArtistId = Album.ArtistId
GROUP BY Album.AlbumId LIMIT 10


```

## Query 4
```sql
--Average and Total time in Milliseconds artist Spend

SELECT Artist.Name AS 'Artist Name', AVG(Track.Milliseconds) AS 'Average Time Milliseconds',
	sum(Track.Milliseconds) AS 'Total Time Milliseconds'
FROM Track
INNER JOIN Album ON Track.AlbumId = Album.AlbumId
INNER JOIN Artist ON Artist.ArtistId = Album.AlbumId
GROUP BY Artist.ArtistId LIMIT 10


```