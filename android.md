[Back](./README.md)


# Project Lego Android

## Technical Documentation

### GETTING STARTED

Project Lego Android was developed using Android Studio. This project uses Kotlin as the Programming Language, Android Studio Layout Editor for the Interface, and Gradle for connecting different Third-Party Libraries. The target and compiled SDK Version is 30 with a minimum SDK version of 26.
For more information on the IDE and system requirements to enable you to work on the source code, it is available [here](https://developer.android.com/)

### INSTALLATION AND DEVELOPMENT

In order to start the development, first you need to start Android Studio. Import the Project Lego project and then wait for the build to finish.

### PROGRAMMING LANGUAGE

Project Lego Android uses Kotlin for development

### MINIMUM VERSION

Project Lego can run on Android Systems with minimum SDK version 26. It may encounter multiple issues on lower SDKversions.

### APPLICATION ID

com.robinsonslandcorp.projectlego

### DEBUGGING

We use a few debugging tools to test Project Lego functionalities.
We also use Android Virtual Device in Android Studio in order to test the Native Apps in different screen sizes and SDK Versions. 

### THIRD-PARTY LIBRARIES

Most of the third-party libraries are integrated using Gradle. They can be added by searching library names found in the Dependencies tab in the Project Structure window.

##### Important Libraries
**Android Lifecycle** - Used to manage data and connections between activities and fragments.  
**RxAndroid and RxJava** - Used to connect to a network and manage data.   
**Jetpack Compose** - Android’s modern toolkit for building native UI. It simplifies and accelerates UI development on Android.
**Apollo GraphQL** - Used to communicate data between Android and Server.


##### Firebase Platform Libraries.  
**Firebase/Analytics** - Used for App Analytics.  
**Firebase/Crashlytics** - Used to identify causes of crashes from users.  
**Firebase/Performance** - Used to monitor app performance.  

##### UI Libraries
**Compose Coil** - Used for displaying images.
**Accompanist** - Used for various composable that are not native to Jetpack Compose.


##### Other Useful Libraries 
**Android Navigation: Kotlin** - Used to manage connections between different screens and layouts.  
**Esperando** - Used to connect shared data between activies.  
**Dagger-Hilt** - Used for easier data management between activities.  
**Karumi/Dexter** - Used to simplify permission requests and access.  
**OkHTTP** - Used by Android to communicate via Http Protocols.
**Zelory-Compressor** - Used to compress the images before uploading.

### IMPORTANT CLASSES

#### Activities/Fragments

- **MainActivity** - Handles the main activity container which will display all the core.
  ##### Composable/ViewModel Methods

- **SplashScreen** - Handles the display for loading the splashscreen for 2 seconds.
  ##### Composable/ViewModel Methods
  - `startSplash()` - Starts a 2 second delay every time the app is launched.

- **LoginScreen** - Handles the display where users will input email account and password.
  ##### Composable/ViewModel Methods
  - `login()` - Handles the process for Login. Calls the API if all credentials are valid and logs user in.
  - `getArticleByType()` - Handles the process for getting the terms and privacy data.

- **ChangePasswordScreen** - Handles the display when the user wants to change password
  ##### Composable/ViewModel Methods
  - `changePassword()` - Handles the process for changing the password.
  
- **ForgotPasswordScreen** - Handles the display of forgot password
  ##### Composable/ViewModel Methods
  - `sendEmailRecoveryLink()` - Handles the process for sending an email password link if a correct email is provided.  

- **UserProfileScreen** - Handles the display of user profile.
  ##### Composable/ViewModel Methods
  - `fetchProfile()` - Handles the process for getting user data.
  - `updateProfile()` - Handles the process for updating user data.
  - `logout()` - Handles the clearing of data when a user logs out.

- **PrivacyPolicyScreen** - Handles the display of privacy policy.
  ##### Composable/ViewModel Methods
  - `getArticleByType()` - Handles the process for getting the privacy data.
  
- **TermsConditionScreen** - Handles the display of terms and conditions
  ##### Composable/ViewModel Methods
  - `getArticleByType()` - Handles the process for getting the terms data.

- **MainDashboardScreen** - Handles the display of main dashboard; landing screen after login
  ##### Composable/ViewModel Methods
  - `getData()` - Handles the process for getting User data, as well as their field restrictions.    
  - `getAllFieldRestrictions()` - Handles the process for getting field restrictions, called in getData(). 

- **UnitSearchScreen** - Handles the display of Unit Search, the fields Projects, Buildings, and Unit Keyword. As well as 4 Additional redirection buttons below.
- **AdvancedSearchScreen** - Handles the display of Advanced Search with all the query fields required.
  ##### Composable/ViewModel Methods - Unit Search and Advanced Search share ViewModels
  - `getProjectData()` - Requests from the GraphQL API the list of available projects.
  - `getBuildingData()` - Requests from the GraphQL API the list of available buildings.
  - `getUnitTypeData()` - Requests from the GraphQL API the list of available unit types.
  - `getReferenceType()` - Requests from the GraphQL API the list of available advanced search field items; Classification, Project Status, Unit Status, Construction Status, PMD, Key Status, Viewing Status, TOQ.
  - `saveAdvancedSearchResults()` - Saves the data inputted from Advanced Search.
  - `saveUnitSearchResults()` - Saves the data inputted from Unit Search.
  - `bringUpToSearchResult()` - Brings up items when pressed from the drawer.
  - `processTaskClick()` - Handles the logic for when project is more than 5; checker if a new project is selected to call getBuildingData() again; calls function to save selected data; calls bringUpToSearchResult().
  - `bottomSheetSearch()` - Handles the logic for drawer search field.
  - `checkIfSales()` - Handles the logic for checking if the user is sales to disable certain fields on Advanced Search.

- **SearchResultScreen** - Handles the display of items coming from the API, with a search bar on top. Some items are hidden based on a user's department restriction.
  ##### Composable/ViewModel Methods
  - `advancedSearch()` - Requests query data if the user used Advanced Search.
  - `unitSearchQuery()` - Requests query data if the user used Unit Search.
  - `saveAdvancedSearchInput()` - Process the input data for Advanced Search before doing the query. Called before advanceSearch().
  - `saveUnitDetails()` - Save selected unit data to be used in Unit Details and beyond.
  - `topBarSearch()` - Handles the logic for searching units based on Unit Name.
  - `newDefaultPhoto()` - Handles the logic if a new default photo is saved from UnitGalleryScreen and user goes back to SearchResultScreen.
  - `checkIfSales()` - Handles the logic for checking if the user is sales to hide items that are not Unsold-Available or Unsold-Reserved.

- **UnitDetailsScreen** - Handles the display of a specific Unit with all its associated data. It also displays additional items or buttons dependent on user's department restriction.
  ##### Composable/ViewModel Methods
  - `getUnitDetails()` - Gets the saved data from saveUnitDetails().
  - `getUnitPhotos()` - Requests the query data for the unit's photos.

- **UnitGalleryScreen** - Handles the display of a unit's available photos in a carousel manner. Ability to add/edit/delete if user is on marketing deparment and the unit is RFO.
  ##### Composable/ViewModel Methods
  - `getGalleryDetails()` - Gets the saved data from saveUnitDetails().
  - `getUnitPhotos()` - Requests the query data for the unit's photos.
  - `prepareShowData()` - Handles the logic for displaying the selected images. Also handles the logic for when the selected images exceed 15 items.
  - `uploadPhotos()` - Handles the request for uploading; compresses images before uploading.
  - `deletePhotos()` - Handles the request for deleting a photo. Users can now delete Default Photos.
  - `setDefaultPhoto()` - Handles the request for setting the selected default photo.
  - `getDisclaimer()` - Handles the query for Gallery's disclaimer.
  - `editDisclaimer()` - Handles the query to edit the details for Gallery's disclaimer.
  - `unmarkDefaultPhoto()` - Handles the logic for when the users attempts to delete a Default Photo. 

- **UnitPlanScreen** - Handles the display of a unit's plan, in both Image or PDF for. If it is revised or not. Ability to add/edit/delete if user is PDS department.
  ##### Composable/ViewModel Methods
  - `getUnitPlanDetails()` - Requests the query data for the unit's Unit Plans.
  - `uploadPhotos` - Handles the request for uploading; Also uploads PDFs.
  - `deleteUnitPlan()` - Handles the request for deleting a Unit Plan item.
  - `editNormalDisclaimer()` - Handles the request for editing Unit Plan disclaimer.
  - `editRevisedDisclaimer()` - Handles the query for editing Revised Unit Plan disclaimer.
  - `getNormalDisclaimer()` - Handles the query for Unit Plan disclaimerr.
  - `getRevisedDisclaimer()` - Handles the query for Revised Unit Plan disclaimer.

- **UnitStatusScreen** - Handles the display of a unit's status. Ability to edit EMI Status on Sold - EMI Units for BD, TOQ, and AMD users.
  ##### Composable/ViewModel Methods
  - `getUnitDetails()` - Gets the saved data from saveUnitDetails().
  - `updateEmiCategory()` - Handles the request for editing the EMI Category on Sold-EMI units.

- **AccountDetailsScreen** - Handles the display for a unit's accountancy details. Some items are hidden based on a user's department restriction.
  ##### Composable/ViewModel Methods
  - `getAccountDetails()` - Requests the query data for the unit's accountancy details.
  - `parsePaymentScheme()` - Handles the logic for parsing payment scheme data.

- **ConstructionStatusScreen** - Handles the display for a unit's construction status. Field is hidden from Sales. Ability to add/edit/delete items for Construction/PMD users.
  ##### Composable/ViewModel Methods
  - `getConstructionStatus()` - Requests the query data for the unit's construction status details.
  - `updateConstructionStatus()` - Handles the request for updating the unit's construction status.
  - `uploadCompletionCertificate()` - Handles the request for uploading a unit's certificate.
  - `deleteCompletionCertificate()` - Handles the request for deleting a unit's certificate.

- **CertificateOfCompletionScreen** - Handles the display when user taps to view a certificate on ConstructionStatusScreen.

- **LegalDocumentsScreen** - Handles the display for a unit's legal documents. Field is hidden from Sales. Ability to add/edit/delete items for Legal users.
  ##### Composable/ViewModel Methods
  - `getLegalDetails()` - Requests the query data for the unit's legal details.
  - `updateEstatePropertyTax()` - Handles the request for updating the unit's estate property taxes.

- **TurnoverStatusScreen** - Handles the display for a unit's turnover status. Only PMD and TOQ can view this screen.
  ##### Composable/ViewModel Methods  
  - `getUnitTurnover()` - Requests the query data for the unit's unit turnover status.
  - `updateUnitTurnover()` - Handles the request for updating the unit's unit turnover status.

- **ViewingScheduleScreen** - Handles the display for a unit's viewing schedule under Turnover Status Screen. Only PMD and TOQ can view this screen while only TOQ can edit and send invites.
  - `getSchedule()` - Requests the query data for the unit's viewing schedule.
  - `getSapSchedule()` - Requests the query data for the unit's SAP schedules.
  - `saveSchedule()` - Handles the request for updating the unit's viewing schedule on both save to drafts or send option.
  - `emailSchedule()` - Handles the request for sending confirmed schedule.
  - `updateSapBooking()` - Handles the request for updating the unit's sap schedules.
  - `validateSchedule()` - Handles the checking when pressing the date, save to draft, or send to check and see if it's a valid schedule.

- **UnitNotesScreen** - Handles the display for a unit's notes. Only PMD, TOQ, and Admin accounts can view, add, edit, or delete Unit Notes
  - `getUnitNotes()` - Requests the query data for the unit notes associated with the unit.
  - `createUnitNote()` - Handles the request for creating a new unit note.
  - `updateUnitNote()` - Handles the request for updating a unit note.
  - `deleteUnitNote()` - Handles the request for deleting a unit note.
  - `getUnitNoteAttachments()` - Requests the query data for the unit note's attachments.
  - `uploadUnitNoteAttachments()` - Handles the request for adding attachments to existing unit notes.
  - `deleteUnitNoteAttachments()` - Handles the request for removing attachments from existing unit notes. 

- **PunchListScreen** - Handles the display of all punchlists. Can be viewed under Punchlist on the Dashboard
  - `getPunchlists()` - Requests the query data for the punchlists.

- **PunchListFilterScreen** - Handles the display for filtering of specifed punshlists.
  - `getUserProjectData()` - Handles the query data for the punchlists.
  - `getProjectBuildingFilterData()` - Handles the query data for getting the buildings based on the project IDs.
  - `getFilteredResultListIds()` - Handles the request for getting the IDs of the filtered results.
  - `searchBasedOnInput()` - Handles the request for searching a specific punchlist.
  - `applyFilters()` - Handles the request for applying the selected filters.

- **BuyerPunchListScreen** - Handles the display for creating a Buyer Punchlist from the Punchlist Screen.
  - `getUnits()` - Handles the query data for getting the units.
  - `getProjectBuildingData()` - Handles the request for getting the building data for the associated project.
  - `addPunchlistItem()` - Handles the request for adding a punchlist item.
  - `duplicatePunchlistItem()` - Handles the logic behind duplicating a punchlist item.
  - `deletePunchlistItem()` - Handles the request for deleting a punchlist item.
  - `savePunchlist()` - Handles the request for saving the punchlist.
  - `editItemForBuyer()` - Handles the request for editing a punchlist item.

- **DetailedBuyerPunchlistScreen** - Handles the viewing of details of the selected Buyer Punchlist. Only the creator of the Punchlist can edit and cancel the punchlist. Only Construction can process the Punchlist. Anyone can download the punchlist report.
  - `getPunchlist()` - Handles the query data for the associated punchlist.
  - `getPunchlistItems()` - Handles the query data for the punchlist items assoiciated with the punchlist.
  - `processPunchlist()` - Handles the request for processing the punchlist.
  - `cancelPunchlist()` - Handles the request for cancelling the punchlist.
  - `updatePunchlist()` - Handles the request for updating the punchlist.
  - `downloadPunchlistLink()` - Handles the query data for getting the download file link.
  - `downloadBuyerPunchlistFile()` - Handles the request for downloading the punchlist.

- **ToqPunchlistScreen** - Handles the display for creating a TOQ Punchlist from the Punchlist Screen.
  - `addSection()` - Handles the request for adding a section.
  - `editAddSectionName()` - Handles the logic behind editing added section name.
  - `editAddItemName()` - Handles the logic behind editing an item name.
  - `editTOQSection()` - Handles the logic behind editing a section.
  - `editTOQSectionItem()` - Handles the logic behind editing a section item.
  - `editTOQSectionAddItem()` - Handles the logic behind editing the added punchlist item.
  - `saveDuplicateSection()` - Handles the request for duplicating and saving the section.
  - `deleteSection()` - Handles the reqeuest for deleting a section.
  - `deleteTOQSectionItem()` - Handles the request for deleting a section item.
  - `deleteAddedPunchlistFromSection()` - Handles the request for deleting the added punchlist item from the section.
  - `saveNewSectionPunchlistToList()` - Handles the request for saving a new section to the list.
  - `savePunchlist()` - Handles the request for saving the punchlist.

- **DetailedToqPunchlistScreen** - Handles the creation of a TOQ Punchlist from the Punchlist Screen. Only the creator of the Punchlist can edit and cancel the punchlist. Only Construction can process the Punchlist. Anyone can download the punchlist report.
  - `processPunchlist()` - Handles the request for processing the punchlist.
  - `cancelPunchlist()` - Handles the request for cancelling the punchlist.
  - `addSection()` - Handles the request for adding a section.
  - `editAddSectionName()` - Handles the logic behind editing added section name.
  - `editAddItemName()` - Handles the logic behind editing an item name.
  - `editTOQSection()` - Handles the logic behind editing a section.
  - `editTOQSectionItem()` - Handles the logic behind editing a section item.
  - `editTOQSectionAddItem()` - Handles the logic behind editing the added punchlist item.
  - `saveDuplicateSection()` - Handles the request for duplicating and saving a section.
  - `deleteSection()` - Handles the reqeuest for deleting a section.
  - `deleteTOQSectionItem()` - Handles the request for deleting a section item.
  - `deleteAddedPunchlistFromSection()` - Handles the request for deleting the added punchlist item from the section.
  - `saveNewSectionPunchlistToList()` - Handles the request for saving a new section to the list.
  - `savePunchlist()` - Handles the request for saving the punchlist.
  - `downloadPunchlistLink()` - Handles the query data for getting the download file link.
  - `downloadPunchlist()` - Handles the request for processing the punchlist.
  - `getPunchlist()` - Handles the query data for the associated punchlist.
  - `getPunchlistItems()` - Handles the query data for the punchlist items assoiciated with the punchlist.

- **GeneratePunchlistScreen** - Handles the display for generating a punchlist report.
  - `generateReport()` - Handles the request for generating the punchlist report.
  - `generateReportLink()` - Handles the query data for getting the generate report link.

- **CalendarScreen** - Handles the display of unit turnover schedules.
  - `projectsQuery()` - Handles the query data for projects.
  - `getCalendarExportLink()` - Handles the queary data for getting the calendar export link.
  - `exportCalendar()` - Handles the request for downloading the calendar.
  - `getUnitTurnoverSchedules()` - Handles the query data for getting the turnover schedule for a specific project.

- **ProjectScreen** - Handles the display of project listings. Can tap a listing to be sent to the detailed page. Any other department can view except Sales Department.
  - `getAdvancedProjectList()` - Handles the query data for project listing.

- **ProjectDetailsScreen** - Handles the display a specific selected project. Only marketing is able to change the Admin Contact Number of said Project. Any other department can view except Sales Department.
  - `getProjectPhotos()` - Handles the query data for a project's list of photos for both Project and Pre-selling options.
  - `updateProjectAdminContact()` - Handles the request for changing the admin contact number of the project. Only marketing has access.
  - `getProjectUnitCount()` - Handles the query data for a project's unit count.

- **ProjectPhotoGalleryScreen** - Handles the display of the selected photo gallery, either from Project or Preselling Gallery. Only marketing is able to add, edit, delete, the photos. Any other department can view except Sales Department.
  - `getPhotos` - Handles the query data for the selected option (either Project or Pre-selling) for display in the gallery.
  - `uploadPhotos` - Handles the request for uploading the photos.
  - `deletePhoto` - Handles the request for deleting a selected photo.
  - `setDefaultPhoto` - Handles the request for changing the default photo.
  - `unmarkDefaultPhoto` - Handles the request for unmarking the default photo.
  - `getDisclaimer` - Handles the query data for the selected option for display in gallery.
  - `editDisclaimer` - Handles the request to change the selected disclaimer.

- **ProjectPlansScreen** - Handles the display of the type of Project Plans from the ProjectDetailsScreen, can also be accessed from Unit Plans from the View Floor Plans buttons.

- **BidPlan** - Handles the display of Bid Plans of the specific Project. All user can view Bid Plans but only Construction and PDS user can add, edit and delete the project plans.
  - `getProjectPlan` - Handles the query data for a project's Bid Plans.
  - `uploadProjectPlan` - Handles the request for uploading a project plan.
  - `deleteProjectPlan` - Handles the request for deleting a project plan.
  - `updateDescription` - Handles the request for adding or updating the description of a project plan.

- **FCDPlan** - Handles the display of FCD Plans of the specific Project. All user can view Bid Plans but only Construction and PDS user can add, edit and delete the project plans.
  - `getProjectPlan` - Handles the query data for a project's FCD Plans.
  - `uploadProjectPlan` - Handles the request for uploading a project plan.
  - `deleteProjectPlan` - Handles the request for deleting a project plan.
  - `updateDescription` - Handles the request for adding or updating the description of a project plan.

- **BuiltDrawingsPlan** - Handles the display of Built Drawings Plan of the specific Project. All user can view Bid Plans but only Construction and PDS user can add, edit and delete the project plans.
  - `getProjectPlan` - Handles the query data for a project's Built Drawings Plans.
  - `uploadProjectPlan` - Handles the request for uploading a project plan.
  - `deleteProjectPlan` - Handles the request for deleting a project plan.
  - `updateDescription` - Handles the request for adding or updating the description of a project plan.
  
- **KeyPlanUnitizedLayout** - Handles the display of Key Plan and Unitized Layout of the specific Project. All user can view Bid Plans but only Construction and PDS user can add, edit and delete the project plans.
  - `getProjectPlan` - Handles the query data for a project's Key Plan and Unitized Layout.
  - `uploadProjectPlan` - Handles the request for uploading a project plan.
  - `deleteProjectPlan` - Handles the request for deleting a project plan.
  - `updateDescription` - Handles the request for adding or updating the description of a project plan.

- **ProjectMilestonesScreen** - Handles the display of Project Milestones for the selected project. All users can view Project Milestones but only TOQ and Construction users can edit or clear the milestones.
  - `getProjectMilestone` - Handles the query data for a Project's Project Milestones.
  - `saveProjectMilestones` - Handles the request for saving the project milestones.

- **ConstructionProgressScreen** - Handles the display of the selected Project's buildings that can be selected to view their construction progress.
  - `getBuildingsByProjectId` - Handles the query data of the buildings of the selected Project.

- **ConstructionProgressDetails** - Handles the display of a selected building's construction progress. 
  - `getConstructionProgress` - Handles the query data of the selected building's construction progress.
  - `saveConstructionProgress` - Handles the request for saving the construction progress.

 

  

### ARCHITECTURE USED

Project Lego Android follows and uses the Model-View-ViewModel Architecture (MVVM). It consists of a Composable file which is the UI layout definition for the screen, a NavController that is the UI controller that navigates and displays the data, and the ViewModel, a class that prepares the data for viewing in the Composables and reacts to user interactions.

[here](https://drive.google.com/file/d/14qTQycPw3L7csnNIkNvsJa5OWXVVHZRq/view?usp=share_link)

![alt text](https://github.com/Rogomi/Traxion-ProjectLego-TechDoc/blob/develop/UMS-architecture.png)

