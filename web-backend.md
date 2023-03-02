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
- **tokenValidation.js** - validates the authentication token
- **logAudit.js** - handles the uploading of log files
- **restriction.js** - handles the application permissions based on user role
- **filesHandles.js** - handles the uploading of image files

#### Controllers - Handles the connection to data related with user authentication and user authorization
- **articleController.js** - Handles the uploading and retrieveal of Privacy Policy, and Terms and Conditions articles

- **authController.js** - Handles the authentication for user login and registration
    ##### Data/Methods
    - `signup` - processes the registration for new users
    - `login` - processes the login for existing users

- **errorController.js** - Handles the errors for different deployment branches

- **migrateController.js** - Handles the migration of the previous database to MariaDB database

- **userController.js** - Handles both the password related functions and profile related informations
    ##### Data/Methods
    - `forgotPassword` - processes the sending of the password reset link to the email of the user
    - `resetLink` - handles the creation of the password reset link
    - `changePasswordEmail` -  handles the reset password on the external reset link
    - `changePasswordUser` - handles the reset password on in-app reset link
    - `getUserProfile` - processes the retrieval of user information
    - `updateProfile` - processes the edit and update of user profile
    - `activateUser` - handles the activation of newly created users

- **validationController.js** - Handles the validation related functions. 

#### Resolvers - Handles the data connection to GraphQL
- **index.js** - directory for the different resolvers

- **articleResolver.js** - Handles the connection to articles related data
    ##### Data/Methods
    - `createArticle` - handles the creation for the different articles accessible in the application
    - `articleByType` - handles the retrieval of the different articles

- **auditResolver.js** - Handles the connection to audits related data
    ##### Data/Methods
    - `createAudit` - processses the creation of new audits
    - `audits` - handles the retrieval of all the audits
    - `filterAudits` - handles the retrieval of audits filtered with a starting, and ending date
    - `filterAuditsByModule` - handles the retrieval of audits filtered with a starting, ending date, and selected module

- **buildingResolver.js** -  Handles the connection to buildings related data. 
    ##### Data/Methods
    - `buildings` - handles the retrieval of all the buildings
    - `buildingByProject` - handles the retrieval of all the buildings under a project
    - `buildingByProjectIds` - handles the retrieval of all the buildings under all selected projects

- **constructionResolver.js** -  Handles the connection to construction status related data. 
    ##### Data/Methods
    - `updateConstructionStatus` - processes the updating of the construction status of a unit
    - `addCompletionCertificate` - processes the creation and addition of a completion certificate to a construction status
    - `addAdditionalCertificate` - processes the addition of multiple completion certificates to a construction status
    - `deleteCompletionCertificate` - processes the removal of a completion certificate
    - `deleteFileWithinCompletionCertificate` - processes the removal of a file in a completion certificate
    - `getConstructionStatus` - handles the retrieval of construction status data

- **fieldResolver.js** - Handles the connection to field restrictions for departments related data. 
    ##### Data/Methods
    - `insertField` - processes creation of a restriction field.
    - `insertFieldRestriction` - processes the addition of a restriction field to a department
    - `insertFieldRestrictionException` - processes the exception for the restriction field to a department
    - `getFields` - handles the retrieval of all restriction fields.
    - `getAllFieldRestrictions` - handles the retrieval of all the restriction fields of all departments
    - `getFieldRestrictions` - handles the retrieval of all the restricion fields for a department

- **legalResolver.js** - Handles the connection to legal documents related data. 
    ##### Data/Methods
    - `updateEstatePropertyTax` - processes the updating of a estate property tax of a unit
    - `getLegalDetails` - handles the retrieval of all the legal details of a unit

- **moduleResolver.js** - Handles the connection to modules related data. 
    ##### Data/Methods
    - `createModule` - processes the creation of a new module
    - `createDepartment` - processes the creation of a new department or update on an existing department
    - `modules` - handles the retrieval of all modules
    - `departments` - handles the retrieval of all departments
    - `departmentById` - handles the retrieval of a department based on the provided departmentId

- **projectResolver.js** - Handles the connection to projects related data.
    ##### Data/Methods
    - `projects` - handles the retrieval of all projects
    - `setDefaultBookingLimit` - process the setting of default booking limit
    - `addEditBookingLimit` - process the adding and updating the booking limit of a project
    - `deleteBookingLimit` - process the deleting of booking limit of a certain project
    - `getBookingLimits` - handles the retrieval of list of projects with their corresponding limit
 

- **referenceStatusResolver.js** - Handles the connection to reference status related data. 
    ##### Data/Methods
    - `createReferenceStatus` - processes the creation of a new reference status
    - `referenceStatuses` - handles the retrieval of reference statuses based on the provided type
    - `allReferenceStatus` - handles the retrieval of all reference statuses

- **unitResolver.js** - Handles the connection to units related data.
    ##### Data/Methods
    - `createUnit` - processes the creation of a new unit
    - `createUnitType` - processes the creation of a new unit type
    - `insertUnitPlan` - processes the insertion of a unit plan to a unit
    - `uploadUnitPhotos` - processes the addition of photos to a unit
    - `uploadUnitPhotosV2` - processes the addition of photos to a unit using decompressed parameters
    - `deleteUnitPhoto` - processes the removal of a photo in a unit
    - `setDefaultPhoto` - processes the selection of a unit default photo
    - `unmarkDefaultPhoto` - processes the removal of a default unit photo
    - `uploadUnitPlan` - processes the creation and update of the unit plan for a unit
    - `deleteUnitPlan` - processes the removal of the unit plan of a unit
    - `updateEmiCategory` - processes the update of the emi category of a unit
    - `searchUnit` - handles the retrieval of all units based on the given parameters
    - `searchUnitV2` - handles the retrieval of all units based on the given and decompressed parameters
    - `advancedSearchV2` - handles the retrieval of all units based on the given parameters and more specific filters
    - `unitTypes` - handles the retrieval of all unit types
    - `units` - handles the retrieval of all units
    - `unitDetails` - handles the retrieval of all available information for a unit
    - `unitDetailsByUnitCode` - handles the retrieval of all available information for units based on the given unit code
    - `getAccount` - handles the retrieval of all available account details information for a unit
    - `getUnitPlan` - handles the retrieval of the unit plan for a unit
    - `getUnitPhotos` - handles the retrieval of the photos for a unit

- **userResolver.js** - Handles the connection to user related data.. 
    ##### Data/Methods
    - `createUser` - processes the creation of a new user
    - `activateUser` - processes the activation of a new user
    - `users` - handles the retrieval of all the users
    - `userById` - handles the retrieval of a user based on the given user id
    - `filterUser` - handles the retrieval of all the users using the given filter

- **scheduleResolver.js** - Handles the connection to scheduling related data.
    ##### Data/Methods
    -`emailSchedule` - process the email sending of schedule
    -`saveSchedule` - process the saving of viewing schedule
    -`updateBooking` - process the update schedule to sap server
    -`validateSchedule` - process the checking of booking limit
    -`getSchedule` - handles the retrieval of viewing schedule
    -`getSapSchedules` - handles the retrieval of booking schedule from SAP API
    
- **unitTurnoverResolver.js** - Handles the connection to scheduling related data.
    ##### Data/Methods
    -`updateUnitTurnover` - process the updating of unit turnover
    -`getUnitTurnover` - handles the retrieval of unit turnover



#### Routes
- **routes.js** - compiles the routes

### ARCHITECTURE USED

#### API ARCHITECTURE
![alt text](https://github.com/Rogomi/Traxion-ProjectLego-TechDoc/blob/develop/UMS-architecture-web.png)

#### OVERALL ARCHITECTURE
![alt text](https://github.com/Rogomi/Traxion-ProjectLego-TechDoc/blob/develop/UMS-architecture-overall.png)
