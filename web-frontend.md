[Back](README.md)

# Project LEGO Web Frontend

## Technical Documentation

### GETTING STARTED

Project LEGO Web Frontend was created using the Vue.js JavaScript framework. It makes use of different JavaScript libraries that allow the app to function and be developed in a structured manner. The frontend utilizes the Apollo GraphQL client and the Axios HTTP client to communicate with the external API. It also uses Tailwind CSS for styling.

### INSTALLATION AND DEVELOPMENT

The user must first install the [Node.js](https://nodejs.org/en/) runtime environment for development, building, and deployment. Installation of this includes the [Node Package Manager (NPM)](https://www.npmjs.com/), which helps install external libraries needed for the app to function.

This project was created with **Node.js version 16.16.0**.

The Vue.js 3 framework was used for this project, and a guide for it can be found [here](https://vuejs.org/guide/introduction.html#what-is-vue). The app uses the Options API.

Lastly, the user must have a text editor. The developers suggest [Visual Studio Code](https://code.visualstudio.com/) with the following extensions:

[Vue Language Features (Volar)](https://marketplace.visualstudio.com/items?itemName=Vue.volar) - Language support for Vue 3  
[Apollo GraphQL](https://marketplace.visualstudio.com/items?itemName=apollographql.vscode-apollo) - Rich editor support for GraphQL client and server development that seamlessly integrates with the Apollo platform  
[Tailwind CSS IntelliSense](https://marketplace.visualstudio.com/items?itemName=bradlc.vscode-tailwindcss) - Intelligent Tailwind CSS tooling for VS Code.

### UPDATING DATA DUMP

The user must first upload the new files into this folder: __*/home/v-traxion/Traxion-ProjectLego-API/files*__

The user must follow these file names depending on what they want to update:
 - **Contract.csv**
 - **ProjectList.csv**

After uploading the files the user needs to update it either manually or scheduled in the web CMS. 

For Manual, press the Update button.

For Scheduled, input a time following the same format and press the Save button.

Flow: Web Portal > System Menu > Update Data Dump / Update Data Dump Sched
![alt text](https://github.com/Rogomi/Traxion-ProjectLego-TechDoc/blob/develop/DataDump.png)



### PROGRAMMING LANGUAGE

Project LEGO Web uses JavaScript for development.

With it being a web application, it uses HTML for markup and CSS for styling.

### DEBUGGING

The developers use the corresponding developer tools for [Chrome](https://developer.chrome.com/docs/devtools/), [Firefox](https://firefox-dev.tools/), and [Safari](https://developer.apple.com/safari/tools/) respectively, together with the [Vue.js Devtools](https://devtools.vuejs.org/). 

### UI LIBRARIES

[**Tailwind CSS**](https://tailwindcss.com/) - A utility first CSS framework that can be composed to build any design, directly in your markup.  
[**Vue Toaster**](https://github.com/MeForma/vue-toaster) - Custom Utility CSS that allows an easy and simple toast message for Vue.  
[**Vue Datepicker**](https://vue3datepicker.com/) - Powerful, lightweight, and reusable datepicker component to fit within any project.

### IMPORTANT CLASSES

#### Initialization Classes
- **main.js** - Handles the initialization of Vue components. Also contains initial navigation of the pages.

#### Screens
- **LoginPage.vue** - Page that contains forms related to user login. 
    ##### Data/Methods
    - `isCredInvalid` - Flag for displaying error message.
    - `message` - Error message to be displayed.
    - `isHeightBig` - Flag for window sizing.
    - `getMessage()` - Get error message from form to display.
    - `onResize()` - Account for window sizing.
    ##### Components
    - `LoginForm` - Form with textfields to handle user login.  

- **MainPage.vue** - Container where most other screens are rendered. 
    ##### Data/Methods
    - `isFirstLoginModalVisible` - Flag for displaying modal on user's first login.
    - `isLogoutModalVisible` - Flag for displaying logout confirmation modal.
    - `id` - Currently logged in user's ID.
    - `firstName` - Currently logged in user's first name.
    - `lastName` - Currently logged in user's last name.
    - `role` - Currently logged in user's role.
    - `profilePicture` - Currently logged in user's profile picture URL.
    - `confirmLogout()` - Show logout modal.
    - `cancelLogout()` - Hide logout modal.
    ##### Components
    - `TopBar` - Top bar that persists throughout the app. Contains logo and user info.
    - `SideBar` - Side bar that persists throughout the app. Contains sections that can be navigated.
    - `MainPageFirstLoginModal` - Modal shown to user during first login.
    - `LogoutModal` - Modal shown to user attempting to logout.  

- **UserProfile.vue** - Page that contains user information and allows changing of passwords. 
    ##### Data/Methods
    - `change_password_clicked` - Flag for checking if password form is editable.
    - `password_match` - Flag for checking if input passwords match.
    - `old_password` - User's old password.
    - `new_password` - User's new password.
    - `confirm_password` - Confirmation of user's new password.
    - `firstName` - Currently logged in user's first name.
    - `lastName` - Currently logged in user's last name.
    - `role` - Currently logged in user's role.
    - `position` - Currently logged in user's position.
    - `department` - Currently logged in user's department.
    - `user_id` - Currently logged in user's ID.
    - `email` - Currently logged in user's email address.
    - `projects` - List of currently logged in user's projects.
    - `filteredPasswordParameters()` - **Computed property.** Returns a list of checkers/parameters required for new passwords.
    - `checkPassword()` - Check if new password passes specified constraints and return API response.
    - `toggleTextVisibility()` - Toggle password text field obfuscation.
    - `cancelChangePassword()` - Reloads the page and cancels password changing.
    ##### Components
    - `UserProfilePasswordField` - Text field with obfuscation toggle for passwords.  

- **UserList.vue** - Page that displays existing users and allows for creation/editing. 
    ##### Data/Methods
    - `departments` - List of all available departments.
    - `departmentOptions` - List of selectable departments for filtering purposes.
    - `users` - List of users to be displayed.
    - `query` - Query for user filtering.
    - `showAddUserForm` - Flag for display of form to add a new user.
    - `isConfirmingReactivate` - Flag for display of confirmation modal for user reactivation.
    - `isConfirmingDeactivate` - Flag for display of confirmation modal for user deactivation.
    - `currentUser` - User currently selected for reactivation/deactivation.
    - `isShowEditUserForm` - Flag for display of form to edit an existing user.
    - `selectedEdituser` - User currently selected for editing.
    - `pageOfItems` - List of users visible in the currently viewed page.
    - `selectedDepartmentIds()` - **Computed property.** Returns a list of selected departments from the filter.
    - `changePage()` - Change the currently viewed page.
    - `showModal()` - Show reactivation/deactivation confirmation modal.
    - `addedANewUser()` - Close the "add user" form and refresh the page.
    - `showEditUserForm()` - Show form for editing an existing user.
    - `editAUser()` - Close the "edit user" form and refresh the page.
    - `toggleUserActivationStatus()` - Reactivate/deactivate a user.
    ##### Components
    - `UserListDropdown` - Dropdown for department filters.
    - `AddUserForm` - Form for adding users.
    - `UserListDeactivateModal` - Modal to confirm user deactivation.
    - `UserListReactivateModal` - Modal to confirm user reactivation.
    - `EditUserForm` - Form for editing users.
    - `Pagination` - Handler of pagination for users.  

- **UserLogs.vue** - Page that contains user activity logs. 
    ##### Data/Methods
    - `audits` - List of logs to be displayed.
    - `logModules` - List of selectable modules.
    - `fromDate` - Start date for log filtering.
    - `toDate` - End date for log filtering.
    - `isLoading` - Flag for loading data.
    - `pageOfItems` - List of logs visible in the currently viewed page.
    - `hasQueried` - Flag for determining if user has attempted to query a filter.
    - `formattedFromDate()` - **Computed property.** Returns a GraphQL-formatted date String if given a valid "from date", or an empty string if not. 
    - `formattedToDate()` - **Computed property.** Returns a GraphQL-formatted date String if given a valid "to date", or an empty string if not. 
    - `changePage()` - Change the currently viewed page.
    - `generateLogs()` - Query the API for logs that fit the provided date filter and selected module.
    - `formatDate()` - Format a date to `MM-dd-yyyy hh:mm aa`.
    - `convertDigits()` - Used in `formatDate()` to add 0s before 1-digit entries.
    - `queryFormatDate()` - Formats a date for GraphQL queries. Used in computed properties.
    - `selectLogModule()` - Selects a module.
    ##### Components
    - `DatePicker` - Vue Datepicker component for date selection.
    - `Pagination` - Handler of pagination for logs.  

- **AccessManagement.vue** - Page that contains available departments and allows for creation/editing. 
    ##### Data/Methods
    - `isDepartmentList` - Flag for showing list of departments.
    - `isAddDepartment` - Flag for showing form for adding departments.
    - `isEditDepartment` - Flag for showing form for editing departments.
    - `showUnitDetailsForm` - Flag for showing form of unit details.
    - `isRequired` - Flag for showing error message if required fields are not filled.
    - `selectedDepartment` - Currently selected department.
    - `selectedModule` - Currently selected module.
    - `selectedDepartmentDetails` - Currently selected department details.
    - `moduleGroups` - List of module groups.
    - `departments` - List of all available departments.
    - `departmentName` - Name of currently selected department.
    - `parentModules()` - **Computed property.** Returns list of parent modules.
    - `subModules()` - **Computed property.** Returns list of submodules.
    - `addDepartment()` - Initialize list of departments. 
    - `initModuleGroup()` - Initialize list of module groups.
    - `getTypes()` - Create a string of types based on a given array.
    - `initEditDepartment()` - Initialize form for editing departments.
    - `getSubmodule()` - Returns a list of submodules based on the provided parent ID.
    - `showEditModuleForm()` - Display form for editing a module.
    - `saveDetails()` - Save changes made related to access types.
    - `updateDepartmentName()` - Update shown department name.
    - `addNewDepartment()` - Create a new department.
    ##### Components
    - `UnitDetailsForm` - Form to display unit details.  

- **ContentManagement.vue** - Page that contains the site's privacy policy (PP) and terms and conditions (T&C). Allows for editing. 
    ##### Data/Methods
    - `type` - Determines which article (PP/T&C) should be displayed.
    ##### Components
    - `TopTabs` - Tabs to switch articles.
    - `ArticleByType` - Text box that can be toggled to be editable or not.

  - **ProjectManagement.vue** - Page that contains customization settings for projects. 
    ##### Data/Methods
    - `tabs` - Content tabs to be displayed.
    ##### Components
    - `Settings` - Tab that allows editing of booking limits.

- **DataDump.vue** - Page that contains settings and options related to data dumps and logs.
   ##### Data/Methods
   - `updateDataDump()` - Trigger a script that updates updates the database with the data dump file.
   - `updateCronSchedule()` - Schedule a daily cron job that updates the database with a data dump file.
   - `downloadDataDumpLogs()` - Download a single log file detailing data dump log outputs from the server.
   - `formatDate()` - Format user input date for cron schedule processing.
   - `convertDigits()` - Add 0s before 1-digit time values (e.g. '1' to '01').
   - `queryFormatDate()` - Format date for GraphQL query.
   - `formattedFromDate()` - **Computed property.** Checks if "From Date" has a value and calls `queryFormatDate()` to format.
   - `formattedToDate()` - **Computed property.** Checks if "To Date" has a value and calls `queryFormatDate()` to format.

### ARCHITECTURE USED

Vue.JS has its own architecture. Kindly refer to this [link](https://vuex.vuejs.org/guide/structure.html).

#### API ARCHITECTURE
![alt text](https://github.com/Rogomi/Traxion-ProjectLego-TechDoc/blob/develop/UMS-architecture-web.png)

#### OVERALL ARCHITECTURE
![alt text](https://github.com/Rogomi/Traxion-ProjectLego-TechDoc/blob/develop/UMS-architecture-overall.png)
