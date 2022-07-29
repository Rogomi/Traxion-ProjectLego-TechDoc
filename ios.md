[Back](README.md)

# Traxion-ProjectLego

## Technical Documentation

### GETTING STARTED



### INSTALLATION AND DEVELOPMENT

In order to start with the development, first, you will need an Apple account for development. It must be under the team Rogomi, Inc. Then, open the .xcworkspace under the repository root directory. If possible, do a pods repo update in order to avoid missing library errors.

### PROGRAMMING LANGUAGE



### MINIMUM VERSION



### APPLICATION ID


### DEBUGGING

We use a few debugging tools to test functionalities.

For the Native App, we use Xcode's debugging console to create breakpoints and test variables, API responses, and identify null objects which sometimes causes the crash.

We also use iOS Simulator in order to test the apps in different screen sizes and iOS Versions.

### THIRD-PARTY LIBRARIES


#### Cocoapods
Most of the third party libraries are installed using CocoaPods. They can be added by searching library names found in https://cocoapods.org/, inserting them in the Podfile and running the pod install command in the Terminal.

#### Swift Package Manager (SPM)
Some of the third party libraries are installed using SPM

##### Important Libraries

### ACTIVITIES AND CONTROLLERS  

#### Core Classes
- **AppDelegate** - manages most of the pre-startup items like Firebase configurations, etc.
  ##### Configured items

#### View Controllers
