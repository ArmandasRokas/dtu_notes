### Arkitektur

- Data Access Layer
- Business Logic layer
- Presentations Layer - Client/server-side

```
-------------------------
| Database server       |
-------------------------
		|
-------------------------
| Web-server/App server |
-------------------------
| Data Access Layer     |
| Business Logic Layer  |
| Presentations Layer   |
-------------------------
		|      HTML/CSS
-------------------------
| Klient/Browser        |
-------------------------
| View                  |
-------------------------
```

#### Server side rendering
- JSP/PHP/ASP
#### Client side
- JS og API(REST)


### Applikations-optimering
- Connection
	- TCP/IP handshake
	- MySQL handshake
- Connection pooling
	- Out of memory
- Caching 
	- Gamle data

### ORM
- Automatiseret konverting fra Objekter til Skema/SQL
- Java de facto standard: Hibernate