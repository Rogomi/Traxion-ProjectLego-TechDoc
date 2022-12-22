[Back](README.md)

# Traxion-ProjectLego UMS

## Technical Documentation

### GETTING STARTED

UMS requires Xcode 13.0 and above for development. This project uses Swift 5 as the Programming Language, Storyboard for the Interface and CocoaPods and SPM for Third Party Libraries. The current Xcode version used for development is 13.4. The minimum iOS Version required is iOS 13.0

### INSTALLATION AND DEVELOPMENT

In order to start with the development, first, you will need an Apple account for development. It must be under the team Rogomi, Inc. Then, open the Traxion-ProjectLego.xcworkspace under the repository root directory. If possible, do a pods repo update in order to avoid missing library errors. As well as update SPM to latest package versions.

### PROGRAMMING LANGUAGE

UMS uses the latest Swift version, Swift 5, for development.

### MINIMUM VERSION

UMS requires devices with at least iOS 13.0

### APPLICATION ID

com.robinsonslandcorp.projectlego

### DEBUGGING

We use a few debugging tools to test functionalities.

For the Native App, we use Xcode's debugging console to create breakpoints and test variables, API responses, and identify null objects which sometimes causes the crash.

To test the API before integrating for app usage, we use Postman. Postman is a very reliable REST API tool. We can test different HTTP Methods especially POST, PATCH, PUT, DELETE and GET. We can also add header variables to test SSO and token authentications.

We also use iOS Simulator in order to test the apps in different screen sizes and iOS Versions.


### THIRD-PARTY LIBRARIES


#### Cocoapods
Most of the third party libraries are installed using CocoaPods. They can be added by searching library names found in https://cocoapods.org/, inserting them in the Podfile and running the pod install command in the Terminal.

#### Swift Package Manager (SPM)
Some of the third party libraries are installed using SPM

##### Important Libraries
**Alamofire** - For Web API Communications  
**SwiftyJSON** - To ease up processing of response data  
**ObjectMapper** - To easily create models for response data  
**Apollo** - To communicate with the GraphQL API

##### UI Libraries
**IQKeyboardManagerSwift** - To automatically scroll up the UITextView on screen when the keyboard is up.  
**IBAnimatable** - To easily add special UI Designs on specific views, and see them reflected on the Interface Builder. Also has methods to animate views.  
**InitialsImageView** - To easily use letters in profile icon incase profile image is unavailable.  
**Pulley** - Pull down UI.  
**TLPhotoPicker** - Used to select multiple images.  
**MBProgressHUD** - Used to add heads up display on screen to indicate loading while user is waiting for data to be loaded from the API.  
**Kingfisher** - To easily load Images from URL and has caching functions.  

### ACTIVITIES AND CONTROLLERS  

#### Core Classes
- **AppDelegate** - manages most of the pre-startup items like Firebase configurations, etc.
  ##### Configured items
  Firebase
    

#### View Controllers
  

##### **LandingViewController** - controls the behavior of the splash screen

###### **Methods and Calculated Variables**
- `viewDidLoad` - calls rotate function
- `viewDidAppear` - is calls `checkToken` and `goToLogin` depending on the situation
- `checkToken` - checks if the token is still valid
- `proceed` - shows `DashboardViewController`
- `terms` - shows `UserAgreementViewController`
- `goToLogin` - shows `LoginViewController`
- `rotate` - makes the loading icon rotate


##### **LoginViewController** - controls the behavior of the login screen

###### **Methods and Calculated Variables**
- `didTapLoginBtn` - checks if email and password is not empty and calls `login`
- `didTapForgotBtn` - calls `goToForgotPassword` when the button  is tapped
- `unwindToLogin` - marks the screen as an unwind point
- `terms` - shows `UserAgreementViewController`
- `goToForgotPassword` - shows `ForgotPasswordViewController`  
- `goToDashboard` - shows `DashboardViewController`
- `hideError` - hides the error message
- `showError` - shows error message  
- `login` - calls the back-end endpoint to login using the credentials provided by the user



##### **ForgotPasswordViewController** - controls the behavior of the forgot password screen

###### **Methods and Calculated Variables**
- `didTapEmailBtn` - calls `forgotPassword`
- `didTapBackBtn` - goes back to login
- `goToResult` - shows `ResultForgotPasswordViewController` and passes information whether it is a success or not
- `forgotPassword` - calls the endpoint to send an email to the email provided




##### **ResultForgotPasswordViewController** - controls the behavior of the result screen

###### **Methods and Calculated Variables**
- `var success` - changes the value of the `message` variable when set to true
- `viewDidLoad` - calls `setup()` when view is loaded
- `viewWillAppear` - calls `setup()` when view is loaded
- `didTapMainButton` - calls `backToLogin` when success and `popOrDismiss` otherwise
- `didTapSecondaryButton` - calls `backToLogin`
- `backToLogin` - goes back to login screen
- `setup` - sets up the appearance of the screen depending if the result is success 




##### **ChangePasswordEmailViewController** - controls the behavior of the change password screen when from email

###### **Methods and Calculated Variables**
- `didTapChangePasswordButton` - calls `changePassword`
- `changePassword` - calls the endpoint to change password
- `hideError` - hides the error message
- `showError` - shows the error message




##### **ResultChangePasswordViewController** - controls the behavior of the change password screen when from email

###### **Methods and Calculated Variables**
- `viewDidLoad` - sets the title of the `backButton` based on the `isProfile` variable
- `didTapBackButton` - calls `goToLogin` or `popOrDismiss` depending on the value of `isProfile`
- `goToLogin` - shows login screen



##### **UserAgreementViewController** - controls the behavior of the user agreement screen

###### **Methods and Calculated Variables**
- `var isTappable` - changes some buttons depending on the new value
- `viewDidLoad` - assigns delegates 
- `viewWillAppear` - calls `getAgreement`
- `didTapAcceptButton` - calls `postUserLog`
- `goToDashboard` - shows `DashboardViewController`
- `didTapBackButton` - calls `sessionLogout`
- `postUserLog` - calls endpoint to post user log
- `getAgreement` - endpoint to get user agreement 
- `scrollViewDidScroll`
- `webView(...didFinish)` 



##### **DashboardViewController** - controls the behavior of the user dashboard screen, contains two container views, UnitSearchViewController and AdvancedSearchViewController
- `showFields` - dynamic function, is called in `SearchPulleyViewController` to display the fields in the drop down
- `viewWillAppear` - calls `getUser` and `getFieldRestrictions`
- `prepare` - calls the `showFields` function of `UnitSearchViewController` and `AdvancedSearchViewController`
- `setupProjects` - calls the `setupProjects` function of `UnitSearchViewController` and `AdvancedSearchViewController`
- `setupBuildings` - calls the `setupBuildings` function of `UnitSearchViewController` and `AdvancedSearchViewController`
- `setupReferences` - calls the `setupReferences` function of `UnitSearchViewController` and `AdvancedSearchViewController`
- `didTapProfileButton` - navigates to the profile screen when the button is tapped
- `customSegmentValueChanged` - changes the container view depending on the segment selected
- `didTapSearchButton` - calls the `searchUnit` function of `SearchPulleyViewController`
- `getUser` - endpoint for getting user details
- `getFieldRestrictions` - endpoint for getting field restrictions depending on department
- `setUser` - sets the image of the current user



##### **ProfileViewController** - controls the behavior of the user profile screen

###### **Methods and Calculated Variables**
- `viewWillAppear` - calls `getUser`
- `getUser` - endpoint for getting user details
- `didTapCameraButton` - navigates user to edit profile screen
- `didTapEditButton` - navigates user to edit profile screen
- `didTapTermsButton` - navigates user to terms and conditions screen
- `didTapPrivacyButton` - navigates user to privacy policy screen
- `didTapChangePasswordButton` - navigates user to change password screen
- `didTapLogoutButton` - logs the user out and navigates to login screen




##### **EditProfileViewController** - controls the behavior of the edit user profile screen

###### **Methods and Calculated Variables**
- `viewWillAppear` - calls `getUser`
- `getUser` - endpoint for getting user details
- `didTapSaveButton` - calls `editUser`
- `editUser` - endpoint for updating user details
- `didTapImageButton` - calls `openPicker`
- `openPicker` - opens camera/gallery picker for photo update



##### **AgreementViewController** - controls the behavior of the TNC, and privacy policy screens

###### **Methods and Calculated Variables**
- `var isPrivacyPolicy` - changes agreement type depending on the value
- `viewWillAppear` - calls `getPrivacyPolicy` or `getTNC`
- `getTNC` - calls endpoint to get terms and conditions
- `getPrivacyPolicy` - calls endpoint to get privacy policy



##### **ChangePasswordUserViewController** - controls the behavior of the user change password screen

###### **Methods and Calculated Variables**
- `didTapChangePasswordButton` - calls `changePassword`
- `changePassword` - calls the endpoint to change password
- `hideError` - hides the error message
- `showError` - shows the error message



##### **ConstructionStatusViewController** - controls the behavior of the construction status screen

###### **Methods and Calculated Variables**
- `isEdit` - toggles the screen between editing and viewing
- `isAdd` - checks if you are adding additional files
- `selectedCertificate` - contains the value if the selected certificate is main or additional
- `setupRestrictions` - sets up department restrictions
- `didTapBackButton` - goes back the previous screen
- `didTapKebabButton` - opens the menu screen
- `didTapConstructionStatusButton` - opens the selection for construction status details
- `didTapAddButton` - calls `setupMainCertificate` and sets isAdd to true
- `didTapSaveButton` - validates the data and calls `updateConstructionStatus` and `uploadFiles`
- `refreshData` - clears cache and reloads the data
- `getConstructionStatus` - calls the endpoint for construction status details 
- `initConstructionStatus` - initializes the view of the screen
- `setupAddAdditionalFiles` - sets the screen to accomodate adding of additional files
- `setupCertificationOfCompletions` - initializes the certificate of completion views
- `setupIsEdit` - sets up the certificates if the user is in editing mode
- `updateConstructionStatus` - calls the endpoint to update the construction status details
- `setupMainCertificate` - sets up the main certificate view
- `didTapMainCertificateButton` - calls `openPicker` to add a certificate file
- `didTapRemoveMainCertificateButton` - removes the added main certificate file
- `didTapSelectCategoryButton` - opens the selection for the category of the certificate
- `didTapSelectStatusButton` - opens the selection for the status of the certificate
- `openPicker` - opens gallery/document picker for certificate update
- `uploadFiles` - calls the endpoint to upload files
- `imagePickerController` - updates the screen depending on the result of `openPicker`
- `imagePickerControllerDidCancel` - closes the image picking view
- `documentPicker` - updates the screen depending on the result of `openPicker`
- `documentPickerWasCancelled` - closes the document picking view


##### **CocAdditionalFilesViewController** - controls the behavior for the certificate of completion additional files

###### **Methods and Calculated Variables**
- `setupAdditionalFiles` - initializes the views for the certificate of completion additional files



##### **LegalViewController** - controls the behavior of the legal details screen

###### **Methods and Calculated Variables**
- `isSeeAll` - boolean value, hides the seeAll button if false
- `isEdit` - boolean value, toggles the view for editing/viewing 
- `didTapBackButton` - goes back to the previous screen if the button is tapped
- `didTapSeeAllButton` - shows all the year covered values if tapped
- `didTapKebabButton` - shows the menu if tapped
- `didTapAddButton` - will add a year covered input if tapped
- `didTapSaveButton` - collects all the current year covered values and calls `updateRealEstateTax`
- `updateRealEstateTax` - calls an endpoint to save the real estate tax year covered
- `setupRestrictions` - sets up restrictions based on department
- `setupRealEstateTax` - sets up the initial view for the real estate tax
- `setupEditRealEstateTax` - sets up the editing view for the real estate tax
- `getLegalDetails` - calls and endpoint to get the legal details of the unit
- `initLegalDetails` - initializes the legal details values



##### **GeneralUnitDetailsViewController** - controls the behavior of the unit details screen

###### **Methods and Calculated Variables**
- `viewWillAppear` - calls `initUI`
- `didTapImage` - navigates the user to the gallery view when tapping the unit image
- `setupFields` - sets up the visibility of fields based on the restrictions
- `didTapAccountDetails` - navigates the user to the account details screen when tapping the account details view
- `didTapViewDetails` - navigates the user to the unit details screen when tapping the view details button
- `didTapViewUnitPlan` - navigates the user to the unit plan screen when tapping the button
- `didTapConstructionStatus` - navigates the user to the construction status screen when tapping the view
- `didTapLegalDocuments` - navigates the user to the legal documents screen when tapping the view
- `didTapUnitMilestonesButton` - navigates the user to the unit milestones screen when tapping the view
- `getUnitDetails` - calls the endpoint for the unit details data
- `initUI` - initializes the ui for the current screen
- `setupRestrictions` - sets up the restrictions based on the department
- `getUnitPhotos` - calls the endpoint for the unit photos
- `initUnitDetails` - initializes the unit details data to the views



##### **AccountDetailsViewController** - view that manages the display of Account Details

###### **Methods and Calculated Variables**
- `setupFields` - hides and shows certain views depending on user restrictions
- `getAccountDetails` - call endpoint to get unit account details
- `initAccountDetails` - setups the labels on screen based on data retrieved from `getAccountDetails`



##### **UnitPlanViewController** - view that manages the display Unit Plan details and navigations to update the Unit Plan

###### **Methods and Calculated Variables**
- `isRevisedSelected` - variable that holds the value 'true' if selected unit type is Revised
- `hasUP` - variable that holds the value 'true' if unit has a unit plan
- `hasRUP` - variable that holds the value 'true' if unit has a revised unit plan
- `refreshData` - refreshes the screen to display proper date when edits are made
- `setupRestrictions` - hides and shows certain views depending on user restrictions
- `didTapRUPImage` - navigates to gallery view of revised unit plan image
- `didTapUnitPlanButton` - navigates to gallery view of unit plan image
- `openImagePicker`- opens camera/gallery picker for photo update
- `openPDFPicker` - opens pdf/document picker for pdf update
- `didTapUPEditFileButton` - navigates to edit unit plan file screen
- `didTapRUPEditFileButton` - navigates to edit revised unit plan file screen
- `didTapUpDeleteButton` - shows delete unit plan option menu
- `didTapRupDeleteButton` - shows delete revised unit plan option menu
- `didTapUpEditDisclaimerButton` - navigates to edit disclaimer for unit plan screen
- `didTapRupEditDisclaimerButton` - navigates to edit disclaimer for revised unit plan screen
- `getUnitPlanDetails` - call endpoint to get unit plan details
- `initUnitPlanDetails` - setups the labels on screen based on data retrieved from `getUnitPlanDetails`
- `getDisclaimers` - call endpoint to get disclaimer and populate disclaimer label for unit plan and revised unit plan



##### **UnitStatusViewController** -  view that manage the display of EMIs for Unit Status

###### **Methods and Calculated Variables**
- `didTapEditSaveButton` - shows EMI options menu
- `updateEMI` - call endpoint to update EMI category
- `setupFields` - setups the views on the screen based on data retrieved from `getUnitDetails`
- `getUnitDetails` - call endpoint to get unit details



##### **UnitStatusEMIViewController** - view that manages the selection/adding of EMIs for Unit Status

###### **Methods and Calculated Variables**
- `firstChoice` - dynamic function called if the first button is selected
- `secondChoice` - dynamic function called if the second button is selected
- `c` - dynamic function called when the save button is tapped
- `didSelectFirst` - calls the `firstChoice` function
- `didSelectSecond` - calls the `secondChoice` function
- `didTapSaveButton` - saves the text from the input field and calls the `customChoice` function



##### **PdfViewController** - view that manages the display of PDF details for the selected file

###### **Methods and Calculated Variables**
- `initUnitPlanPdf` - setups the views based from the file passed to the screen



##### **UnitPlanEditFileViewController** - view that manages the edit of PDF or Image for Unit Plan

###### **Methods and Calculated Variables**
- `isRevised` - variable that holds the value 'true' if unit plan type is 'Revised'
- `replaceImage` - passed function that opens the camera/gallery picker for photo update
- `replacePDF` - passed function that opens the pdf/document picker for photo update
- `didTapReplaceWithImageButton` - calls the `replaceImage` function
- `didTapReplaceWithPDFButton` - calls the `replacePDF` function



##### **UnitPlanUploadFileViewController** - view that manages the adding/initial upload of PDF or Image for Unit Plan

###### **Methods and Calculated Variables**
- `isRevised` - variable that holds the value 'true' if unit plan type is 'Revised'
- `uploadSuccess` - passed function to refresh the previous screen on file update
- `didTapUploadButton` - call endpoint to upload new file
- `initDisplay` - setups the views based on file details passed on the screen



##### **DeleteConfirmationViewController** - view that manages the confirmation prompt to confirm the deletion of a Unit Plan

###### **Methods and Calculated Variables**
- `isRevised` - variable that holds the value 'true' if unit plan type is 'Revised'
- `deleteSuccess` - passed function to refresh the previous screen on file deletion
- `initLabel` - setups the views based on file details passed on the screen
- `didTapDeleteButton` - call endpoint to delete selected unit plan
- `didTapCancelButton` - closes the option menu and return to previous screen



##### **SearchResultsViewController** - view that manages the search results returned from the api

###### **Methods and Calculated Variables**
- `isAdvancedSearch` - boolean field, distinguishes advanced search from unit search 
- `isLoading` - boolean field, used to store the value if the api is loading data
- `isSalesDepartment` - boolean fied, used to check if the user is from sales department
- `textFieldChanged` - monitors the text field if any changes happen, filters the data based on the text
- `numberOfSections` - controls the number of sections the tableview will display
- `countFiltered` - the total number of results based on the filter
- `tableView - numberOfRowsInSection` - controls the number of rows the tableview will display in a section
- `tableView - cellForRowAt` - manages the views displayed for each cell
- `tableView - didSelectRowAt` - manages the selection of the row
- `loadSearchUnitsV2` - calls the unit search endpoint
- `loadSearchUnitsAdvancedV2` - calls the advanced search endpoint
- `SearchResultGroup` - the grouping of each search result



##### **GalleryViewController** - manages the gallery view 

###### **Methods and Calculated Variables**
- `isUnitPlan` - boolean value, stores the value if the view is from unit plan
- `isImageOnly`- boolean value, stores the value if the gallery view should only display an image
- `initFields` - initializes the fields for the view
- `setupRestrictions` - sets up the restrictions based on the department
- `setupFields` - sets up the fields for the view
- `getUnitPhotos` - calls an endpoint to get the gallery photos
- `makeDefault` - calls an endpoint to make the current photo the default
- `deletePhoto` - calls an endpoint to delete the current photo
- `didTapKebabButton` - opens the menu
- `collectionView` - the view that contains the images
- `collectionView - numberOfItemsInSection` - the number of images to be displayed
- `collectionView - cellForItemAt` - sets the views for the cell
- `collectionView - didSelectItemAt` - is called when an image is tapped in the collection view
- `scrollViewDidEndDecelerating` - manages the scrolling of the image
- `getDisclaimers` - calls an endpoint to get the disclaimer text



##### **GalleryOptionsViewController** - menu screen showing the gallery options

###### **Methods and Calculated Variables**
- `editDisclaimer` - opens a new view for editing the disclaimer text
- `addEdit` - opens a new view for adding photos
- `delete` - dynamic function is called when the delete button is tapped
- `makeDefault` - dynamic function is called when make default is tapped
- `didTapEditDisclaimerTextButton` - calls `editDisclaimer`
- `didTapMakeDefault` - calls `makeDefault`
- `didTapAddEditButton` - calls `addEdit`
- `didTapDeleteButton` - calls `delete`



##### **EditDisclaimerViewController** - manages the editing of disclaimer text

###### **Methods and Calculated Variables**
- `editSuccess` - dynamic function called when saving is successful
- `didTapSaveButton` - calls the endpoint for saving the disclaimer and calls the function `editSuccess` after successfully saving
- `initLabels` - initializes the labels
- `textView - shouldChangeTextIn` - contains a checker for text count



##### **GalleryEditAddPhotoViewController** - manages the adding of additional photos

###### **Methods and Calculated Variables**
- `uploadSuccess` - dynamic function is called when the upload is successfull
- `didTapUploadButton` - validates the images and calls the function `uploadPhotosV2`
- `uploadPhotosV2` - calls an endpoint to upload the selected photos
- `shouldDismissPhotoPicker` - is called when the picker is closed
- `dismissPhotoPicker` - is called when the picker is closed
- `photoPickerDidCancel` - is called when the cancel button is tapped
- `dismissComplete` - is called when the picker is closed
- `didExceedMaximumNumberOfSelection` - is called when the maximum number is reached
- `handleNoAlbumPermissions` - handles no album permissions
- `handleNoCameraPermissions` - handles no camera permissions
- `askPermissions` - asks permission from the user
- `setupPhotoPicker` - sets up the photo picker
- `tableView - numberOfRowsInSection` - displays the number of rows in the section
- `tableView - cellForRowAt` - manages the cells to be displayed
- `ImageUpload` - object that contains image and their name



##### **GalleryDeleteViewController** - a view that manages the deletion of gallery images

###### **Methods and Calculated Variables**
- `delete` - dynamic function called when the delete button is tapped
- `didTapCancelButton` - closes the view
- `didTapDeleteButton` - calls the delete function



##### **FailedMessageViewController** - a view that displays a failed message

###### **Methods and Calculated Variables**
- `alertTitle` - the title to be displayed in the view
- `alertMessage` - the message to be displayed in the view
- `didTapGotItButton` - is called when the got it button is tapped
- `initLabels` - inits the labels for the view


##### **SearchPulleyViewController** - manages the pull down view, sets the drawer position based on the dynamic functions

###### **Methods and Calculated Variables**
- `setDrawerPosition` - sets the drawer position
- `primaryVC` - the main view controller
- `drawerVC` - the drawer view controller



##### **SearchDrawerViewController** - manages the drawer view for the selectable items and its search 

###### **Methods and Calculated Variables**
- `position` - the position of the drawer
- `setToHalf` - sets the drawer position to half the screen
- `selectedField` - the selected field
- `isSalesDepartment` - boolean value, true if the department is sales
- `setupFields` - sets up the fields for the view
- `getProjects` - calls an endpoint to get the projects
- `getBuildings` - calls an endpoint to get the buildings
- `getUnitTypes` - calls an endpoint to get the unit types
- `getReferenceTypes` - calls an endpoint to get the reference types
- `updateBuildings` - updates the buildings based on the projects selected
- `textFieldChanged` - updates the items to be displayed depending on the text
- `tableView - numberOfRowsInSection` - displays the number of rows in the section
- `tableView - cellForRowAt` - manages the views for the cell
- `tableView - didSelectRowAt` - is called when a row is tapped
- `PulleyDrawerViewControllerDelegate` - delegate for the Pulley library, used for the drawer views



##### **UnitSearchViewController** - manages the view displaying the unit search

###### **Methods and Calculated Variables**
- `showFields` - dynamic function that passes a variable, is called in `DashboardViewController`
- `didTapProjectsButton` - calls the dynamic function `showFields` and passes projects enum
- `didTapBuildingsButton` - calls the dynamic function `showFields` and passes buildings enum
- `didTapSearchButton` - validates the inputs and navigates to the search results view
- `setupProjects` - sets up the text for the projects view
- `setupBuildings` - sets up the text for the buildings view



##### **AdvancedSearchViewController** - manages the view displaying the advanced search

###### **Methods and Calculated Variables**
- `showFields` - dynamic function that passes a variable, is called in `DashboardViewController`
- `isSalesDepartment` - boolean value, true if the department is sales
- `didTapProjectsButton` - calls the dynamic function `showFields` and passes projects enum
- `didTapBuildingsButton` - calls the dynamic function `showFields` and passes buildings enum
- `didTapUnitTypeButton` - calls the dynamic function `showFields` and passes unit type enum
- `didTapProjectClassificationButton` - calls the dynamic function `showFields` and passes the project classification enum
- `didTapProjectStatusButton` - calls the dynamic function `showFields` and passes the project status enum
- `didTapUnitStatusButton` - calls the dynamic function `showFields` and passes the unit status enum
- `didTapConstructionStatusButton` - calls the dynamic function `showFields` and passes the construction status enum
- `didTapPunchlistStatus` - calls the dynamic function `showFields` and passes the pr enum
- `didTapKeyStatus` - calls the dynamic function `showFields` and passes the key status enum
- `didTapViewingStatusButton` - calls the dynamic function `showFields` and passes the viewing status enum
- `didTapTOQPunchlistButton` - calls the dynamic function `showFields` and passes the toq punchlist enum
- `didTapSearchButton` - checks the selected inputs and navigates the user to the search results view
- `changeViewsAlpha` - changes the views alpha values
- `setupSalesFields` - sets up the fields to be disabled if sales
- `setupProjects` - sets up the view if a project is selected, also sets the isSelected value of a project
- `setupReferences` - sets the isSelected value of a reference
- `setupBuildings` - sets up the view if a building is selected, also sets the isSelected value of a building
- `RangeSeekSliderDelegate` - manages the returned results if the range is moved



##### **ChangePasswordViewController** - manages the change password view

###### **Methods and Calculated Variables**
- `rules` - contains the rules for the password
- `PasswordRules` - enum listing the possible rules for the password
- `newPasswordField - didSet` - adds the `textFieldDidChange` function
- `newPasswordField - textFieldDidChange` - updates the views depending on the inputted password, calls `updateReqs`
- `updateReqs` - checks if the input is correct or wrong
- `setupRequirements` - sets up the display for the rules, calls `setupRuleDisplay`
- `setupRuleDisplay` - sets up the display for one rule
- `PasswordValidator` - checker that returns if the password follows the rules



##### **StatusOptionsViewController** - View that displays the selection of status options

###### **Methods and Calculated Variables**
- `setupOptions` - sets up the options to display
- `StatusOptions` - enum containing the current options for status



##### **EditViewController** - Reusable view that displays an edit and cancel button

###### **Methods and Calculated Variables**
- `editOption` - dynamic function called when the edit button is tapped
- `cancelOption` - dynamic function called when the cancel button is tapped
- `didTapEditButton` - calls the `editOption` function
- `didTapCancelButton` - calls the `cancelOption` function and closes the view



##### **DeleteViewController** - Reusable view that displays a delete and cancel button

###### **Methods and Calculated Variables**
- `confirmationText` - the text to be displayed when the delete view is shown
- `deleteOption` - dynamic function called when the delete button is tapped
- `didTapDeleteButton` - calls the `deleteOption` function
- `didTapCancelButton` - closes the delete view



### ARCHITECTURE

![alt text](https://github.com/Rogomi/Traxion-ProjectLego-TechDoc/blob/develop/UMS-architecture.png)


