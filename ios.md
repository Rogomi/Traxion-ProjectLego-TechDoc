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



##### **DashboardViewController** - controls the behavior of the user dashboard screen



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


##### **CocAdditionalFilesViewController** - 

###### **Methods and Calculated Variables**
- `setupAdditionalFiles` - initializes the views for the certificate of completion additional files



##### **LegalViewController** - 

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



##### **GeneralUnitDetailsViewController** - 

###### **Methods and Calculated Variables**
- `viewWillAppear`
- `didTapImage`
- `setupFields`
- `didTapAccountDetails`
- `didTapViewDetails`
- `didTapViewUnitPlan`
- `didTapConstructionStatus`
- `didTapLegalDocuments`
- `didTapUnitMilestonesButton`
- `getUnitDetails`
- `initUI`
- `setupRestrictions`
- `getUnitPhotos`
- `initUnitDetails`



##### **AccountDetailsViewController** - 

###### **Methods and Calculated Variables**
- `payments`
- `setupFields`
- `getAccountDetails`
- `initAccountDetails`



##### **UnitPlanViewController** - 

###### **Methods and Calculated Variables**
- `isRevisedSelected`
- `hasUP`
- `hasRUP`
- `refreshData`
- `setupRestrictions`
- `didTapRUPImage`
- `didTapUnitPlanButton`
- `openImagePicker`
- `openPDFPicker`
- `didTapUPEditFileButton`
- `didTapRUPEditFileButton`
- `didTapUpDeleteButton`
- `didTapRupDeleteButton`
- `didTapUpEditDisclaimerButton`
- `didTapRupEditDisclaimerButton`
- `getUnitPlanDetails`
- `initUnitPlanDetails`
- `getDisclaimers`
- `imagePickerController`
- `imagePickerControllerDidCancel`
- `documentPicker`
- `documentPickerWasCancelled`



##### **UnitStatusViewController** - 

###### **Methods and Calculated Variables**
- `didTapEditSaveButton`
- `updateEMI`
- `setupFields`
- `getUnitDetails`



##### **UnitStatusEMIViewController** - View that manages the selection/adding of EMIs for Unit Status

###### **Methods and Calculated Variables**
- `firstChoice` - dynamic function called if the first button is selected
- `secondChoice` - dynamic function called if the second button is selected
- `c` - dynamic function called when the save button is tapped
- `didSelectFirst` - calls the `firstChoice` function
- `didSelectSecond` - calls the `secondChoice` function
- `didTapSaveButton` - saves the text from the input field and calls the `customChoice` function



##### **PdfViewController** - 

###### **Methods and Calculated Variables**
- `initUnitPlanPdf`



##### **UnitPlanEditFileViewController** - 

###### **Methods and Calculated Variables**
- `isRevised`
- `replaceImage`
- `replacePDF`
- `didTapReplaceWithImageButton`
- `didTapReplaceWithPDFButton`



##### **UnitPlanUploadFileViewController** - 

###### **Methods and Calculated Variables**
- `isRevised`
- `uploadSuccess`
- `didTapUploadButton`
- `initDisplay`



##### **DeleteConfirmationViewController** - 

###### **Methods and Calculated Variables**
- `isRevised`
- `deleteSuccess`
- `initLabel`
- `didTapDeleteButton`
- `didTapCancelButton`



##### **SearchResultsViewController** - 

###### **Methods and Calculated Variables**
- `isAdvancedSearch`
- `isLoading`
- `isSalesDepartment`
- `textFieldChanged`
- `numberOfSections`
- `countFiltered`
- `tableView - numberOfRowsInSection`
- `tableView - cellForRowAt`
- `tableView - didSelectRowAt`
- `loadSearchUnitsV2`
- `loadSearchUnitsAdvancedV2`
- `priceToCurrencyFormatter`
- `SearchResultGroup`



##### **GalleryViewController** - 

###### **Methods and Calculated Variables**
- `isUnitPlan`
- `isImageOnly`
- `initFields`
- `setupRestrictions`
- `setupFields`
- `getUnitPhotos`
- `makeDefault`
- `deletePhoto`
- `didTapKebabButton`
- `collectionView`
- `collectionView - numberOfItemsInSection`
- `collectionView - cellForItemAt`
- `collectionView - didSelectItemAt`
- `scrollViewDidEndDecelerating`
- `getDisclaimers`



##### **GalleryOptionsViewController** - Menu screen showing the gallery options

###### **Methods and Calculated Variables**
- `editDisclaimer`
- `addEdit`
- `delete`
- `makeDefault`
- `didTapEditDisclaimerTextButton`
- `didTapMakeDefault`
- `didTapAddEditButton`
- `didTapDeleteButton`



##### **EditDisclaimerViewController** - Manages the editing of disclaimer text

###### **Methods and Calculated Variables**
- `editSuccess` - dynamic function called when saving is successful
- `didTapSaveButton` - calls the endpoint for saving the disclaimer and calls the function `editSuccess` after successfully saving
- `initLabels` - initializes the labels
- `textView - shouldChangeTextIn` - contains a checker for text count



##### **GalleryEditAddPhotoViewController** - 

###### **Methods and Calculated Variables**
- `uploadSuccess`
- `didTapUploadButton`
- `uploadPhotosV2`
- `shouldDismissPhotoPicker`
- `dismissPhotoPicker`
- `photoPickerDidCancel`
- `dismissComplete`
- `didExceedMaximumNumberOfSelection`
- `handleNoAlbumPermissions`
- `handleNoCameraPermissions`
- `askPermissions`
- `setupPhotoPicker`
- `tableView - numberOfRowsInSection`
- `tableView - cellForRowAt`
- `ImageUpload`



##### **GalleryDeleteViewController** - A view that manages the deletion of gallery images

###### **Methods and Calculated Variables**
- `delete` - dynamic function called when the delete button is tapped
- `didTapCancelButton` - closes the view
- `didTapDeleteButton` - calls the delete function



##### **FailedMessageViewController** - A view that displays a failed message

###### **Methods and Calculated Variables**
- `alertTitle` - the title to be displayed in the view
- `alertMessage` - the message to be displayed in the view
- `didTapGotItButton` - is called when the got it button is tapped
- `initLabels` - inits the labels for the view


##### **SearchPulleyViewController** - 

###### **Methods and Calculated Variables**
- `setDrawerPosition`
- `primaryVC`
- `drawerVC`



##### **SearchDrawerViewController** - 

###### **Methods and Calculated Variables**
- `position`
- `setToHalf`
- `selectedField`
- `isSalesDepartment`
- `setupFields`
- `getProjects`
- `getBuildings`
- `getUnitTypes`
- `getReferenceTypes`
- `updateBuildings`
- `textFieldChanged`
- `tableView - numberOfRowsInSection`
- `tableView - cellForRowAt`
- `tableView - didSelectRowAt`
- `PulleyDrawerViewControllerDelegate`



##### **UnitSearchViewController** - 

###### **Methods and Calculated Variables**
- `showFields`
- `didTapProjectsButton`
- `didTapBuildingsButton`
- `didTapSearchButton`
- `setupProjects`
- `setupBuildings`



##### **AdvancedSearchViewController** - 

###### **Methods and Calculated Variables**
- `showFields`
- `isSalesDepartment`
- `didTapProjectsButton`
- `didTapBuildingsButton`
- `didTapUnitTypeButton`
- `didTapProjectClassificationButton`
- `didTapProjectStatusButton`
- `didTapUnitStatusButton`
- `didTapConstructionStatusButton`
- `didTapPunchlistStatus`
- `didTapKeyStatus`
- `didTapViewingStatusButton`
- `didTapTOQPunchlistButton`
- `didTapSearchButton`
- `changeViewsAlpha`
- `setupSalesFields`
- `setupProjects`
- `setupReferences`
- `setupBuildings`
- `RangeSeekSliderDelegate`



##### **ChangePasswordViewController** - 

###### **Methods and Calculated Variables**
- `rules`
- `PasswordRules`
- `newPasswordField - didSet` 
- `newPasswordField - textFieldDidChange`
- `updateReqs`
- `setupRequirements`
- `setupRuleDisplay`
- `PasswordValidator`



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


