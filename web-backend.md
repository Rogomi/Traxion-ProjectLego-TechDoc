[Back](README.md)

# Project LEGO Web Backend

## Technical Documentation

### GETTING STARTED

Project LEGO Web Backend was developed using the Node.JS JavaScript framework.

### INSTALLATION AND DEVELOPMENT

The user must first install the [Node.js](https://nodejs.org/en/) runtime environment for development, building, and deployment. Installation of this includes the [Node Package Manager (NPM)](https://www.npmjs.com/), which helps install external libraries needed for the app to function.

This project was created with **Node.js version 16.16.0**.

After that, the user must follow the guide for ExpressJS [here](https://expressjs.com/en/starter/installing.html).

Lastly, the user must have a text editor. The developers suggest [Visual Studio Code](https://code.visualstudio.com/) with the following extensions:

[Apollo GraphQL](https://marketplace.visualstudio.com/items?itemName=apollographql.vscode-apollo) - Rich editor support for GraphQL client and server development that seamlessly integrates with the Apollo platform  

### PROGRAMMING LANGUAGE

Project LEGO Web uses JavaScript for development.

### DEBUGGING

The developers use the corresponding developer tools for [Chrome](https://developer.chrome.com/docs/devtools/), [Firefox](https://firefox-dev.tools/), and [Safari](https://developer.apple.com/safari/tools/) respectively, together with the [Vue.js Devtools](https://devtools.vuejs.org/). 

As well as [Postman](https://www.postman.com/downloads/) for testing API calls.

### IMPORTANT CLASSES

#### Initialization Classes
- **server.js** - handles the initialization of server configuration
- **config.js** - processes the environment ports
- **app.js** - initiates the middleware, routes, error handler, and server configuration

#### Middlewares
- **tokenMiddleware.js** - validates the authentication token

#### Controllers
- **controller.js** - . 
    ##### Data/Methods
    - `` - .

#### Routes
- **routes.js** - compiles the routes

### ARCHITECTURE USED

![alt text](https://github.com/Rogomi/Traxion-ProjectLego-TechDoc/blob/develop/UMS-architecture.png)
