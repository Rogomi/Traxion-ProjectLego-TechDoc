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

##### Firebase Platform Libraries.  
**Firebase/Analytics** - Used for App Analytics.  
**Firebase/Crashlytics** - Used to identify causes of crashes from users.  
**Firebase/Performance** - Used to monitor app performance.  

##### UI Libraries
**Compose Coil** - Used for displaying images.  

##### Other Useful Libraries 
**Android Navigation: Kotlin** - Used to manage connections between different screens and layouts.  
**Esperando** - Used to connect shared data between activies.  
**Dagger-Hilt** - Used for easier data management between activities.  
**Karumi/Dexter** - Used to simplify permission requests and access.  

### IMPORTANT CLASSES

#### Activities/Fragments

- **MainActivity** - handles the main activity container which will display all the core.
  ##### Composable/ViewModel Methods

- **SplashScreen** - handles the display for loading the splashscreen for 2 seconds.
  ##### Composable/ViewModel Methods
  - `startSplash()`  

- **LoginScreen** - handles the display where users will input email account and password.
  ##### Composable/ViewModel Methods

 
- **ChangePasswordScreen** - handles the display when the user wants to change password
  ##### Coomposable/ViewModel Methods

  
- **ForgotPasswordScreen** - handles the display of forgot password
  ##### Coomposable/ViewModel Methods
  
  
- **MainDashboardScreen** - handles the display of main dashboard; landing screen after login
  ##### Coomposable/ViewModel Methods
  
  
- **UserProfileScreen** - handles the display of user profile
  ##### Coomposable/ViewModel Methods
  
  
- **PrivacyPolicyScreen** - handles the display of privacy policy
  ##### Coomposable/ViewModel Methods
  
  
- **TermsConditionScreen** - handles the display of terms and conditions
  ##### Coomposable/ViewModel Methods
  


### ARCHITECTURE USED

Project Lego Android follows and uses the Model-View-ViewModel Architecture (MVVM). It consists of an xml file which is the UI layout definition for the screen, a Fragment that is the UI controller that displays the data, and the ViewModel, a class that prepares the data for viewing in the Fragment and reacts to user interactions.

![alt text](https://drive.google.com/file/d/1ikD6dEHvLZIGkIyTN_1Zs-iRh_RnZbgy/view?usp=sharing)

![alt text](https://github.com/Rogomi/Traxion-ProjectLego-TechDoc/blob/develop/UMS-architecture.png)

