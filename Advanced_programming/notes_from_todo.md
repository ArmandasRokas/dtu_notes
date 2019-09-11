```
Retrieve all Todos for a user
GET /users/{user_name}/todos

Delete a todo of a User
DELETE /users/{user_name}/todos/{todo_id}

Edit/Update a Todo
PUT /users/{user_name}/todos/{todo_id}

Create a new Todo
POST /users/{user_name}/todos


```

- Todo on clients side. Angular do not need username, because it is already assigned to user. 



### Handling Error

```typescript
  getWelcomeMessageWithParameter() {   
  	this.service.executeHelloWorldServiceWithPathVariable(this.name).subscribe(
      response => this.handleSuccessfulResponse(response),
      error => this.handleErrorResponse(error)
    );
  }

handleErrorResponse(error) {
    //console.log(error);
    //console.log(error.error);
    //console.log(error.error.message);
    this.welcomeMessageFromService = error.error.message
  }
}
```





### Form based authentication

- sends username and password in the header

