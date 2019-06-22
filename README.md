# Install-Guides
Just a place to save some instructions from class on installs/setups for projects

# React Install (Bootstrap/Firebase/scss/eslint(airbnb))
### Features
* REACT with JSX
* ES6+ (all the es6 stuff we love writing with)
* Autoprefixes CSS (no need to add in all the -webkit stuff)
* Unit test runner (Jest is already installed and configured)
* Live development server (make some changes and the app automatically reloads)
* Build scripts to bundle all the things (JS, CSS, images, and sourcemaps)
* Offline service works (you can technically do development offline)
* Hassle free updates (if a new version of create-react-app comes out you just update the version in the package.json file)
---
### Step By Step
##### Github Stuff
* In gitbash type ` npx create-react-app name-of-directory ` @ the local location you want the project
* Create github project (name it the same as local dir for your sanity)
* Copy SSH info from github
* in gitbash/terminal `npm remote add origin <SSH INFO HERE>`
* `git checkout -b setup`
---
##### Organizing files
* Create a folder in "src" named "App" (cap is required!)
* Move `app.css`, `app.js`, and `logo.svg` to the App folder
* Delete `App.test.js`, and the "test" script from `package.json`
* Make a folder named "styles" in "src" (no caps in this one)
* Rename `index.css` to `index.scss`, and move it to the "styles" folder
* Change the import statement inside "index.js" to `import './styles/index.scss';` (don't forget to save!)
* create a file named `_variables.scss` inside thr "styles" folder (use it to create a variable that can be used to change the background color in index.scss)
* On the termindal inside your project type `npm install node-sass --save-dev` to allow your project to use scss instead of css (your scss should now work)

* **Your directory should look like this:**


![alt text][example]

[example]: https://raw.githubusercontent.com/nss-nightclass-projects/Night-Class-Resources/master/book-4-react/images/setup_scss.png "Directory Example"

---
##### Adding eslint
* install the VS Code plugin eslint [here](https://marketplace.visualstudio.com/items?itemName=dbaeumer.vscode-eslint)
* create a file named `.eslintrc` in the root of your project (not in src!)
* Add the following to the `.eslintrc` file. (don't forget to save!)
```
{
  "parserOptions": {
    "ecmaVersion": 6,
    "sourceType": "module"
  },
  "extends": ["airbnb-base", "react-app"],
  "globals": {
    "document": true,
    "window": true,
    "allowTemplateLiterals": true
  },
  "rules": {
    "no-console": [1, { "allow": ["error"] }],
    "no-debugger": 1,
    "class-methods-use-this": 0,
    "linebreak-style": 0 
  }
}
```
* Install airbnb styles by typing the following into the terminal on your project `npm install eslint-config-airbnb-base --save-dev`
---
##### Adding Bootstrap
* type the following into the terminal on your project `npm install bootstrap --save`
* import bootstrap in `app.js` by adding the following `import 'bootstrap/dist/css/bootstrap.min.css';`
* Add a test button to `app.js` inside the render space `<button className='btn btn-danger'>HELP ME</button>`
* Bootstrap should now work
---
##### Adding Firebase
* Type the following into the terminal on your project `npm install firebase --save`
---
##### Finalizing
* Add, and commit changes from your project once everything is working
* Push the commit to github, and merge
* Install the React Developer Tools extension for Chrome [here](https://chrome.google.com/webstore/detail/react-developer-tools/fmkadmapgofadopljbjfkapdkoienihi?hl=en)
* You can access these tools in the dev tools top bar, but only when viewing a website which uses React
### You are ready to start coding!
---
---
# Firebase Realtime Databse Install
* Make Project @ firebase
* @ firebase enable gmail login (authentication -> Sign in method -> gmail -> enable)
* go to project settings -> click the html icon (`</>`)
* back in the local project's console enter `npm install --save firebase`
* make a file named `apiKeys.json`, @ `src/javascripts/helpers`
* copy the part of the firebase info given on firebase with "apikey, authDomain, etc", and convert this into json data.
    * **IMPORTANT** YOU MUST ADD THIS FILE TO `.gitignore`, and import when needed
``` JSON
{
  "firebaseKeys": {
    "apiKey": "sorryNotARealApiKey",
    "authDomain": "example.firebaseapp.com",
    "databaseURL": "https://example.firebaseio.com",
    "projectId": "example-123456789",
    "storageBucket": "example-666.google.com",
    "messagingSenderId": "123456789",
    "appId": "123456789"
  }
}
```
* (Add a file named `apiKeys.example.json` with empty values for reference.)

* inside `auth.js`, and `main.js`, on top of the file `import firebase from 'firebase/app';`, and `import 'firebase/auth';`
* in `auth.js` make a new function named `signMeIn()` which will call a popup window to log into google when called
```
const signMeIn = () => {
  const provider = new firebase.auth.GoogleAuthProvider();
  firebase.auth().signInWithPopup(provider);
};
```
* add an event listener that calls `signMeIn()`  when your login button is clicked
* export if needed
* Inside `main.js`,  `import apiKeys from './helpers/apiKeys.json';`
* inside your init function call `firebase.initializeApp(apiKeys.firebaseKeys);`

* You will now get a popup box when the login button is clicked, but when you log in the browser throws an error. If you follow that link, and use your email address as the customer support email, and accept you should be able to log in successfully.
