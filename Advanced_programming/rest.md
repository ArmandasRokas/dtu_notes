## Rest

### Intro

- Specifikationer for overførsel af data mellem klient og server med HTTP
- Core idea of REST is the resource. Everything you want to expose to outside world
- Each **resource is identified by a URL**, endpoint
- You retrieve that resource by sending a `GET` request to that URL

### Web service

- Software system designed to support interoperable **machine-to-machine** interaction over a network
- **Interoperable** - not platform depend. JSON

### REST vs RESTful API

- Representational state transfer (**REST**) er  **arkitektur for webservices** 
  - It should be state2less
  - It should access all the resources from the server using only URI
  - It does not have inbuilt encryption
  - It does not have session
  - It uses one and only one protocol that is HTTP
  - For performing CRUD operations, it should use HTTP verbs such as get, post, put and delete
  - It should return the result only in the form of JSON or XML, atom, OData etc. (lightweight data )
- **RESTful web services** is typically used to refer to web services **implementing such an architecture**.
  - There are clients and servers, separated by API boundaries over a network. **Clients** takes care of **presentation**, **servers** takes care of **logic** and **storage**
    - Klient: Presentation
    - Server: Business login og storage
  - Communication is **stateless**, every request contains all the information requiered to service that request
    - Et **request** indeholder nødvendig information til serveren
    - Et **response** indeholder det nødvendig for præsentation og opdatering af tilstand på clienten
  - Messages are **cacheable** by server, client or any proxy in between, or when not appropriate, mark themselves as not cacheable
  - A client cannot tell whether it is connected directly to the source of the service, there can be ane number of layers in between, facilitating load, balancing, caching and more
  - Data and functionality are accessed through a **uniform interface**
    - Ensartet ressource-struktur **URL**
    - Ensartet ressource-format **JSON/XML**
    - Serveren manipuleres gennem ressourcer

### HTTP reuqests

#### Methods

- POST 
  - create
- GET 
  - read one
  - read all
- PUT
  - Update
- DELETE
  - Delete

#### Headers

- Content-type
- Autherization
- Anden meta data

### Stateless vs stateful

#### Stateful

- Serveren holder styr på klinetens progession

#### Stateless

- Klienten holder styr på egen progression
- Serveren holder ikke på login status
- Serveren udsteder og validerer tokens
- (Returnerer næste valide link - HATEOS)

### Tykke vs tynde klienter

#### Tynde klienter

- Hurtigt opstart
- Hele brugergrænserfladen generes og sender
- sempel browser
- centrilisering af præsentations logik

#### Tykke klienter

- Skal downloade præentation logik
  - JQuery
- Kun data sendes


### JAX-RS 

- Java API for RESTful Web Servicess
- **Java** specifikation for overførsel af data mellem klient og server med HTTP
- Standardize the development of RESTful web services using J2EE. These specifications are just the definitions and not the concrete implementation

### Jersey

- Referencer Implements JAX-RS APIs 
- Jersey processerer annotationerne og udstiller webservices
- Pakker annoterede klasser ind i servlets
- Konfigureres via XML eller ResourceConfig

### Serialization 
Means to convert an object into that string, and deserialization is its inverse operation
#### Jackson

Jersey uses Jackson internally to convert Java objects to JSON and vice versa. That means JSON-mapper

- JSON key SKAL passe til POJO feltnavn - CaseSensitive!
- SKAL have setters til alle felter 
- SKAL have en tom constructor 
- Parse JSON objekter:

```java
import org.codehaus.jackson.map.ObjectMapper;

ObjectMapper mapper = new ObjectMapper();
Person perosnJava = mapper.readValue("{\"name\":\"Peter\", \"age\":23}", Person.class)
```



### Sync vs async

Synchronous" or "Asynchronous" is the **behaviour of the client** that is requesting the resource. It has nothing to do with REST webservice, its structure, or the supporting server. 

#### Synchronous behaviour

- Client constructs an HTTP structure, sends over the socket connection.
- Waits for the response HTTP.

#### Asychronous behaviour

- Client constructs HTTP structure, sends the request, and moves on.
- There's another thread that is waiting on the socket for the response. Once response arrives, the original sender is notified (usually, using a callback like structure).


> **Every browser api call is async, because the javascript engine runs in a single thread**. 
>
> <cite>[StackOverflow](https://stackoverflow.com/questions/47605737/how-to-make-a-synchronous-call-in-angular-5?rq=1)</cite>

### Postman

- HTTP klient 

### HTTP response status codes

- 1xx (Informational): The request was received, continuing process
- 2xx (Successful): The request was successfully received, understood and accepted
  - 200: OK
  - 201: Created
- 3xx (Redirection): Further action needs to be taken in order to complete the request
  - 304: Not modified
- 4xx (Client Error): The request contains bad syntax or cannot be fulfilled
  - 400: Bad request
  - 401: Unauthorized
  - 403: Forbidden
  - 404: Not found
- 5xx (Server Error): The server failed to fulfill an apparently valid request
  - Internal Server Error

### Fejlhåndtering i Jersey 3 måder

#### Response

- Svar med et Response

```java
public Response addIngredientJSON(Ingredient ingredient){
    if(map.putIfAbsent(ingredient.getId(), ingredient) != null){
        return Response.status(Status.BAD_REQUEST).
            enitity("ID is taken").build();
    }
    return Response.ok().build();
}
```

- Både success og error skal wrappes i Response

#### WebApplicationException

- Jersey RuntimeException - Unchecked
- Kanst en unchecked exception - Jersey klarer resten

```java
public void addIngredientJSON(Ingredient ingredient){
    if(map.putIfAbsent(ingredient.getId(), ingredient) != null){
        throw new WebApplicationException(
       	"ID is taken", Status.BAD_REQUEST); // status 400
    }
}
```



#### ExceptionMapper

- Applikationens egne Exceptions
- Mappes til HTTP fejl
- Exception mappes til Response af mapperen

```java
public void addIngredientJSON(Ingredient ingredient){
    if(map.putIfAbsent(ingredient.getId(), ingredient) != null){
        throw new InvalidIdException("Forkert kodeord");
    }
}

@Provider
public class InvalidIdExceptioMapper implements ExceptionMapper<InvalidIdException>{
    public Response toResponse(InvalidIdException ex){
        return Response.status(400).
            enitty(ex.getMessage()).
            type("text/plain").
            build();
    }
}
```



### References

- Documentation: https://idratherbewriting.com/learnapidoc/