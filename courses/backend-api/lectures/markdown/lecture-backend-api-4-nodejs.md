### 4.Backend APIs
#### Node.js

---
### What is Node.js

* Node.js is a free open source server environment.
* An open source runtime environment.
* Makes it possible to execute javascript outside the browser.
* Node.js runs on various platforms (Windows, Linux, Unix, Mac OS X, etc.)
* Node.js use the v8 engine (same as chrome).
* Node compiles JavaScript code into native code.

---
#### Node.js
* Is often used to build backend services called APIs.
* Can also be used a middlewares to handle requests from different systems.

---
#### Node.js
* Good for I/O intensive tasks (such as sending http requests)
* Non Blocking IO
* Single Threaded
* <a href="https://www.youtube.com/watch?v=jOupHNvDIq8" target="_blank">Mosh Explains</a>
* Has a package manager too, npm

---
#### Try it
Run in terminal
```Shell
$ node -v
$ npm -v
$ npm install npm@latest -g
```

---
#### Node package manager (npm)
Package manager (just like brew/chocolatey) and dependency manager
* Install locally `npm install --save` in current project
* Install globally `npm install -g` for all users
* Node and npm are npm packages
  * `npm install -g node`
  * `npm install -g npm`

---

#### Package.json
Specifies dependencies for a project
* adds dependency files to `node_modules`
	* `node_modules` should be ignored by git
	* need to run `npm install` after clone
* npm `install --save mongoose`
  * Adds to package.json
  * installs to node_modules

---

#### Package.json
is a plain json file
```json
{
  "name": "lectures-exercises",
  "main": "index.js",
  "dependencies": {
    "express": "^4.16.4"
  },
  "devDependencies": {
    "nodemon": "^2.1.48"
  },
  "scripts": {
    "start": "node index.js",
    "develop": "nodemon index.js"
  },
}
```

---
#### Using dependencies
* import dependencies using
  * `const express = import("express");`
  * `const express = require("express");`

---
#### Node

* Create an index.js file.
* Add some javascript code that logs something.

```Shell
$ node index.js
```

---

#### Modules
* Small units of independent, encapsulated, reusable code.
* A module is just a file. One script is one module.
* Modules can:
	* Load each other
	* Call functions of one module from another one:

---
#### Node modules

* Can import stuff from each other.
* Need to be exported to be imported.

lib.js
```JavaScript
module.exports = 10;
```

main.js
```JavaScript
const someValue = require('./lib');
console.log(someValue); // 10
```

---
#### Node modules

lib.js
```JavaScript
const first = 1;
const second = 2;
module.exports.firstValue = first;
module.exports.secondValue = second;
```

main.js
```JavaScript
const {firstValue, secondValue} = require('./lib');
console.log(firstValue); // 1
console.log(secondValue); // 1
```

---


#### Node modules

lib.js
```JavaScript
const first = 1;
const second = 2;
module.exports = {
	firstValue: first,
	secondValue: second
}:
```

main.js
```JavaScript
const {firstValue, secondValue} = require('./lib');
console.log(firstValue); // 1
console.log(secondValue); // 1
```


---

#### Node modules

lib.js
```JavaScript
const sayHello = ()=>{
	console.log('Hello world!');
}

const sayBye = ()=>{
	console.log('Bye Bye!');
}

module.exports = {
	sayHello
};
```

main.js
```JavaScript
const { sayHello } = require('./lib');

sayHello(); // Hello world!
```


---

#### Node modules

lib.js
```JavaScript
const sayHello = ()=>{
	console.log('Hello world!');
}

const sayBye = ()=>{
	console.log('Bye Bye!');
}

module.exports = {
	sayHello
};
```

main.js
```JavaScript
const { sayHello, sayBye } = require('./lib');

sayHello(); // Hello world!
sayBye(); // TypeError: sayBye is not a function
```


---
#### Globals

* Since we do not run Node in the browser we don't have a window object.
* However Node also provides global objects called globals.
* <a href="https://nodejs.org/api/globals.html" target="_blank">Content of the global object</a>

index.js
```JavaScript
console.log(global);
```

Shell
```Shell
$ node index.js
```

---
#### Process

* The process object is a global that provides information about, and control over, the current Node.js process.
* Since it's a global it is always available to Node.js applications without using require().

index.js
```JavaScript
console.log(process);
```

---
#### Command line arguments

index.js
```JavaScript
console.log('Arguments', process.argv);
```

Shell
```Shell
$ node index.js hello world
```

Logs
```Shell
Arguments [
	'/Users/nisse/.nvm/versions/node/v12.14.0/bin/node',
	'/Users/nisse/Desktop/node_course/playground/index.js',
	'hello',
	'world'
]
```

---
#### Command line arguments

```Shell
npm i yargs
```

index.js
```JavaScript
const argv = require('yargs').argv
		
console.log(argv);
```

Shell
```Shell
$ node index.js --phrase=hello
```

---
#### Reading from file

* fs = <a href="https://nodejs.org/api/fs.html" target="_blank">File System</a>

index.js
```JavaScript
const fs = require('fs');

const dataBuffer = fs.readFileSync('1-json.json');
const dataJSON = dataBuffer.toString();

const data = JSON.parse(dataJSON);

console.log(dataJSON); // { name: 'nisse' }
console.log(data.name); // nisse
```

info.json
```JSON
{
	"name": "nisse"
}
```

---
#### Write to file

index.js
```JavaScript
const fs = require('fs');

fs.writeFile('message.txt', 'Hello Node.js', 'utf8', ()=>{console.log('done')});
```

message.txt
```
Hello Node.js
```

---
#### JavaScript versions
"Node.js is built against modern versions of V8. By keeping up-to-date with the latest releases of this engine, we ensure new features from the JavaScript ECMA-262 specification are brought to Node.js developers in a timely manner, as well as continued performance and stability improvements." - <a href="https://nodejs.org/en/docs/es6/" target="_blank">Node.js docs</a>

---
#### Node.js provides a lot of functionality that we will use during the course.