# Scaffolding
Clone this repo and use it as a scaffolding for any new React library project. The repo has been configured to work with webpack(ES6 and hot loading enabled).

# Code structure
- **bin/www/** starts the webpack dev server for running the project during development
- **src/js/** should expose the main file for the library. This file will be the entry point for webpack when run in production mode.
- **src/index.js** is the file that will be the entry point for webpack when run in development mode.
- **src/stylesheets** can have SASS style files to be used in the component
- **config.jscs.json** has the JSCS config for the project set to the airbnb standards
- **index.html** is the file that will be loaded by the webpack dev server in development

# Setup
Say the react library to be exposed is in a file **somecomponent.js**
- Clone the repo using `git clone https://github.com/storeo/scaffolding.git`
- Run `npm install`
- Copy **somecomponent.js** into **src/js**
- If there are any associated styles for the library, keep them as SASS files(.scss) in **src/stylesheets**. Import styles in **somecomponent.js** using `import ../stylesheets/<stylefile>`
- For testing your library in development, import the component in **src/index.js** as `import SomeComponent from './js/somecomponent'` 
- Render the results with `ReactDOM.render(<SomeComponent />, document.querySelector("#app-container"))`
- Open **webpack/base.config.js** and replace *<Project Title>* in **WebpackNotifierPlugin** options with the name of your project
- Open **webpack/production.config.js** and replace *'./relative/path/to/libfile/in/src/js'* in entry config with *./src/js/somecomponent.js*
- Edit **package.json** - *name*, *author*, *description*, *repository.url*, *bugs.url*, *dependencies*, *peerDependencies*, *keywords* etc.

# Running
- For development testing, execute `npm run dev` in the project directory. This will start a webpack dev server in port *9000*. `http://localhost:9000` will load the **index.html** file which will in turn load and execute the **src/index.js** file.
- For generating a production build, execute `npm run production` which will compile the **src/js/somecomponent.js** and place it as **dist/index.js**. Once the library is published to the npm registry, when users import the component, the module exposed by this file is what will get imported.

> To change the port on which the dev server is running , use the `PORT=<PORT_NUMBER> npm run dev`