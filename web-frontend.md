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

#### Components
- **LoginPage.vue** - Container that handles forms related to user login.
- **LoginForm.vue** - Handles the user login.
- **ForgotPasswordForm.vue** - Handles the forgot password function.
- **ChangePassword.vue** - Handles the reset password function.
- **UserList.vue** - Handles the display of different users of Project LEGO.

### ARCHITECTURE USED

Vue.JS has its own architecture. Kindly refer to this [link](https://vuex.vuejs.org/guide/structure.html).

![alt text](https://github.com/Rogomi/Traxion-ProjectLego-TechDoc/blob/develop/UMS-architecture.png)
