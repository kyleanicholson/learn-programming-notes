### Install Prerequisites
Before starting a new react project you first need to install Node and NPM. These are used to manage libraries. 

In Linux you can install node with the following command
```bash
sudo apt install nodejs
```

Once installed you can verify checking the installed version with:
```bash
node --version
```

To install NPM, use the following commands:

```bash
sudo apt install npm  
npm -v or npm –version
```

### Set up React Project

We will use Vite to set up the react application. Vite is a modern build tool for status quo web frameworks which comes with sensible defaults while remaining extensible for specific use cases.

After navigating to the folder you want to create your React project, type the following command:

```bash
npm create vite@latest <project name> -- --template react
```

Then:
```bash
cd <project directory
npm install
npm run dev
```

Now you have a project skeleton which should resemble the following (overall structure)

```code
.
├── index.html
├── node_modules
├── package.json
├── package-lock.json
├── public
├── README.md
├── src
└── vite.config.js
```

A brief explanation of some of the important files in the project skeleton:
* **src**: Most of what we need lives here.
	* **src/App.jsx**: File which is used to implement React components. React components can be split into multiple files where each file maintains one or more components on its own.
	* **src/main.jsx**: The main or entry component that initializes and renders the overall structure or layout of your app.
	* 
* **package.json**: All third-party dependencies and other essential project configurations related to Node/npm. 
	* Project-specific commands also live here (more on this below)
* **package-lock.json**: Indicates to npm how to break down all node package ersion and their internal third party dependencies (do not change)
* **node_modules**: Contains installed node packages - Vite includes various node packages by default (should not change)
* .**gitignore**: Contains a list of folders and files that should not be added to git repository. When using git, these files and folders should be located only on your local machine and will not be included in git pushes/commits.
* **vite.config.js**: Configuration for Vite 
* **public**: Holds static assets for the project like a favicon (used for the browser's thumbnail )
* **index.html:** The HTML displayed in the browser when starting the project. Script tag in this file links to the source folder where react code is located to output HTML/CSS to the browser.

***npm Scripts***

As mentioned above, project specific commands live in the **package.json** file. Here is what the scripts property of the package.json file contains for my example application:
```json
"scripts": {

"dev": "vite",

"build": "vite build",

"lint": "eslint . --ext js,jsx --report-unused-disable-directives --max-warnings 0",

"preview": "vite preview"

},
```

These scripts can be run with the `npm run <script>` command in the command line:

```bash
# Run the application locally
npm run dev

# Build the application for production
npm run build

# Run production ready build on local machine (after npm run build)
npm run preview

```

Run `npm run dev`. If there are no errors you should see a screen similar to the following:
```bash
  VITE v4.4.7  ready in 386 ms

  ➜  Local:   http://localhost:5173/
  ➜  Network: use --host to expose
  ➜  press h to show help

```

Open the Local link in the browser and you should see something like this if everything worked correctly:
![[Pasted image 20230729185317.png]]

Congrats! You now have a React app up and running!

You can terminate the app from the command line with `ctrl+c`:

Next, run the `npm run build` script and verify that a **dist/** folder was added to your project. This will be used later on to deploy your application.

Then you can run `npm run preview` to see the production ready application in the browser.
