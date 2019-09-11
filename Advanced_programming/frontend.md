### HTML - HyperText Markup Language

- Definere sidens indhold og struktur
- consist of tags
- Deklarativ sprog

### CSS - Cascading Style Sheets 

- Definerer HTML-elemnternes udseende og placering (uafhængigt af indhold)
- Deklarativ sprog

- Typer:

  - **Element specifikt**

    ```html
    <h1 style="color:blue; margin-left:30px;"> 
    ```

  - **Indlejret**

    ```html
    <head><style> body{background-color: blue;}</style></head>
    ```

  - **I separat .css - fil**

    ```html
    <link rel="stylesheet" type="text/css" href="mystyle.css">
    ```

- Syntax:

```css
table {   					//inbyggede klasser eks. td
    border-width: 1px;    
}
#submitbutton {  			// ider #myid
    background-color: #f2f2f2 
}
.container {				// egne klassser .myclass
    position: relative;
}
```

### DOM

- Træ struktur

```
document
	|
	-- <html>
		|
		|-- <head>
		|		|-- <title>
		|				|
		|				"My title"
		|-- <body>
				|-- <h1>
				|	 |
				|	"A heading"
				|
				|-- <a>- href
					 |
					"Link text"
```



### JQuery 

- Javascript bibliotek til manipulation af hjemmesider
- Simplificerer 
  - HTML DOM manipulation
    - vise/skjule
    - skifte css
    - fange events
    - animation
    - .ajax
  - Event-håndtering
  - Animationer
  - Asynkrone kald
- Fjerne browserforskellen
-  poorly structured JS code (in many cases, powered by jQuery)



### AJAX

- **A**synchronous **Ja**vaScript and **X**ML
- I praksis bruges JSON i stedet for XML
- Hente data i baggrunden og manipulere DOM

![ajax](images\ajax.PNG)



- AJAX is a JavaScript method that enables asynchronous communication between the database and the server, that is receives data in background.

- Angular uses the AJAX technology to build single-page applications.  **The [`http`](https://angular.io/api/http/Http) class can get resources for you using AJAX**. 

- AJAX is a web browser technology independent of web server software



#### JQuery vs Angular
- Jquery is a library used for DOM manipulation whereas Angular is a framework.
-  Jquery has got nothing to do with the models; Angular is used to create SPA (single page applications).
-  Jquery does not have two-way binding features whereas Angular has key features like routing, directives, two-way data binding, models, dependency injection, unit tests etc.
-  Jquery becomes complex and difficult to maintain when the size of project increases but in case of Angular things are different as they are manageable at big project size.
-  Many a time happens that one has to write more codes in jquery to achieve same functionality whereas Angular reduces these criteria as the codes are generally are not lengthy as compared to jquery.

