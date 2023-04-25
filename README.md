## About
- This is a single-page app, mobile first and responsive
- This is a test and learn javascript with the intent on mastering react
- Run `node nodePractice.js` in terminal.
- Open with live-server `jsPractice.html` via right-click

## Issues
- `npm install -g json-server` globally so we can access `empdb.json` via `http://localhost:3000/employees` and json-server
- `npm install axios`, beginning of react




## Notes
- If you want to set environment variables via .bashrc
    - `alias create-react-app=~/AppData/Roaming/npm/create-react-app.cmd `
    - `alias json-server=~/AppData/Roaming/npm/json-server.cmd`




## Concepts Part 1
- JS originally only ran in browsers.
- Browsers are mandated to ALLOW event listeners for events.
- Everytime an html page was rendered in a window, the window has an instance of JS running. this executing JS instance could be asked to manipulate the DOM.
    - DOM is an OP representation of the view that is rendered by the browser.
    - DOM has element tree => "inspect" any browser window.
- Every html element is like an object and each has properties/fields/instanceVars like "style", "id", "src", "rowspan".
- DOM tree => elements inside elemtns nested to whatever level.
- JS is able to manipulate the DOM => changing the view displayed in the window
    - add elements, remove elements, modify elements, change properties of elements
- JS implements "interactivity" with the user or with timers/timeout => events and event listeners
    - Events are happenings such as clicking/hovering/typing/long press a button/focusOn (clicking into)/drag.
    - Event listeners => functions that have code that runs when a specific thing happen
- `script` tag in html is used to include JS code to run wherever in the HTML it is found.
- When JS instance starts running in the browser window, there are global vars available:
    - `window` => browser window object
    - `document` => entire html document object

## Concepts Part 2
- Frameworks like React and Angular use JS to efficiently manage views in our frontend. 
- The browser loads the page only once in the beginning, then all the view changes that happen are through JS => Single Page Application (SPA). 
- Browsers do fetch http requests but do not render directly.
    - Node.js is the JS interpreter that was made available for OS like Mac, Windows, Linux, etc.
    - With node.js we were able to run JS code outside the browsers. 
    - Node.js is a JS interpreter/runtime. It is dynamically typed language.
        - types are checked at runtime and can change at runtime
        - there is no compile time since node.js can directly interpret (run) the code.
    - JS code does not need to declare types like Java. => type can keep changing while the code runs. => `return(<p>hello world</p>)`
- Run JS code using node.js in the terminal => `node filename.js`
- Angular and React projects: we write code on our computer, but the app actually runs in the browser through `script` tag in some HTML file. The apps do not execute on our computers. 
- We need to pack our JS code into a JS file bundle and include it in a `script` tag somewhere.
- Webpack is one of the most popular tools to pack js applications that are written on a computer but run in browsers. Packing is generally done automatically.

## Concepts Part 3: Node Package Manager
- a node.js package manager/build tool
- main purpose of npm is dependency (other people's code used in our project) and project management (like maven in Java)
- Node projects look for dependencies in `node_modules` folder, and then in parents folder's `node_modules`, parent's parent's and so on.
- Npm commands:
    - `npm install` => looks at a file called **package.json** (like pom file in Maven projects) in the current folder and downloads all dependencies in the node_modules folder
    - `npm install <dependencyName>` installs that dependency and also adds a line in the package.json for adding that dependency
    - `npm install -g <dependencyName>` => adding the `g` tag means instally globally, all projects will have access AND is installed somewhere else instead of `node_modules` => typically done for util programs like `ng` or `create-react-app`.
- lots of other commands => `npm start`, `npm build` or `npm init`

## Concepts Part 4: JavaScript Rules and Syntax
- `let` or `const` is used to create variables
- arrays are dynamic like ArrayLists are in java
- Arrow function in JS looks like lambda in Java
- arrow is equals followed by greater than symbols
- no types of specified in JS
- objects in JS are created as "key-value" pairs. Key are instance var names and values are the values of the inistance vars
- spread operator to create copies of objects and arrays. 
    - Syntax is 3 dots followed by the arrayName/ObjectName => spread key-value pairs or arrayElements into wherever this spread op is used
    - using spread operator for objects can override fields. to remove any field, override its value to "null"
- arrays/objects should be copied instead of modifying them due to immutability nature
- Functional Programming => using pure functions (without side effects) in code and passing and returning other functions; immutability is central in functional programming
- Pure Function => anything that a code does that affects computer input/output or network etc. (e.g. printing on the console or in a log file; loggin/access API over the network)
- JS is a single threaded langrage. It will never create separate threads. It will never wait for things.
- If any operation involves any sort of delays/waiting => those are done by JS "job handler" and the only thing our code can do: 
    - provide a callback function to run when the delays/waiting is completed => ASYNC PROGRAMMING
    - JS can provide args to the callback function as well => typically a value that is resolved after waiting operation:
        - calling an API
        - connecting to DB
- promises are a way to do this async programming in a manageable way => easy to understand and manage
    - promise contain config info on what will happen if `thatObject.then()` is executed. typically a value is returned after some delay. Can do chaining operations.
    - code structure: 
```
        somePromise.then(value => {do sth with value returned by promise after whatever time})
            .catch(error => {do sth with error object returned by the promise});
        let someTimieout = setTimeout(fnToExecute, timeoutToExecuteTheFnAfter);
        let someInterval = setnterval(fnToExecute, intervalAtWhichToExecuteRepeatedly);
```