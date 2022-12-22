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
  - `login()` - Handles the process for Login. Calls the REST API if all credentials are valid and logs user in.
  - `getArticleByType()` - Handles the process for getting the Article data.

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
  - `getArticleByType()` - Handles the process for getting the Article data.
  
- **TermsConditionScreen** - Handles the display of terms and conditions
  ##### Composable/ViewModel Methods
  - `getArticleByType()` - Handles the process for getting the Article data.

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
  - `processTaskClick()` - Handles the logic for when project is more than 5; checker for if a new project is selected to getBuildingData() is called again; calls function to save selected data; calls bringUpToSearchResult().
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
  - `deletePhotos()` - Handles the request for deleting a photo.
  - `setDefaultPhoto()` - Handles the request for setting the selected photo default.
  - `getDisclaimer()` - Handles the query for Gallery's disclaimer.
  - `editDisclaimer()` - Handles the query to edit the details for Gallery's disclaimer.

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


### ARCHITECTURE USED

Project Lego Android follows and uses the Model-View-ViewModel Architecture (MVVM). It consists of an xml file which is the UI layout definition for the screen, a Fragment that is the UI controller that displays the data, and the ViewModel, a class that prepares the data for viewing in the Fragment and reacts to user interactions.

[here](https://drive.google.com/file/d/1ikD6dEHvLZIGkIyTN_1Zs-iRh_RnZbgy/view?usp=sharing)

![alt text](https://github.com/Rogomi/Traxion-ProjectLego-TechDoc/blob/develop/UMS-architecture.png)

