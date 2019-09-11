## Spring boot

### Dispatcher servlet 

- plays key role
- handles all requests
- knows all different mappings
- which is the right controller to execute request?
- makes sure that the right method executed and the bean returned
- invokes conversion to `JSON` and returns

### Lifecycle
- Due to the annotation ``@RestController`, this class will be auto-detected through `classpath` scanning and the methods annotated with `@RequestMapping` annotation will be exposed as `HTTP endpoints`. When an incoming request matches the requirements specified by the `@RequestMapping` annotation, the method will execute to serve the request.
- Incoming request is handled by `DispatcherServlet`, which is the **front controller** and all incoming request goes through this single servlet . Spring Boot’s auto-configuration feature configures `dispatcherServlet`, a default error page, and other dependent jar files, when `Starter Web` included as dependency in `pom.xml`


#### Behind the scenes:

1.  Request for a resource 
```
Request: http://localhost:8080/users
Accept: application/json
```

2.  Dispatcher servlet will intercept the request for the resource
3.   The servlet determines the handler for the request
4. Spring checks which controller method matches the incoming lookup path of the “/users” request. Spring maintains a list of all mapping registries fetched from the `@RequestMapping` of the controller class and iterates the list to look for the matching method in the controller class implemented by the developer
5. after determining the right method it executes the controller method
6. Spring takes the ArrayList of users and uses the message converter method to marshal it to the type requested by the client. If the converted message is not available, then the client will get a 406 error.


### Testing 
https://stackoverflow.com/questions/12732182/ab-load-testing - testing
`ab -n 1000 -c 100 -k http://localhost:8080/routes`



### Concurrency 

- Hver request behandles parallelt, men én request behandles som én thread

https://spring.io/guides/gs/async-method/



### References

https://www.baeldung.com/spring-dispatcherservlet

https://dzone.com/articles/lifecycle-of-a-request-response-process-for-a-spri

https://www.e4developer.com/2018/03/30/introduction-to-concurrency-in-spring-boot/ - concurrency

https://dzone.com/articles/aws-lambda-with-spring-boot - AWS