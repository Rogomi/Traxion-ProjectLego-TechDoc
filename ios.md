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
