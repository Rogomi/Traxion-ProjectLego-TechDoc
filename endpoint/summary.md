# Project Lego API Documentation

Our team utilizes both REST API authentication and GraphQL, with REST being our primary method for authenticating user requests and GraphQL serving as our primary query language for accessing and manipulating data from our server. This allows us to leverage the strengths of both technologies in order to provide a secure and efficient experience for our users.

REST API

Staging Base URL: https://devumsapi.robinsonsland.com/
Production Base URL: https://umsapi.robinsonsland.com/

Basic Auth Credentials:

- Username: `username`
- Password: `password`

Content: 

* User Login
* Forgot Password
* Change Password from Reset Link 
* Change Password in User Profile 
* Viewing Schedule
* List of Punchlists
* Post Buyer Remarks

* GraphQL API

<hr />

# User Login

For user authentication

**URL** : `/api/v1/auth/login`

**Method** : `POST`

**Auth required** : Basic

**JSON Body Parameters** : 

```json
{
	"email": "testmail@mail.com",
	"password" : "S3cr!tPass"
}
```

## Success Response

**Code** : `200 OK`

**Content example**

```json
{
	"token": "Bearer token to be used for authorization header",
	"userId": "bb166ce3-899d-47f9-a622-f51019b60b4b"
}
```

<hr />

# Forgot Password

**URL** : `/api/v1/auth/forgotPassword`

**Method** : `POST`

**Auth required** : Basic

**JSON Body Parameters** : 

```json
{
	"email": "testmail@mail.com"
}
```

## Success Response

**Code** : `200 OK`

**Content example**

```json
{
	"link": "redirection link"
}
```

<hr />

# Change Password from Reset Link

**URL** : `/api/v1/auth/changePasswordEmail`

**Method** : `POST`

**Auth required** : Basic

**JSON Body Parameters** : 

```json
{
  "userId": "user id from link",
  "token": "token from link",
  "password": "new password",
}
```

## Success Response

**Code** : `200 OK`

**Content example**

```json
{
	message: "Password Changed Successfully"
}
```
<hr />

# Change Password on User Profile

**URL** : `/api/v1/auth/changePasswordUser`

**Method** : `POST`

**Auth required** : Basic

**Header** :

- Authorization: `Bearer Token`

**JSON Body Parameters** : 

```json
{
  "oldPassword": "old password",
  "password": "new password",
}
```

## Success Response

**Code** : `200 OK`

**Content example**

```json
{
	message: "Password Changed Successfully"
}
```

<hr />

# Get Viewing Schedules

Show a viewing schedule based on submitted time range.

**URL** : `/api/v1/schedule/viewSchedule`

**Query Parameters** : 

- `unitNo=[string]` CONDO13
- `projectCode=[string]` 00048100
- `buildingCode=[string]` TEST123

**Method** : `GET`

**Auth required** : Basic


## Success Response

**Code** : `200 OK`

**Content example**

```json
[
	{
		"id": "cda1e6dd-8567-43da-8152-3931b3f374eb",
		"propertyAddress": "QC",
		"viewingDate": "2023-03-15T16:00:00.000Z",
		"timeFrom": "08:00:00",
		"timeTo": "09:00:00",
		"buyerName": "JAMES REID FORD WHITE REID ORANGE BLUE",
		"turnoverEngineer": {
			"firstName": "Media",
			"lastName": "Gulapa",
			"position": "Turnover Engineer"
		},
		"unit": {
			"unitNo": "CONDO13",
			"contractNo": "0000100001771"
		},
		"project": {
			"name": "Sample BE 123",
			"projectCode": "00048100"
		},
		"building": {
			"name": "The Residences TEST A",
			"bldgCode": "TEST123"
		}
  ....
 ]
```

## Error Responses

**Condition** : If wrong Basic Auth Credentials

**Code** : `401 UNAUTHORIZED`

**Content** : `{}`

<hr />

# Get Buyer Punchlists

Show the list of buyer punchlists.

**URL** : `/api/v1/punchlist/list`

**Query Parameters** : 

- `unitNo=[string]` CONDO13
- `projectCode=[string]` 00048100
- `buildingCode=[string]` TEST123

**Method** : `GET`

**Auth required** : Basic


## Success Response

**Code** : `200 OK`

**Content example**

```json
[
	{
		"id": "e064f6bd-165d-4cf6-bc74-cb1d333e1b42",
		"refNo": "BPLTEST1230009",
		"dateAccepted": "2023-04-16T16:00:00.000Z",
		"buyerName": "Mediatrix Gulapa",
		"status": "Accepted",
		"turnaroundTime": "15 days",
		"targetCompletionDate": "2023-04-15T16:00:00.000Z",
		"filedBy": {
			"firstName": "Media",
			"lastName": "Gulapa",
			"position": "Turnover Engineer"
		},
		"unit": {
			"unitNo": "CONDO13",
			"contractNo": "0000100001771"
		},
		"project": {
			"name": "Sample BE 123",
			"projectCode": "00048100"
		},
		"building": {
			"name": "The Residences TEST A",
			"bldgCode": "TEST123"
		},
		"punchlistitems": [
			{
				"sectionName": null,
				"item": "Floor tiles",
				"particular": "okay",
				"status": "Accepted"
			}
		]
	}
  ....
 ]
```

## Error Responses

**Condition** : If wrong Basic Auth Credentials

**Code** : `401 UNAUTHORIZED`

**Content** : `{}`

<hr />

# Post Buyer Remarks

Post a buyer remarks for viewing schedule.

**URL** : `/api/v1/schedule/viewSchedule`

**Method** : `POST`

**Auth required** : Basic

**JSON Body Parameters** : 

```json
{
	"unitNo": "CONDO13",
	"projectCode" : "00048100",
	"buildingCode": "TEST123",
	"buyerRemarks" : "This is a remark"
}
```

## Success Response

**Code** : `200 OK`

**Content example**

```json
{
	"id": "e5a8836c-8a16-4bbc-a99f-f76f48af6f80",
	"message": "Buyer's Remarks Successfully Posted."
}
```

## Error Responses

**Condition** : If wrong Basic Auth Credentials

**Code** : `401 UNAUTHORIZED`

**Content** : `{}`

<hr />

# GRAPHQL API Documentation

Our team has adopted GraphQL as our primary method for accessing data, as it provides a streamlined and intuitive approach to fetching and manipulating data from our server. With GraphQL, we are able to easily document our API and maintain consistent communication between our frontend and backend teams.

Staging Endpoint: https://devumsapi.robinsonsland.com/rLcTrAxi0NpR0d
Production Endpoint: https://umsapi.robinsonsland.com/rLcTrAxi0NpR0d

Header Credentials:

- Authentication: `Bearer Token`
- api-key: `APIKEY`

Access the endpoint to test the API. You can use GraphQL Altair, a GraphQL API tool. https://altairgraphql.dev/ Also, GraphQL API Tool provides a more user-friendly and detailed documentation. 

## Projects / Buildings

**Query** - is the equivalent of GET

```graphql

    # Use to get the list of all projects
    projects: [Project]
    
    # Use to get the list of all buildings
    buildings: [Building]

    # Use to get the list of all buildings by projects
    #
    # Arguments
    # projectIds:
    buildingsByProjectIds(projectIds: [String]): [Building] 
    
    # Use to get the list of projects of a specific user
    #
    # Arguments
    # userId:
    getUserProjects(userId: String): [Project] 
    
    # Use to get a advanced project lists. It returns more details or fields --
    # primarily used in project module
    getAdvancedProjectLists: [Project]
    
    # Use to get the project photos
    #
    # Arguments
    # projectId:
    # isPreselling:
    getProjectPhotos(projectId: String, isPreselling: Boolean): [ProjectPhoto]
    
    # Use to get a number of units per project
    #
    # Arguments
    # projectId:
    getProjectUnitCount(projectId: String): Int 
    
	# Use to get the list of project plans per project
	#
	# Arguments
	# projectId:
	# planType:
	getProjectPlans(projectId: String, planType: ProjectPlanType): [ProjectPlan]
	# Use to get the project milestone
	#
	# Arguments
	# projectId:
	getProjectMilestone(projectId: String): ProjectMilestone
	# Use to get the construction progress of a building
	#
	# Arguments
	# buildingId:
	getConstructionProgress(buildingId: String): ConstructionProgress 
    

```

**Mutation** - is the equivalent of POST/PUT/DELETE

```graphql
    
    # Use to upload project photos
    #
    # Arguments
    # photos:
    # projectId:
    # defaultPhotoIndex:
    # isPreselling:
    uploadProjectPhotos(
    photos: [Upload],
    projectId: String,
    defaultPhotoIndex: Int,
    isPreselling: Boolean
    ): GeneralMessage
    
    # Use to delete a project photo
    #
    # Arguments
    # photoId:
    deleteProjectPhoto(photoId: String): GeneralMessage
    
    # Use to set a default project photo
    #
    # Arguments
    # photoId:
    # projectId:
    # isPreselling:
    setProjectDefaultPhoto(
    photoId: String,
    projectId: String,
    isPreselling: Boolean
    ): GeneralMessage
    
    # Use to set a default project photo
    #
    # Arguments
    # photoId:
    # projectId:
    # isPreselling:
    unmarkProjectDefaultPhoto(
    photoId: String,
    projectId: String,
    isPreselling: Boolean
    ): GeneralMessage
    
    # Use to update admin contact
    #
    # Arguments
    # projectId:
    # adminContactNo:
    updateProjectAdminContact(
    projectId: String,
    adminContactNo: String
    ): GeneralMessage 
	
	# Use to upload project plan
	#
	# Arguments
	# projectId:
	# file:
	# planType:
	# description:
	uploadProjectPlan(
	projectId: String,
	file: Upload,
	planType: ProjectPlanType,
	description: String
	): GeneralMessage
	
	# Use to delete project plan
	#
	# Arguments
	# projectPlanId:
	deleteProjectPlan(projectPlanId: String): GeneralMessage
	
	# Use to update project plan description
	#
	# Arguments
	# projectPlanId:
	# description:
	updateDescription(projectPlanId: String, description: String): GeneralMessage
	
	# Use to save construction progress
	#
	# Arguments
	# buildingId:
	# completionPercentage:
	# projectedCompletionDate:
	# actualCompletionDate:
	saveConstructionProgress(
	buildingId: String,
	completionPercentage: Int,
	projectedCompletionDate: String,
	actualCompletionDate: String
	): GeneralMessage
	
	# Use to save project milestone
	#
	# Arguments
	# projectId:
	# completionDate:
	# revisedTargetDate:
	# groundBreakingEventDate:
	# groundBreakingActualDate:
	# toppingOffEventDate:
	# toppingOffActualDate:
	saveProjectMilestone(
	projectId: String,
	completionDate: String,
	revisedTargetDate: String,
	groundBreakingEventDate: String,
	groundBreakingActualDate: String,
	toppingOffEventDate: String,
	toppingOffActualDate: String
	): GeneralMessage 

```

## Users

**Query** 

```graphql
    # Use to get the list of departments
    departments: [Department] 
    -
    
    # Use to get the details of specific department
    #
    # Arguments
    # id:
    departmentById(id: String): Department 
    -
    
    # Use to get the list of all users
    users: [User] 
    -
    
    # Use to get the details of a specific user
    #
    # Arguments
    # id:
    userById(id: String): User 
    -
    
    # Use to search or filter user
    #
    # Arguments
    # userEmail:
    # department:
    filterUser(userEmail: String, department: [String]): [User] 
    -
    
```

**Mutation**

```graphql

    # Create/Update a department. Pass an empty or null id update if create. For
    # update, pass the id of department.
    #
    # Arguments
    # id:
    # name:
    # abbreviation:
    # modules:
    createDepartment(
    id: String,
    name: String,
    abbreviation: String,
    modules: [DepartmentModuleInput]
    ): Department 
    
    -
    
    # Use to create or update a user in admin portal. Pass an id in userInput for update.
    #
    # Arguments
    # userInput:
    createUser(userInput: UserInput): UserResponse 
    
    -
    
    # Use to activate or deactivate a user
    #
    # Arguments
    # userId:
    activateUser(userId: String): ActivationResponse 
    
    -
    
    # Use to update the password of a user.
    #
    # Arguments
    # passwordInput:
    changePassword(passwordInput: PasswordInput): String 

```

## Units

**Query** 

```graphql

    # Use to seach a unit by projects, buildings, and keyword only
    #
    # Arguments
    # projectIds:
    # buildingIds:
    # keyword:
    searchUnitV2(
    projectIds: [String],
    buildingIds: [String],
    keyword: String
    ): [Unit] 
    
    # Use to make an advanced unit search
    #
    # Arguments
    # advancedSearchInput:
    advancedSearchV2(advancedSearchInput: AdvancedSearchInput): [Unit]
    
    # Use to get the legal details of a unit
    #
    # Arguments
    # unitId:
    # bldgId:
    getLegalDetails(unitId: String, bldgId: String): Legal
    
    # Use to get the construction status of a unit
    #
    # Arguments
    # unitId:
    getConstructionStatus(unitId: String): Construction
    
    # Use to get the unit turnover details of a unit
    #
    # Arguments
    # unitId:
    getUnitTurnover(unitId: String): UnitTurnover
    
    # Use to get the list of unit notes
    #
    # Arguments
    # unitId:
    unitNotes(unitId: String): [UnitNote]
    
    # Use to get the list of attachments of a unit note
    #
    # Arguments
    # noteId:
    unitNoteAttachments(noteId: String): [UnitNoteAttachment]  
    
    # Use to get the viewing schedule details
    #
    # Arguments
    # unitId:
    getSchedule(unitId: String): ViewingSchedule
    
    # Use to get the viewing schedule details
    #
    # Arguments
    # unitId:
    getSapSchedules(unitId: String): [SapSchedule] 

```

**Mutation**

```graphql
    
    # Use to update emiCategory.
    #
    # Arguments
    # emiCategory:
    # unitId:
    updateEmiCategory(emiCategory: String, unitId: String): GeneralMessage
    
    # Use to create a unit note
    #
    # Arguments
    # content:
    # unitCode:
    # unitId:
    # attachments:
    createUnitNote(
    content: String,
    unitCode: String,
    unitId: String,
    attachments: [Upload]
    ): UnitNote
    
    # Use to update a unit note
    #
    # Arguments
    # noteId:
    # content:
    updateUnitNote(noteId: String, content: String): GeneralMessage
    
    # Use to upload a unit note attachments
    #
    # Arguments
    # attachments:
    # noteId:
    uploadUnitNoteAttachments(
    attachments: [Upload],
    noteId: String
    ): GeneralMessage
    
    # Use to delete a unit note
    #
    # Arguments
    # noteId:
    deleteUnitNote(noteId: String): GeneralMessage
    
    # Use to delete a unit note attachment
    #
    # Arguments
    # attachmentId:
    deleteUnitNoteAttachment(attachmentId: String): GeneralMessage 
    
    # Use to upload unit photos
    #
    # Arguments
    # photos:
    # unitId:
    # defaultPhotoIndex:
    # bldgCode:
    uploadUnitPhotosV2(
    photos: [Upload],
    unitId: String,
    defaultPhotoIndex: Int,
    bldgCode: String
    ): GeneralMessage
    
    # Use to delete a unit photo
    #
    # Arguments
    # photoId:
    deleteUnitPhoto(photoId: String): GeneralMessage
    
    # Use to set a default unit photo
    #
    # Arguments
    # photoId:
    # unitId:
    # bldgId:
    setDefaultPhoto(photoId: String, unitId: String, bldgId: String): GeneralMessage
    
    # Use to set a default unit photo
    #
    # Arguments
    # photoId:
    # unitId:
    unmarkDefaultPhoto(photoId: String, unitId: String): GeneralMessage
    
    # Use to upload a unit plan or revised unit plan.
    #
    # Arguments
    # file:
    # unitId:
    # isRevised:
    # bldgId:
    uploadUnitPlan(
    file: Upload,
    unitId: String!,
    isRevised: Boolean!,
    bldgId: String
    ): GeneralMessage
    
    # Use to delete a unit plan or revised unit plan.
    #
    # Arguments
    # unitId:
    # isRevised:
    deleteUnitPlan(unitId: String!, isRevised: Boolean!): GeneralMessage
    
    # Use to update estate property tax under legal submodule
    #
    # Arguments
    # unitId:
    # yearCovered:
    # bldgId:
    updateEstatePropertyTax(
    unitId: String,
    yearCovered: [String],
    bldgId: String
    ): GeneralMessage
    
    # Use to update construction status
    #
    # Arguments
    # unitId:
    # constructionStatus:
    # bldgId:
    updateConstructionStatus(
    unitId: String,
    constructionStatus: String,
    bldgId: String
    ): GeneralMessage
    
    # Use to add completion certificate
    #
    # Arguments
    # files:
    # unitId:
    # category:
    # status:
    # bldgId:
    addCompletionCertificate(
    files: [Upload],
    unitId: String,
    category: String,
    status: String,
    bldgId: String
    ): GeneralMessage
    
    # Use to update completion certificate
    #
    # Arguments
    # certificateId:
    # file:
    # constructionId:
    # category:
    # status:
    editCompletionCertificate(
    certificateId: String,
    file: Upload,
    constructionId: String,
    category: String,
    status: String
    ): GeneralMessage
    
    # Use to delete completion certificate
    #
    # Arguments
    # certificateId:
    deleteCompletionCertificate(certificateId: String): GeneralMessage
    
    # Use to add additional certificate within Completion Certificate
    #
    # Arguments
    # certificateId:
    # files:
    # unitId:
    # category:
    # status:
    addAdditionalCertificate(
    certificateId: String,
    files: [Upload],
    unitId: String,
    category: String,
    status: String
    ): GeneralMessage
    
    # Use to delete certificate within Completion Certificate
    #
    # Arguments
    # certificateId:
    # fileUploadId:
    deleteFileWithinCompletionCertificate(
    certificateId: String,
    fileUploadId: String
    ): GeneralMessage
    
    # Use to update unit turnover
    #
    # Arguments
    # viewingStatus:
    # keyStatus:
    # atmiStatus:
    # unitId:
    # bldgId:
    updateUnitTurnover(
    viewingStatus: String,
    keyStatus: String,
    atmiStatus: String,
    unitId: String,
    bldgId: String
    ): GeneralMessage 
    
    # Use to send viewing schedule email
    #
    # Arguments
    # scheduleId:
    emailSchedule(scheduleId: String): GeneralMessage
    
    # Use to save viewing schedule
    #
    # Arguments
    # unitId:
    # buildingId:
    # projectId:
    # propertyAddress:
    # inviteStatus:
    # viewingDate:
    # timeFrom:
    # timeTo:
    # bccEmail:
    # engineerUserId:
    saveSchedule(
    unitId: String,
    buildingId: String,
    projectId: String,
    propertyAddress: String,
    inviteStatus: String,
    viewingDate: String,
    timeFrom: String,
    timeTo: String,
    bccEmail: String,
    engineerUserId: String
    ): ViewingSchedule
    
    # Use to update booking of in sap schedule
    #
    # Arguments
    # unitId:
    # scheduleId:
    # date:
    # timeFrom:
    # timeTo:
    # viewingResult:
    # remarks:
    updateBooking(
    unitId: String,
    scheduleId: String,
    date: String,
    timeFrom: String,
    timeTo: String,
    viewingResult: String,
    remarks: String
    ): GeneralMessage
    
    # Use to validate schedule based on date
    #
    # Arguments
    # projectId:
    # date:
    validateSchedule(projectId: String, date: String): GeneralMessage
    
```

## Punchlists

**Query**

```graphql
    
    # Use to get the list of punchlists
    getPunchlists: [Punchlist]
    
    # Use to get the details of punchlist
    #
    # Arguments
    # id:
    getPunchlistDetails(id: String): Punchlist
    
    # Use to get the punchlist items
    #
    # Arguments
    # punchlistId:
    getPunchlistItems(punchlistId: String): [PunchlistItem]
    
    # Use to get the predefined punchlist items for TOQ
    getPredefinedPunchlistItems: [PunchlistItem]
    
    # Use to get the unit turnover schedules
    #
    # Arguments
    # month:
    # year:
    # projectId:
    getUnitTurnoverSchedules(
    month: String,
    year: String,
    projectId: String
    ): [ViewingSchedule]
    
    # Use to filter the viewing schedule per day
    #
    # Arguments
    # date:
    # projectId:
    getUnitTurnoverSchedulesPerDay(
    date: String,
    projectId: String
    ): [ViewingSchedule]
    
    # Use to filter turnover schedules by date range and or project
    #
    # Arguments
    # dateFrom:
    # dateTo:
    # projectId:
    filterTurnoverSchedules(
    dateFrom: String,
    dateTo: String,
    projectId: String
    ): String
    
    # Use to get the latest toq puchlist of a unit
    #
    # Arguments
    # unitId:
    getLatestToqPunchlist(unitId: String): Punchlist
    
    # Use to get the latest buyer punchlist of a unt
    #
    # Arguments
    # unitId:
    getLatestBuyerPunchlist(unitId: String): Punchlist
    
    # Use to get the list of punchlists of a certain unit
    #
    # Arguments
    # unitId:
    getUnitPunchlists(unitId: String): [Punchlist]
    
    # Use to download the pdf file of punchlists report
    #
    # Arguments
    # dateFrom:
    # dateTo:
    downloadPunchlist(dateFrom: String, dateTo: String): String
    
    # Use to download the pdf file of punchlist details
    #
    # Arguments
    # punchlistId:
    downloadPunchlistById(punchlistId: String): String 

    
```
**Mutation**

```graphql
    
    # Use to save or update punchlist. Pass an empty or null id when adding a
    # punchlist.
    #
    # Arguments
    # id:
    # projectId:
    # buildingId:
    # unitId:
    # status:
    # type:
    # dateAccepted:
    # dateInspected:
    # buyerName:
    # targetCompletionDate:
    # turnaroundTime:
    # punchlistItems:
    savePunchlist(
    id: String,
    projectId: String,
    buildingId: String,
    unitId: String,
    status: String,
    type: String,
    dateAccepted: String,
    dateInspected: String,
    buyerName: String,
    targetCompletionDate: String,
    turnaroundTime: String,
    punchlistItems: [PunchlistItemInput]
    ): GeneralMessage
    
    # Use to process a punchlist
    #
    # Arguments
    # punchlistId:
    # status:
    # punchlistItems:
    processPunchlist(
    punchlistId: String,
    status: String,
    punchlistItems: [PunchlistItemInput]
    ): GeneralMessage
    
    # Use to cancel a punchlist
    #
    # Arguments
    # punchlistId:
    cancelPunchlist(punchlistId: String): GeneralMessage 

```

## Settings

**Query**

```graphql
    
    # Use to show the list of logs by module
    #
    # Arguments
    # module:
    # fromDate:
    # toDate:
    filterAuditsByModule(
    module: ModuleName,
    fromDate: String,
    toDate: String
    ): [Audit] 
    
    # Use to get the value of a simple content based on type like Terms and Conditions
    #
    # Arguments
    # type:
    articleByType(type: ArticleType): Article 
    
    # Use to get the restricted fields of a certain user
    getFieldRestrictions: [FieldRestriction] 
    
    # Use to get the list booking limits
    getBookingLimits: BookingLimits 
    
   
```

**Mutation**

```graphql
    
    # Use to set default booking limit
    #
    # Arguments
    # limit:
    setDefaultBookingLimit(limit: Int): GeneralMessage
    
    # Use to add or update booking limit of a project
    #
    # Arguments
    # projectId:
    # limit:
    addEditBookingLimit(projectId: String, limit: Int): GeneralMessage
    
    # Use to delete booking limit of a project
    #
    # Arguments
    # bookingLimitId:
    deleteBookingLimit(bookingLimitId: String): GeneralMessage 
    
    # Use to create a simple content, that needs only one field such as terms and
    # conditions, privacy policy, etc
    #
    # Arguments
    # id:
    # content:
    # type:
    createArticle(id: String, content: String, type: ArticleType): Article 

```



