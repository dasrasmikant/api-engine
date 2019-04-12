# csm-ai Genarator 
A simple Library to generate templates for different type of projects such as API Framework, Chatbot Framework etc.

## Installation
    npm i csm-ai

# API Framework
<<<<<<< HEAD
## Structure
=======
Structure
------------
>>>>>>> dev
![Project Structure](https://raw.githubusercontent.com/dasrasmikant/assets/master/images/project-structure.jpg)
- Define your APIs in the api.json file
- Do the project configuration in project-config.js file. Define project Name, Mongo DB Connection details in this file 
    >  {
    'projName': 'API Project',    
    'mongoConnection':{
        'db':'projectdb',
        'url':'mongodb://localhost:27017'
        },
    'controllerClassDir':"../business-controllers"
    }
- The business controller directory is created to store all business controller classes.


API Configuration
------------------------
APIs will be created in the api.json file.

**Calling a remote API** 

    {
    "method": "get",
    "apiName": "/getUsers/:page",
    "isRemoteAPI": 1,
    "remoteApi": {
      "paramType": "q",
      "endPoint": "https://reqres.in/api/users/"
    },
    "auth": ""
    }
- method value can be get or post
- apiname is the name of remote API
- isRemoteAPI is true
- remoteAPI object hold the details on remote API
  - paramType is "q" which states that parameter will be sent as querystring. In this case the end point will be called as _"https://reqres.in/api/users/?page=[page]"_
  - if paramType is not defined or "" then the endpoint will be called as _"https://reqres.in/api/users/[page]"_
  - endpoint is used to define the endpoint url of remote API
- auth can contain the value as "" or basic

**Create Internal API**

    {
    "method": "post",
    "apiName": "/insertUser",
    "isRemoteAPI": 0,
    "businessClass": "user-controller",
    "auth": "basic"
     }
-   All configurations are like above  except businessClass
-   The businessClass property define the class where teh API logic needs to defined.  

**Authentication**

You can also add authentication to your web APIs. to add a basic authentication follow these below steps.
- Use auth as basic. It will allow to access the APIs with basic authentication.
   
      {
        "method": "get",
        "apiName": "/getEmployee/:job",
        "isRemoteAPI": 0,
        "businessClass": "get-user-controller",
        "auth": "basic"
      }
- The user ID and password is defined in the auth>secretKey.js
