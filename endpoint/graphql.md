# GRAPHQL API Documentation

Our team has adopted GraphQL as our primary method for accessing data, as it provides a streamlined and intuitive approach to fetching and manipulating data from our server. With GraphQL, we are able to easily document our API and maintain consistent communication between our frontend and backend teams.

Endpoint: https://devumsapi.robinsonsland.com/rLcTrAxi0NpR0d

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

**Mutation** - is the equivalent of POST/PUT/DELETE

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


