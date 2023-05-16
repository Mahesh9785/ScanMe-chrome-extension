# Angular Chrome Extension

## Introduction: 

Chrome extensions provide a great way to enhance the functionality of the Chrome browser and integrate additional features into web applications. This document will guide you through the process of creating a Chrome extension for an Angular app. By following these steps, you'll be able to extend your Angular application's capabilities and offer a seamless user experience within the Chrome browser.

## Prerequisites:
Basic knowledge of Angular development.
Familiarity with HTML, CSS, and JavaScript.
Chrome browser installed on your machine.

## Run Locally

### Step 1: Setting Up Your Project
Create a new directory for your Chrome extension project.
Initialize a new Angular project within the directory using the Angular CLI:

```
ng new chrome-extension-app
```

Change to the project directory and develop your frontend by generating components:
```
cd chrome-extension-app
```
```
ng generate component extension
```
Change your directory for backend and develop a node backend as per your app's requirement.\
For Example-
```
npm init -y
```
Install dependencies
```
npm install express body-parser --save
```
Create a new file named server.js in the root directory of your project.\
Open server.js and import the required modules:
```
const express = require('express');
const bodyParser = require('body-parser');

const app = express();

app.use(bodyParser.json());
app.use(bodyParser.urlencoded({ extended: false }));

app.get('/api/users', (req, res) => {
  // Handle GET request for retrieving users
});

app.post('/api/users', (req, res) => {
  // Handle POST request for creating a new user
});

app.put('/api/users/:id', (req, res) => {
  // Handle PUT request for updating a user
});

app.delete('/api/users/:id', (req, res) => {
  // Handle DELETE request for deleting a user
});

const port = 3000; // Choose the port number for your server

app.listen(port, () => {
  console.log(`Server listening on port ${port}`);
});
```
Run the server

Open the command prompt or terminal and navigate to your project directory.\
Run the following command to start the Node.js server:
```
node server.js
```
### Step 2: Configuring the Manifest File

Create a new file named manifest.json in the src of your project directory.\
Add the following content to the manifest.json file:
```
{
  "manifest_version": 3,
  "name": "Your Extension Name",
  "version": "1.0",
  "description":"Description of your extension",
  "action": {
    "default_popup": "index.html"
  },
  "host_permissions":[
    "http://*/*",
    "https://*/*",
    "*://*/*"
  ],
  "icons": {
    "16": "/assets/logo.png"
  },
  "content_security_policy": {
    "extension_pages":"script-src 'self'; object-src 'self'"
  }
}
```
Place the icon files referenced in the manifest.json file within the src/assets directory of your project.

### Step 3: Modify the following file 
To make your build include manifest.json and run your inline styles if any add the following

angular.json
```
"assets": [
    "src/favicon.ico",
    "src/assets",
    "src/manifest.json"
]
```
(Under configurations object)
```
"optimization": {
    "scripts": true,
    "styles": {
      "minify": true,
      "inlineCritical": false
}
```
### Step 4: Building the Extension

Build the Angular project:
```
ng build
```
### Step 5: Start your Backend
Start your backend to listen to api requests
```
node server.js
```
### Step 6: Loading the Extension in Chrome

Open the Chrome browser and go to chrome://extensions.
Enable the "Developer mode" toggle switch.
Click on "Load unpacked" and select the extension directory from your frontend build (a dist folder with your app named folder)

### Step 7: The Extension is added to your Chrome browser
You can pin the extension if you wish and run it on any website you want, like any ordinary angular app
