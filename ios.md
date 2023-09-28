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
- `unmarkDefaultPhoto` - calls an endpoint to unmark the current default photo



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
- `checkIfDefaultPhoto` - checks if the photo is the default photo and changes the labels accordingly


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



##### **UnitNotesViewController** - View that displays the unit notes of the selected unit

###### **Methods and Calculated Variables**
- `getUnitNotes` - calls an endpoint to get all unit notes of the selected unit
- `cell.editUnitNote` - navigates the user to the edit view of the selected unit note
- `cell.deleteUnitNote` - manages the deletion of the selected unit note upon users approval
- `didTapAddButton` - navigates the user to the add unit note view



##### **UnitNoteDetailsViewController** - View that display the details of the selected unit note

###### **Methods and Calculated Variables**
- `initUnitNoteDetails` - initializes the labels of the view using the information of the selected unit note
- `getUnitNoteAttachments` - calls an endpoint to get all the attachments of the selected unit note
- `storeAndShare` - handles the viewing and sharing of the selected attachment of the unit note



##### **UnitNoteAddEditViewController** - View that displays the edit or add view for unit notes

###### **Methods and Calculated Variables**
- `isEdit` - variable that is used to check if the view is for editing or adding a unit note
- `setupEditView` - initializes the labels and fields of the unit note to be edited 
- `didTapSaveButton` - calls an endpoint to either edit or add a unit note
- `getUnitNoteAttachments` - calls an endpoint to get all the attachments of the selected unit note
- `uploadFiles` - calls an endpoint to edit or add new attachments for the selected unit note
- `deleteAttachment` - manages the deletion of the selected unit note attachment upon users approval
- `documentPicker` - navigates the user to the document picker view for editing or adding an attachment



##### **UnitTurnoverViewController** - View that displays the turnover details of the selected unit

###### **Methods and Calculated Variables**
- `getUnitTurnover` - calls an endpoint to get all the turnover details of the selected unit
- `initUnitTurnover` - initializes the labels and fields of the view using the turnover detials of the unit
- `goToViewingView` - manages the transformation of the labels and fields of the view to display mode
- `goToEditView` - manages the transformation of the lables and fields of the view to edit mode
- `didTapViewingSchedule` - navigates the user to the viewing schedule view of the unit turnover



##### **ViewingScheduleViewController** - View that displays the viewing schedule of a unit turnover

###### **Methods and Calculated Variables**
- `initFields` - initializes the default values for the labels and fields of the viewing schedule
- `setupFields` - setups the values for the labels and fields using the retrieved data related to the viewing schedule
- `getViewingSchedule` - calls an endpoint to get the viewing schedule for the unit turnover
- `getSapSchedules` - calls an endpoint to get the SAP schedules of the viewing schedule
- `didTapEditButton` - navigates to the edit view of the viewing schedule



##### **ViewingScheduleEditViewController** - View that manages the edit option of the viewing schedule

###### **Methods and Calculated Variables**
- `setupFields` - setups the values for the labels and fields using the data of the viewing schedule
- `getViewingSchedule` - call an endpoint to get the viewing schedule for the unit turnover
- `validateSchedule` - calls an endpoint to validate the availability of the viewing schedule
- `didTapSendButton` - navigates to the preview screen of the new viewing schedule
- `didTapTurnoverEngineerButton` - calls an endpoint to retrieve the details of the available turnover engineer for the viewing schedule
- `saveViewingSchedule` - calls an endpoint to save the new viewing schedule



##### **PreviewMockupViewController** - View that handles the preview for the details of the viewing schedule

###### **Methods and Calculated Variables**
- `initDetails` - initializes the details of the viewing schedule before sending it to concerned parties
- `didTapSendButton` - calls an endpoint to send the viewing invite to the buyer's email upon the approval of the user



##### **UpdateBookingViewController** - View that handles the update option for the booking of the viewing schedule

###### **Methods and Calculated Variables**
- `uneditableFields` - initializes the state of the uneditable fields based on the booking data
- `setupFields` - setups the values of the labels and fields based on the booking data
- `saveViewingSchedule` - calls an endpoint to save the updated booking date for the viewing schedule


##### **PunchlistViewController** - View that handles the display of punchlists

###### **Methods and Calculated Variables**
- `didTapFilterButton` - navigates to the filter view for the punchlists
- `didTapAddPunchlistButton` - handles the showing of the options to add a new punchlist
- `didTapToqButton` - navigates to the view for adding a new toq punchlist
- `didTapBuyerButton` - navigates to the view for adding a new buyer punchlist
- `didTapEraseTextButton` - handles the function that clears of the search punchlist text field
- `refreshData` - function that refreshes the punchlists
- `getPunchlist` - calls an endpoint to get all available punchlists for display
- `textFieldChanged` - handles the corresponding functions when text is changed on different text fields



##### **PunchlistFilterViewController** - View that handles the filter function for the punchlists view

###### **Methods and Calculated Variables**
- `currentFilter` - variable that checks if filters to be used is for a toq punchlist or a buyer punchlist
- `getProjects` - calls an endpoint to get the projects available as filter
- `getBuildings` - calls an endpoint to get the buildings available as filter
- `didTapApplyAllButton` - calls the function that applies the filters selected
- `didTapClearAllButton` - calls the function that clears all the selected filters



##### **PunchlistTableViewCell** - Table View Cell that contains the outlets for the punchlist items cells display



##### **PunchlistFilterTableViewCell** - Table View Cell that contains the outlets and functions for the punchlist filters item

###### **Methods and Calculated Variables**
- `setup` - setup the initial values of the filters available
- `didTapItem` - calls the dynamic function for the selected filter item



##### **FilterHeaderTableViewCell** - Table View Cell that contains the outlets and functions for the punchlist filters header

###### **Methods and Calculated Variables**
- `setSelected` - call the function that sets the focus on the selected header



##### **BuyerPunchlistAddEditViewController** - View that handles the adding and editing of buyer punchlists

###### **Methods and Calculated Variables**
- `isAdd` - boolean variable that is used to check if view will handle add punchlist display and functions
- `isEdit` - boolean variable that is used to check if view will handle edit punchlist display and functions
- `isProcess` - boolean variable that is used to check if view will handle process punchlist display and functions
- `uneditableFields` - variable that is to check uneditable fields that have their own functions then tapped
- `requiredFields` - variable that is to check for required fields
- `didTapAddButton` - function that handles the adding of new an empty punchlist item
- `didTapSaveButton` - function that asks for confirmation when making changes to existing punchlists
- `savePunchlist` - calls an endpoint that saves new punchlist or save changes on edited or processed punchlists
- `initEditFields` - functions that initializes the initial display when editing and processing punchlists
- `getProjects` - calls an endpoint to get projects available for adding and editing punchlists
- `getBuildings` - call an endpoint to get buildings available for adding and editing punchlists
- `loadSearchUnitsV2` - calls an endpoint to get units available for adding and editing punchlists
- `textFieldShouldBeginEditing` - functions that handles the corresponding actions for each the textfields tapped
- `buyerPunchlistItemTableViewCell` - function that handles in saving the changes on the textfields of the punchlist itmes



##### **BuyerPunchlistItemTableViewCell** - Table View Cell that contains the outlets and functions for the buyer punchlist items

###### **Methods and Calculated Variables**
- `isSubConDisabled` - variable used to check if subcon is disabled
- `isPunchlistEdit` - variable used to check if views and functions related to editing will be enabled
- `isProcess` - variable used to check if views and functions related to processing will be enabled
- `isAdded` - variable used to check if views and functions related to adding will be enabled
- `setup` - function that initializes the values of the textfields
- `didTapRemoveButton` - calls the dynamic `remove` function
- `didTapDuplicateButton` - calls the dynamic `duplicate` function
- `didTapStatusButton` - calls the dynamic `status` function
- `didTapCheckboxButton` - calls the dynamic `checkbox` function
- `changeStatus` - calls the function that handles the changing of status and also calls the `checkbox` function
- `didEndEditing` - handles the function when editing the values of the text fields



##### **PunchlistDetailsViewController** - View that handles the display of punchlist details

###### **Methods and Calculated Variables**
- `isToq` - variable used to check if punchlist details to be displayed is from a toq punchlist or a buyer punchlist
- `didTapKebabButton` - handles the display of the punchlist menu options
- `goToEdit` - navigates to the edit view for the punchlist details
- `goToProcess` - navigates to the process view for the punchlist details upon user confirmation
- `goToCancel` - handles the `cancelPunchlist` function upon user confirmation
- `cancelPunchlist` - calls an endpoint to cancel the punchlist
- `goToDownload` - handles the `downloadPunchlist`function upon user confirmation
- `downloadPunchlist` - calls an endpoint to download the punchlist
- `getPunchlistDetails` - calls an endpoint to get the punchlist details to be displayed
- `getPunchlistItems` - calls an endpoint to get the punchlist items for the selected punchlist
- `initPunchlistDetails` - function that initializes the punchlist details textfields and labels
- `storeAndShare` - function that handles the preview,saving, and sharing of the punchlist from `downloadPunchlist`



##### **PunchlistDetailsMenuViewController** - View that handles the functions for the menu options from the punchlist details view

###### **Methods and Calculated Variables**
- `initMenuView` - handles the initialization of the available menu options depending on the user permissions
- `edit` - handles the dynamic edit option when edit button is selected
- `download` - handles the dynamic download option when download button is selected
- `process` - handles the dynamic process option when process button is selected
- `cancel` - handles the dynamic cancel option when option button is selected



##### **PunchlistDetailsBuyerTableViewCell** - Table View Cell that handles the outlets for the display of the punchlist details items



##### **PunchlistDownloadViewController** - View that handles the functions for downloading punchlists

###### **Methods and Calculated Variables**
- `fromDate` - variable that handles the starting date for downloading punchlists
- `toDate` - variable that handles the ending date for downloading punchlists
- `didTapDownloadButton` - handles the `downloadPunchlist` function
- `didTapCancelButton` - closes the view
- `downloadPunchlist` - calls an endpoint to get the url for the punchlists to be downloaded
- `textfieldShouldBeginEditing` - handles the corresponding funtion for the textfields edited
- `storeAndShare` - function that handles the preview,saving, and sharing of the punchlist from `downloadPunchlist`



##### **ToqPunchlistAddEditViewController** - View that handles the adding and editing of toq punchlists

###### **Methods and Calculated Variables**
- `unitDetails` - variable that contains the punchlist details and initializes the unit details view if is not empty
- `punchlistDetails` - variable that contains the punchlist details and initializes the punchlist details view if is not empty
- `isEdit` - boolean variable that is used to check if view will handle edit punchlist display and functions
- `isProcess` - boolean variable that is used to check if view will handle process punchlist display and functions
- `uneditableFields` - variable that is to check uneditable fields that have their own functions then tapped
- `requiredFields` - variable that is to check for required fields
- `didTapSaveButton` - function that asks for confirmation when making changes to existing punchlists
- `processPunchlist` - calls an endpoint that processes the punchlist
- `saveFields` - calls an endpoint that saves new punchlist or save changes on edited or processed punchlists
- `didTapAddSectionButton` - handles the function that adds a section to the punchlist items
- `getProjects` - calls an endpoint to get projects available for adding and editing punchlists
- `getBuildings` - call an endpoint to get buildings available for adding and editing punchlists
- `loadSearchUnitsV2` - calls an endpoint to get units available for adding and editing punchlists
- `getPunchlistItems` - calls an endpoint to get the punchlist items to be displayed or edited if there are any
- `getPredefinedPunchlistItems` - calls and endpoint for the predefined punchlist items to be used
- `textFieldShouldBeginEditing` - functions that handles the corresponding actions for each the textfields tapped
- `punchlistTableViewCell` - function that handles in saving the changes on the textfields of the punchlist itmes



##### **ToqPunchlistAddEditSectionViewController** - View that handles the adding and editing of toq punchlist items sections

###### **Methods and Calculated Variables**
- `isEdit` - boolean variable that is used to check if view will handle edit punchlist item sections
- `setupFields` - function that initializes the punchlist item sections display
- `didTapAddButton` - function that handles the adding of new punchlist items
- `didTapSaveButton` - function that handles the saving of the newly added punchlist items



##### **ToqPunchlistItemTableViewCell** - Table View Cell that handles the outlets and functions for the toq punchlist items

###### **Methods and Calculated Variables**
- `edit` - dynamic function that handles the edit related actions
- `expand` - dynamic function that handles the expand related actions
- `setup` - initializes the values for the toq punchlist item cell
- `didTapExpandButton` - calls the `expand` function



##### **ToqPunchlistItemEditTableViewCell** - Table View Cell that handles the outlets and functions for the toq punchlist items when expanded

###### **Methods and Calculated Variables**
- `collapse` - dynamic function that handles the collapse related actions
- `status` - dynamic function that handles the status related actions
- `checkbox` - dynamic function that handles the checkbox related actions
- `subConDisabled` - variable used to check if subcon is disabled
- `isPunchlistEdit` - variable used to check if views and functions related to editing will be enabled
- `isProcess` - variable used to check if views and functions related to processing will be enabled
- `isAdded` - variable used to check if views and functions related to adding will be enabled
- `setupReadonly` - initializes that values and views that are enabled/disabled for read only
- `changeStatus` - calls the `status` and `checkbox` functions
- `didTapCheckboxButton` - calls the `checkbox` function
- `didTapCollapseButton` - calls the `collapse` function
- `didTapStatusButton` - calls the `status` function
- `didEndEditing` - handles the function when editing the values of the text fields



##### **CalendarViewController** - View that handles the calendar details and functions

###### **Methods and Calculated Variables**
- `setCellsView` - configures and initializes the layout of the calendar cells
- `setMonthView` - function that sets the current calendar details
- `getUnitTurnoverSchedules` - calls an endpoint to get the unit turnover schedules of the current calendar
- `getUnitTurnoverSchedulesPerDay` - calls an endpoint to get the unit turnover schedules of the selected day in the calendar
- `initCalendar` - initializes the calendar view using the `setCellsView` and `setMonthView` functions
- `didTapExportButton` - navigates to the export calendar view
- `didTapPrevMonthButton` - sets the calendar view to the previous month
- `didTapNextMonthButton` - sets the calendar view to the next month
- `didTapFilterButton` - calls an endpoint to filter the unit turnover schedules
- `shouldAutororate` - overrides the boolean value that disables the rotation of the screen to landscape view
- `extension CalendarViewController` - separate section that contains the helper functions for the calendar details



##### **CalendarCollectionViewCell** - Collection View Cell that handles the outlets and functions for the calendar cells

###### **Methods and Calculated Variables**
- `setup` - function that initializes the layout of the calendar cells
- `didTappedDate` - function that handles the actions when tapping a date
- `setupTodayDate` - initializes the values of the current day in the calendar



##### **ScheduleTableViewCell** - Table View Cell that handles the outlets for the unit turnover schedule cells



##### **CalendarExportViewController** - View that handles the functions for exporting of calendar details

###### **Methods and Calculated Variables**
- `fromDate` - variable that handles the starting date for downloading punchlists
- `toDate` - variable that handles the ending date for downloading punchlists
- `didTappedExportButton` - handles the `filterTurnoverSchedules` function
- `filterTurnoverSchedules` - calls an endpoint to get the url for the filtered unit turnover schedules to be downloaded
- `textfieldShouldBeginEditing` - handles the corresponding funtion for the textfields edited
- `storeAndShare` - function that handles the preview,saving, and sharing of the punchlist from `filterTurnoverSchedules`



##### **TurnoverScheduleDetailsViewController** - View that handles the display of the details of the unit turnover schedules

###### **Methods and Calculated Variables**
- `initLabels` - initializes the labes of the view using the details of the selected unit turnoverschedule
- `didTapOutsideButton` - closes the view



##### **ProjectsViewController** - View that handles the display of list of all available projects

###### **Methods and Calculated Variables**
- `filteredProjects` - array that contains the project objects to be displayed, and the array used for the table view functions
- `getProjects` - calls an endpoint to get all project objects available for display
- `textFieldChanged` - handles the monitoring of the text change for the search bar and calls the appropriate function
- `filterProjects` - function that handles the filtering of the displayed project objects depending on the text in the search bar



##### **ProjectGalleryViewController** - View that handles the display of a more detailed view of the project object information

###### **Methods and Calculated Variables**
- `isPreselling` - a variable that is used to checked if the view will use preselling functionalities
- `updateComplete` - a callback function that is called when update on the project object is done
- `getUnitCount` - calls an endpoint to get the count for the unit count of the project
- `didTapImageButton` - function that is called when the project image is tapped to navigate to the gallery view of the project photos
- `customSegmentValueChanged` - handles the monitoring of the selection between preselling and default photo gallery
- `didTapKebabButton` - handles the navigation to the project edit view
- `setupProjectGallery` - function that is called to setup the initial values of the project gallery view
- `getProjectPhotos` - calls an endpoint to get the default and preselling photo gallery of the selected project
- `didTapProjectPlanButton` - handles the navigation to the project plans options view



##### **ProjectEditViewController** - View that handles the display and functions for the edit view of the selected project object

###### **Methods and Calculated Variables**
- `updateComplete` - a callback function that is called when update on the project object is done
- `setupProjectDetails` - function that is called to setup the initial values of the project edit view
- `updateAdminContactNumber` - calls an endpoint to update the admin contact number of the selected project object



##### **ProjectConstructionProgressViewController** - View that handles the display and functions for the construction progress options of the selected project

###### **Methods and Calculated Variables**
- `getBuildings` - calls an endpoint to get the list of the buildings of the selected project
- `tableView - didSelectRowAt` - table view function that handles the navigation to the selected option available from the view




##### **ProjectConstructionProgressDetailsViewController** - View that handles the display and functions for the general details view of the construction progress of the selected project

###### **Methods and Calculated Variables**
- `completionPercentage` - handles the display of the percent completed of the construction progress
- `setupRestrictions` - function that hides and restricts some of the details and functionality of the view depending on the type of user
- `setupFields` - handles the display of the values of the labels and fields for the construction progress general details
- `getConstructionProgress` - calls an endpoint to get the construction details data
- `didTapOptionsButton` - handles the navigation to the edit view for the project construction progress details



##### **ProjectConstructionProgressEditViewController** - View that handles the display and functions for editing and updating the construction progress general details

###### **Methods and Calculated Variables**
- `editSuccess` - callback function that updates the construction progress general details view after editing
- `didTapSaveButton` - calls the saveConstructionProgress function to start the updating of the construction progress details
- `setupFields` - handles the display of the initial values of the labels and fields for the construction progress general details
- `saveConstructionProgress` - calls an endpoint to update the construction progress general details and call the editSuccess callback function



##### **ProjectMilestonesViewController** - View that handles the display and functions for the milestones options of the selected project

###### **Methods and Calculated Variables**
- `didTapOtionsButton` - handles the display of the edit option and navigation for the project milestone
- `setupFields` - handles the display of the initial values for the lables and fields of the project milestone details
- `setupResttriction` - functions that hides and limits some of the details and functionality of the view depending on the type of user
- `getProjectMilestones` - calls and endpoint to get the project milestones information



##### **ProjectMilestonesEditViewController** - View that handles the display and functions for editing and updating the milestones of the selected project

###### **Methods and Calculated Variables**
- `editSuccess` - callback function that updates the project milestones details view after editing
- `uneditableFields` - function that defines the fields that are uneditable and instead show a specific module when tapped
- `setupFields` - handles the display of the initial values for the lables and fields of the project milestone details
- `saveMilestones` - calls an endpoint to update the project milestones details and call the editSuccess callback function



##### **ProjectBuildingsTableViewCell** - Table view cell that handles the variables for the project building objects used in ProjectConstructionProgressViewController



##### **ProjectTableViewCell** - Table View cell that handles the variables and functions of the project objects used in ProjectsViewController



##### **ProjectPlansViewController** - View that handles the display and navigation to the different Project Plan type lists

###### **Methods and Calculated Variables**
- `didTabBidPlanButton` - handles the navigation to the Bid Plan project plan list
- `didTapFcdPlanButton` - hanldes the navigation to the Fcd Plan project plan list
- `didTapBuildDrawingsButton` - handles the navigation to the As Build Drawings Plan project plan list
- `didTapKeyPlanButton` - handles the navigation to the Key Plan and Unitized Layout Plan project plan list



##### **ProjectPlanListViewController** - View that dynamically handles the display of the selected project plan type list

###### **Methods and Calculated Variables**
- `didTapBackButton` - handles the navigation back to the ProjectPlansViewController or Project Plan list display view if view is in edit view.
- `didTapAddFileButton` - handles the display of the different options to add file for a new project plan item.
- `didTapKebabButton` - handles the display of the edit view for the project plan list
- `setupRestrictions` - restricts the available functions depending on the type of user
- `setupView` - function that handles the setup of the display view
- `setupEdit` - function that handles the setup of the edit view
- `getProjectPlans` - calls an endpoint to get the list of the project plan items of the selected project plan type
- `storeAndShare` - handles the viewing and sharing of the file of the selected project plan item



##### **ProjectPlanAddFileViewController** - View that handles the addition of a new file for a new project plan item

###### **Methods and Calculated Variables**
- `openCamera` - function that handles the addition of a new image using the camera for a new project plan item
- `openGallery` - function that handles the addition of a new image selected from the gallery for a new project plan item
- `openFiles` - function that handlest he addition of a new file selected using a document picker for a new project plan item



##### **EditPlanDescriptionViewController** - View that handles the updating of the selected project plan item

###### **Methods and Calculated Variables**
- `setupProjectPlan` - function that setups the initial display of the fields and labels of the view using the values of the selected project plan item
- `didTapSaveButton` - function that calls an an endpoint that updates the description of the selected project plan item 



##### **ProjectPlanTableViewCell** - Table View cell that handles the variables and functions of the project plan objects used in ProjectPlanListViewController

###### **Methods and Calculated Variables**
- `goToEditDescription` - function that handles the navigation to the edit description view of the selected project plan item
- `openDocumentViewer` - function that handles the display and sharing of the file of the selected project plan item
- `deleteProjectPlan`- function that calls an endpoint to delete the selected project plan item
- `setupView` - function that handles the setup of the display view
- `setupEdit` - function that handles the setup of the edit view



##### **ConstructionReportsListViewController** - View that handles the display and functions for the list of Construction Reports

###### **Methods and Calculated Variables**
- `didTapAddFileButton` - function that handles the display of options for adding a new report
- `getConstructionReports` - calls an endpoint to get the list of construction reports



##### **ConstructionReportTableViewCell** - Table View cell that handles the variables and functions construction report objects in ConstructionReportsListViewController

###### **Methods and Calculated Variables**
- `downloadConstructionReport` - callback function that downloads the construction report
- `deleteConstructionReport` - callback function that deletes the construction report
- `didTapFileButton` - callback function that handles the navigation to the display of the construction report details



##### **ConstructionReportAddFileViewController** - View that handles the different options for adding a new construction report

###### **Methods and Calculated Variables**
- `openCamera` - callback function that handles the selection of new construction file through the camera of the device
- `openGallery` - callback function that handles the selection of new construction file through the gallery of the device
- `openfiles` - callback function that handles the selection of new construction file through the files of the device



##### **ConstructionReportImageViewController** - View that handles the display of the image of the construction report

###### **Methods and Calculated Variables**
- `initImageView` - function that initializes the display of the values for the labels and image of the construction report



##### **ConstructionReportPdfViewController** - View that handles the display of the image of the construction report

###### **Methods and Calculated Variables**
- `initPdfView` - function that initializes the display of the values for the labels and pdf file of the construction report



##### **GenerateReportsViewController** - View that handles the navigation to the types for generating reports at an All Projects level

###### **Methods and Calculated Variables**
- `didTapAccomplishmentReportButton` - function that handles the navigation to generate Accomplishment Reports
- `didTapUnitReportButton` - function that handles the navigation to generate Unit Reports



##### **GenerateAccomplishmentReportViewController** - View that handles the generation of the accomplishment reports

###### **Methods and Calculated Variables**
- `didTapGenerateButton` - function that handles the generation of the downloadable report
- `didTapSelectDeselectButton` - function that selects and deselects all buildings/projects where reports could be generated from
- `getBuildings` - calls an api endpoint to get buildings from the selected project
- `getProjects` - calls an api endpoint to get all available projects to the user
- `checkSelection` - function that checks the current selection of the generate accomplishment report objects



##### **GenerateAccomplishmentReportTableViewCell** - Table View Cell that handles the variables of the Generate Accomplishment Report objects

###### **Methods and Calculated Variables**
- `setupBuildings` - initializes the values of the generate accomplishment report objects



##### **GenerateUnitReportSingleViewController - View that handles the generation of the unit reports at a project level

###### **Methods and Calculated Variables**
- `didTapGenerateButton` - function that handles the generation of the downloadable report
- `didTapSelectDeselectButton` - function that selects and deselects all buildings/projects where reports could be generated from
- `getBuildings` - calls an api endpoint to get buildings from the selected project
- `getProjects` - calls an api endpoint to get all available projects to the user
- `checkSelection` - function that checks the current selection of the generate unit report objects
  


##### **GenerateUnitReportNestedViewController - View that handles the generation of the unit reports at the all projects level

###### **Methods and Calculated Variables**
- `didTapGenerateButton` - function that handles the generation of the downloadable report
- `didTapSelectDeselectButton` - function that selects and deselects all buildings/projects where reports could be generated from
- `getBuildings` - calls an api endpoint to get buildings from the selected project
- `getProjects` - calls an api endpoint to get all available projects to the user
- `checkSelection` - function that checks the current selection of the generate unit report objects



##### **UnitReportTableViewCell** - Table View Cell that handles the variables of the Generate Unit Report objects



##### **UnitReportHeaderTableViewCell** - Table View Cell that handles the variables for the section title of the Generate Unit Report objects



##### **AlertMessageViewController** - Reusable view that displays an alert

###### **Methods and Calculated Variables**
- `initLabels` - function that initializes the labels of the alert view
- `didTapGotItButton` - dismisses the view

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



##### **ConfirmationViewController** - Reusable view that displays a yes and no button

###### **Methods and Calculated Variables**
- `messageText` - dynamic variable that handles the message to be displayed when confirmation view is shown
- `noteText` - dynamic variable that handles the note to be displayed when confirmation view is shown
- `isNoteHidden` - boolean variable that is used to check if noteText should be displayed
- `actionOption` - dynamic function called then the yes button is tapped
- `didTapYesButton` - calls the `actionOption` function
- `didTapNoButton` - closes the confirmation view



### ARCHITECTURE

![alt text](https://github.com/Rogomi/Traxion-ProjectLego-TechDoc/blob/develop/UMS-architecture.png)


