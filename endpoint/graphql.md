# GRAPHQL API Documentation

Our team has adopted GraphQL as our primary method for accessing data, as it provides a streamlined and intuitive approach to fetching and manipulating data from our server. With GraphQL, we are able to easily document our API and maintain consistent communication between our frontend and backend teams.

Endpoint: https://devumsapi.robinsonsland.com/rLcTrAxi0NpR0d

Header Credentials:

- Authentication: `Bearer Token`
- api-key: `APIKEY`

Access the endpoint to test the API. You can use GraphQL Altair, a GraphQL API tool. https://altairgraphql.dev/



**Query**

    modules: [Module]
    
    departments: [Department]
    
    # Arguments
    # id:
    departmentById(id: String): Department
    
    users: [User]
    # Arguments
    # id:
    userById(id: String): User
    
    # Arguments
    # userEmail:
    # department:
    filterUser(userEmail: String, department: [String]): [User]
    
    audits: [Audit]
    
    # Arguments
    # fromDate:
    # toDate:
    filterAudits(fromDate: String, toDate: String): [Audit]
    
    # Arguments
    # module:
    # fromDate:
    # toDate:
    filterAuditsByModule(
    module: ModuleName,
    fromDate: String,
    toDate: String
    ): [Audit]
    
    projects: [Project]
    
    buildings: [Building]
    
    # Arguments
    # projectId:
    buildingsByProject(projectId: String): [Building]
    
    # Arguments
    # projectIds:
    buildingsByProjectIds(projectIds: [String]): [Building]
    
    # Arguments
    # type:
    referenceStatuses(type: ReferenceType): [ReferenceStatus]
    
    # Arguments
    # projectIds:
    # buildingIds:
    # keyword:
    searchUnit(projectIds: [String], buildingIds: [String], keyword: String): [Unit]
    
    # Arguments
    # advancedSearchInput:
    advancedSearch(advancedSearchInput: AdvancedSearchInput): [Unit]
    
    # Arguments
    # id:
    unitDetails(id: String): Unit
    
    # Arguments
    # unitCode:
    unitDetailsByUnitCode(unitCode: String): Unit
    
    unitTypes: [UnitType]
    
    # Arguments
    # type:
    articleByType(type: ArticleType): Article
    
    getFields: [Field]
    
    getFieldRestrictions: [FieldRestriction]
    
    getAllFieldRestrictions: [FieldRestriction]
    
    # Arguments
    # unitId:
    getAccount(unitId: String): Account
    
    # Arguments
    # unitId:
    getUnitPlan(unitId: String): UnitPlan
    
    # Arguments
    # unitId:
    # bldgId:
    getUnitPhotos(unitId: String, bldgId: String): [UnitPhoto]
    
    # Arguments
    # projectIds:
    # buildingIds:
    # keyword:
    searchUnitV2(
    projectIds: [String],
    buildingIds: [String],
    keyword: String
    ): [Unit]
    
    # Arguments
    # advancedSearchInput:
    advancedSearchV2(advancedSearchInput: AdvancedSearchInput): [Unit]
    
    # Arguments
    # unitId:
    # bldgId:
    getLegalDetails(unitId: String, bldgId: String): Legal
    
    # Arguments
    # unitId:
    getConstructionStatus(unitId: String): Construction
    
    # Arguments
    # unitId:
    getUnitTurnover(unitId: String): UnitTurnover
    
    # Arguments
    # unitId:
    unitNotes(unitId: String): [UnitNote]
    
    # Arguments
    # noteId:
    unitNoteAttachments(noteId: String): [UnitNoteAttachment]
    
    getBookingLimits: BookingLimits
    # Arguments
    # userId:
    getUserProjects(userId: String): [Project]
    
    # Arguments
    # unitId:
    getSchedule(unitId: String): ViewingSchedule
    
    # Arguments
    # unitId:
    getSapSchedules(unitId: String): [SapSchedule]
    
    # Arguments
    # userType:
    getUserByType(userType: UserType): [User]
    
    getPunchlists: [Punchlist]
    
    # Arguments
    # id:
    getPunchlistDetails(id: String): Punchlist
    
    # Arguments
    # punchlistId:
    getPunchlistItems(punchlistId: String): [PunchlistItem]
    
    getPredefinedPunchlistItems: [PunchlistItem]
    
    # Arguments
    # month:
    # year:
    # projectId:
    getUnitTurnoverSchedules(
    month: String,
    year: String,
    projectId: String
    ): [ViewingSchedule]
    
    # Arguments
    # date:
    # projectId:
    getUnitTurnoverSchedulesPerDay(
    date: String,
    projectId: String
    ): [ViewingSchedule]
    
    # Arguments
    # dateFrom:
    # dateTo:
    # projectId:
    filterTurnoverSchedules(
    dateFrom: String,
    dateTo: String,
    projectId: String
    ): String
    
    # Arguments
    # unitId:
    getLatestToqPunchlist(unitId: String): Punchlist
    
    # Arguments
    # unitId:
    getLatestBuyerPunchlist(unitId: String): Punchlist
    
    # Arguments
    # unitId:
    getUnitPunchlists(unitId: String): [Punchlist]
    
    # Arguments
    # dateFrom:
    # dateTo:
    downloadPunchlist(dateFrom: String, dateTo: String): String
    
    # Arguments
    # punchlistId:
    downloadPunchlistById(punchlistId: String): String

**Mutation**

   
    # Arguments
    # name:
    # parentModule:
    createModule(name: String, parentModule: String): Module
    
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
    
    # Arguments
    # name:
    createProject(name: String): Project
    
    # Arguments
    # userInput:
    createUser(userInput: UserInput): UserResponse
    
    # Arguments
    # userId:
    activateUser(userId: String): ActivationResponse
    
    # Arguments
    # passwordInput:
    changePassword(passwordInput: PasswordInput): String
    
    # Arguments
    # userId:
    # moduleName:
    # activity:
    createAudit(userId: String, moduleName: ModuleName, activity: String): Audit
    
    # Arguments
    # name:
    # projectId:
    createBuilding(name: String, projectId: String): Building
    
    # Arguments
    # name:
    # type:
    createReferenceStatus(name: String, type: ReferenceType): ReferenceStatus
    
    # Arguments
    # name:
    # unitCode:
    # unitType:
    createUnit(name: String, unitCode: String, unitType: String): Unit
    
    # Arguments
    # name:
    createUnitType(name: String): UnitType
    
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
    
    # Arguments
    # noteId:
    # content:
    updateUnitNote(noteId: String, content: String): GeneralMessage
    
    # Arguments
    # attachments:
    # noteId:
    uploadUnitNoteAttachments(
    attachments: [Upload],
    noteId: String
    ): GeneralMessage
    
    # Arguments
    # noteId:
    deleteUnitNote(noteId: String): GeneralMessage
    
    # Arguments
    # attachmentId:
    deleteUnitNoteAttachment(attachmentId: String): GeneralMessage
    
    # Arguments
    # id:
    # content:
    # type:
    createArticle(id: String, content: String, type: ArticleType): Article
    
    # Arguments
    # fieldName:
    # refCode:
    insertField(fieldName: String, refCode: String): Field
    
    # Arguments
    # fieldId:
    # departments:
    # state:
    insertFieldRestriction(
    fieldId: String,
    departments: [String],
    state: State
    ): [FieldRestriction]
    
    # Arguments
    # fieldId:
    # departments:
    # state:
    insertFieldRestrictionException(
    fieldId: String,
    departments: [String],
    state: State
    ): [FieldRestriction]
    
    # Arguments
    # accountInput:
    insertAccount(accountInput: AccountInput): Account
    
    # Arguments
    # url:
    # fileName:
    # fileType:
    # uploadedBy:
    insertFileUpload(
    url: String,
    fileName: String,
    fileType: String,
    uploadedBy: String
    ): FileUpload
    
    # Arguments
    # unit:
    # unitPlan:
    # revisedUnitPlan:
    insertUnitPlan(
    unit: String,
    unitPlan: String,
    revisedUnitPlan: String
    ): UnitPlan
    
    # Arguments
    # unitUpdateInput:
    updateUnit(unitUpdateInput: UnitUpdateInput): Unit
    
    # Arguments
    # file:
    fileUploadTest(file: Upload): String
    
    # Arguments
    # msg:
    # sender:
    # email:
    testMessage(msg: String, sender: String, email: String): String
    
    # Arguments
    # photoInputs:
    # unitId:
    uploadUnitPhotos(photoInputs: [UnitPhotoInput], unitId: String): GeneralMessage
    
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
    
    # Arguments
    # photoId:
    deleteUnitPhoto(photoId: String): GeneralMessage
    
    # Arguments
    # photoId:
    # unitId:
    # bldgId:
    setDefaultPhoto(photoId: String, unitId: String, bldgId: String): GeneralMessage
    
    # Arguments
    # photoId:
    # unitId:
    unmarkDefaultPhoto(photoId: String, unitId: String): GeneralMessage
    
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
    
    # Arguments
    # unitId:
    # isRevised:
    deleteUnitPlan(unitId: String!, isRevised: Boolean!): GeneralMessage
    
    # Arguments
    # emiCategory:
    # unitId:
    updateEmiCategory(emiCategory: String, unitId: String): GeneralMessage
    
    # Arguments
    # unitId:
    # yearCovered:
    # bldgId:
    updateEstatePropertyTax(
    unitId: String,
    yearCovered: [String],
    bldgId: String
    ): GeneralMessage
    
    # Arguments
    # unitId:
    # constructionStatus:
    # bldgId:
    updateConstructionStatus(
    unitId: String,
    constructionStatus: String,
    bldgId: String
    ): GeneralMessage
    
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
    
    # Arguments
    # certificateId:
    deleteCompletionCertificate(certificateId: String): GeneralMessage
    
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
    
    # Arguments
    # certificateId:
    # fileUploadId:
    deleteFileWithinCompletionCertificate(
    certificateId: String,
    fileUploadId: String
    ): GeneralMessage
    
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
    
    # Arguments
    # limit:
    setDefaultBookingLimit(limit: Int): GeneralMessage
    
    # Arguments
    # projectId:
    # limit:
    addEditBookingLimit(projectId: String, limit: Int): GeneralMessage
    
    # Arguments
    # bookingLimitId:
    deleteBookingLimit(bookingLimitId: String): GeneralMessage
    
    # Arguments
    # scheduleId:
    emailSchedule(scheduleId: String): GeneralMessage
    
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
    
    # Arguments
    # projectId:
    # date:
    validateSchedule(projectId: String, date: String): GeneralMessage
    
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
    
    # Arguments
    # punchlistId:
    # status:
    # punchlistItems:
    processPunchlist(
    punchlistId: String,
    status: String,
    punchlistItems: [PunchlistItemInput]
    ): GeneralMessage
    
    # Arguments
    # punchlistId:
    cancelPunchlist(punchlistId: String): GeneralMessage
    
