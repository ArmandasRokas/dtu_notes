## User Repository

### getLocations
```SQL
SELECT id, street_name, street_number, city, country, ST_X(spatial_point) AS X, ST_Y(spatial_point) AS Y
        FROM user_location
        WHERE user_location.user_id = ?
```

- Ekstrakts `x` og `y` fra `spatial_point` med henholdvis `ST_X` og `ST_Y` funktioner.

### getUser by username

```SQL
SELECT *
FROM user
WHERE user.user_name = ?
```

- Fejl: der er ingen index på userName i user tabel

## Route Repository
### getRoute
```SQL
SELECT 
, route.title, route.date, route.distance, route.duration, route.description, route.status, route.max_participants, route.min_participants, 
	COUNT(run.route_id) AS participants_number
	FROM route LEFT JOIN run 
	ON route.id = run.route_id 
	WHERE route.id = ? 
```

- `LEFT JOIN` vil give ruten selv om der ingen run. Dvs. så man kan tælle null værdi, som vil give 0.
### getRouteList

```mysql
SELECT route.id AS id 
	FROM route 
	WHERE `date` >= ? 
	ORDER BY `date` DESC 
	LIMIT ? 
```
- mangler index på `date` i route tabellen 
- `DESC` DESCENDING
- `LIMIT` . retrieves a subset of record.  Der er også en mulighed at tilføje`offset`, dvs. fra hvilken plads der skal record hentes. 
- Hvordan skal du hente resterende route, hvis du ikke kender offset
### getMostPopular routes
```SQL
SELECT COUNT(run.route_id) AS participants_number, run.route_id, route.`date`
	FROM run JOIN route ON run.route_id = route.id 
	WHERE route.`date` >= ? 
	GROUP BY run.route_id 
	ORDER BY COUNT(run.route_id) DESC 
	LIMIT ?
```

- Most popular defineres, at der findes flest run for denne route
- `ORDER BY COUNT(run.route_id)` could be changed to `ORDER BY participants_numer`

```SQL
    SELECT COUNT(run.route_id)
    FROM run JOIN route ON run.route_id = route.id
    GROUP BY run.route_id;
```

- `GROUP BY` statement is often used with aggregate functions (`COUNT, MAX, MIN, SUM, AVG`) to group the result-set by one or more columns

## RunRepository
### addCheckpointIfValid
```sql
INSERT INTO checkpoint (run_id, waypoint_index, visited_timestamp)
	SELECT run.id, `index`, now(6)
	FROM waypoint
	JOIN run ON waypoint.route_id = run.route_id
    WHERE run.id = ? AND 
    ST_Distance(spatial_point, ST_GeomFromText( ? )) <= ?;
```

- returnere alle waypoints igennem ruten  med join
- waypoints har `spatial_point`  så der tjekkes alle som er under den defineret afstand
- der skal helst være 0-1 waypoints som bestå denne condition

### getLatestCheckpoints 

```sql
SELECT MAX(visited_timestamp) AS visited_timestamp
	FROM checkpoint
	WHERE checkpoint.run_id = ? AND 
	checkpoint.waypoint_index = ?
	GROUP BY checkpoint.waypoint_index
```

- hver waypoint kan have index fra 1til MAX_INT
- dvs. alle skal være unikke for den ene rute
- så hvis vi gruppere dem i forhold til deres index og få max() timestamp, fordi jeg tror, art vi gruppe få vi max timestamp for hver index

### getMissingWaypoint

```sql
SELECT ST_X(spatial_point) AS X, ST_Y(spatial_point) AS Y, `index`
	FROM waypoint JOIN run 
	ON waypoint.route_id = run.route_id 
	LEFT JOIN checkpoint ON waypoint.`index` = checkpoint.waypoint_index AND checkpoint.run_id = run.id 
	WHERE run.id = ? AND 
	visited_timestamp IS NULL
```

- der bruges ST_X og ST_Y funktioner til af få nummeretisk værdi af spatial_point. 
- her joines run og waypints igen med route_id for at få waypoints tilhørende til denne run. 
- bagefter der left joines til at 
- der joines to gange fordi der skal bruges run.id. dvs checkpoint alene ikke kender til 