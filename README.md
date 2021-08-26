### Live Links
#### * [ Fontend - PiLeD up ](https://kulsumansari.github.io/Todo-Frontend-webpack/dist/index.html)
#### * [ Backend Server - Hosted on Heroku ](https://todo-backend-switch-mode.herokuapp.com/)


# ToDo List App - PiLeD uP (Frontend)
PiLeD uP is a todo list App which allows users to maintane their todo list , It makes API calls to server for storing and maintaining todo tasks.

## Introduction

PiLed uP todo app is built with HTML and vanillaJS , It allows to create, delete , update , and store todo list with the help of api calls to the server that is hosted on huroku.  


### Installation

1. Clone the repository by running following command in your terminal
   ```sh
   $ git clone https://github.com/kulsumansari/Todo-Frontend-webpack.git
   ```
2. Navigate to the root folder , Open the index.html with Live Server to get the application running

## Features

1. Create a task in todo list

2. Update a task

3. Mark as complete on the completion of task

4. Delete task from todo list


## Folder Structure
```
.
├── dist
│   └── assets
│       └── d460659a82d28551fc079943fa4c66da.png
│   └── style
│       └── style.css
│   └── bundle.js
│   └── index.html
|   └── todoImg.png
│
├── assests
│   └── todoImage.png
├── index.html
├── README.md
├── src
│   ├── actions
│   │   └── domOperations.js
│   ├── apiCalls
│   │   └── taskAPI.js
│   ├── app.js
│   └── components
│       └── task.js
└── style
    └── style.css
    
```

![]()



<br>
<br>


# Todo-API-Mongoose-ModeSwitch

#### Key Concepts : NodeJS, Express, MVC , Mongodb , Mongoose , dotnev

#### [Live Server URL ]( https://todo-backend-switch-mode.herokuapp.com/)

A simple Todo backend server application built using Node.js . It allows to make API calls to get all tasks, get task by Id,
create task, update task and delete task.

This backend server has two operation modes,

1. DATABASE
 
2. FILE SYETEM

If the **MODE** is set to **DATABASE** in config.env , The server's operation mode will be switched to DATABASE. In a Databse operation mode server uses mongodb database operations to manipulate Todos in the database (implemeted in taskControllerDB.js). 

If the mode is not set (in config.env file) the backend server switches to default mode which is file system mode. All read/write operations are performed on JSON file(in this case tasks.json) where all tasks are stored.  


#### Installation and Run

To Setup this project locally follow below mentioned steps:

 1. Installation
 
   - Clone the Repository
   
   ```
    git clone https://github.com/kulsumansari/Todo-API-Mongoose-ModeSwitch.git
  ```
  - navigate to the root folder and run the following commands to install node modules.
   
  ```
  npm install
  ```
  
  2. Configure Database 
   
      a.Install Mongodb database in your system 
   
      b.Create a database named Todos
   
   
  3. Run the Project
  
  ```
  node server.js
  ```
    
##### API Endpoint : http://127.0.0.1:YOUR_PORT


## API

### Get all tasks
   
 url: tasks/

 Method : `GET` 

 URL params : none

 request body : none

 * Response :

    Status Code: 200

    body :
      
      ```
      {
       "message": "successful",
       "data": [
          {
              "taskId": "2qqgt5iqkscxs44b",
              "content": "some new edited",
              "createdAt": "15 / 8 / 2021",
              "updatedAt": "15 / 8 / 2021",
              "isCompleted": false
          },
          {
              "taskId": "2qqgtkwyksd6a5wx",
              "content": "task 1",
              "createdAt": "15 / 8 / 2021",
              "updatedAt": "none",
              "isCompleted": false
          },
        ]
     }
     ```
### Get task by Id
 
   url : /tasks/:taskId
   
   Method : `GET` 
   
   url params : taskId
   
   body params : none
   
   * Successful Response
     
       status code : 200

       body :
     
     ```
     {
        "message": "successful tasks",
        "data": {
            "taskId": "2qqgt5iqkscxs44b",
            "content": "some new edited",
            "createdAt": "15 / 8 / 2021",
            "updatedAt": "15 / 8 / 2021",
            "isCompleted": false
        }
     }
     ```
      * Error Response:
         
          status code : 404

          body :
      
      ```
      {
         "error": "Task not found",
         "message": "Invalid Id"
      }
     
     ```
     
### Create new task

   url : /tasks
   
   Method : `POST` 
   
   url params : none
   
   body params : 
   
   request body should be in JSON format. An example of POST request body for creating task is given below:
   
  ```
  {
      "content" : " Go to gym",
      "createdAt" : "11/08/2021",
      "updatedAt" : "12/08/2021"
  } 

```

>> **Note :** "content" , "createdAt" , "updatedAt"  are only valid keys for creating task.

   Upon the creation of new task id will be dynamically assigned and isCompleted is set to false.
   
   * Successful Response:
      
        status code : 200
     
        body :
   
      ```
     {
       "message": "task Added",
       "data": {
           "taskId": "2qqgt4obkse3qjv8",
           "content": " Go to gym",
           "createdAt": "11/08/2021",
           "updatedAt": "none",
           "isCompleted": false
       }
     }
     ```
     
     
   * Error Response:
         
       status code : 400

       body :
      
      ```
      {
         "message": "Invalid Request: Keys are not compatible",
         "error": "Invalid Request"
      }
     
     ```
     
### Update task by Id
 
   url : /tasks/:taskId

   Method : `POST` 

   url params : taskId

   body params : 

   request body should be in JSON format. An example of POST request body for creating task is given below:


      ```
      {
         "content" : " Go to gym",
         "createdAt" : "11/08/2021",
         "updatedAt" : "12/08/2021",
         "isCompleted" : true,
      }
    ```
>> **Note :** "content" , "createdAt" , "updatedAt" , "isCompleted"  are only valid keys for updating task.

 * Successful Response:
      
    * status code : 200

      body :
   
      ```
       {
         "message": "task Added",
         "data": {
             "taskId": "2qqgt4obkse3qjv8",
             "content": " Go to gym",
             "createdAt": "11/08/2021",
             "updatedAt": "none",
             "isCompleted": false
         }
       }
       ```
     
     
   * Error Response:(Invalid Keys)
         
       status code : 400 

       body :

      ```
      {
         "message": "Invalid Request: Keys are not compatible",
         "error": "Invalid Request"
      }
     
     ```
     
    * Error Response: (task not found)

       status code : 404

       body :

     ```
     {
        "error": "Task not found",
        "message": "Invalid Id"
     }

    ```

### Delete a task by Id

   url : /tasks/:taskId

   Method : `DELETE`

   url params : taskId

   
   * Successful Response
     
        status code : 204 (No Content)
        
   
   * Error Response: (task not found)

       status code : 404

       body :

     ```
     {
        "error": "Task not found",
        "message": "Invalid Id"
     }
      ```
      
      ## Run in postman

You can test this API on Postman :

[![Run in Postman](https://run.pstmn.io/button.svg)](https://app.getpostman.com/run-collection/88c60e2df7d8e2ab003d?action=collection%2Fimport)

## Project Folder Structure
```bash

├── app.js
├── server.js
├── package.json
├── package-lock.json
├── README.md
├── config.env
├── controllers
│   └── taskControllerDB.js
│   └── taskControllerFS.js
├── data
│   └── tasks.json
├── models
│   └── taskModelFS.js
│   └── taskModelMongoose.js
├── routes
    └── taskRouter.js
└── utils
    └── switch.js
    
```


## Resources
* [ Express ](https://developer.mozilla.org/en-US/docs/Learn/Server-side/Express_Nodejs/Introduction)
* [ Fetch() ](https://developer.mozilla.org/en-US/docs/Web/API/Fetch_API/Using_Fetch)
* [ Webpack ](https://webpack.js.org/)
* [ Mongoose ](https://mongoosejs.com/docs/guide.html)
* [ async await ](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/async_function)
