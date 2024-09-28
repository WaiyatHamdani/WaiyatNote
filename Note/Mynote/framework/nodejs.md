### Node.js Notes


## Table of Contents
-[Checking Node.js Version](#checking-nodejs-version)
-[Introduction to Global Objects](#introduction-to-global-objects)
-[Node Modules](#node-modules)
-[File Management and Streams](#file-management-and-streams)


## Checking Node.js Version
To check if you have Node.js installed, open your terminal and run the following command:
- To check if you have Node.js installed, open your terminal and run the following command:
```bash
node -v
```
- If Node.js is not installed, go to nodejs.org and download the LTS version.







## Introduction to Global Objects
1) You can drag the filename of a script into your terminal and start it using:
```bash
node filename.js
```
2) More on Global Objects
- __filename: Provides the full path of the file currently being executed.
- __dirname: Provides the directory name of the current module's location.
- Global Elements: Node.js offers many global variables, like console, process, Buffer, etc., which are accessible anywhere without needing to require them.

3) Process Object
- The process object provides information about, and control over, the current Node.js process.
- Expected output: Running process in Node.js will display the details of the current process (e.g., environment variables, arguments passed, etc.).
- You can handle arguments using process.argv. For example:
```javascript
console.log(process.argv);
```
4) Standard Input and Output
- Standard Input (stdin) is used to receive input from the user.
- Standard Output (stdout) is used to print output to the console.
```javascript
process.stdin.on('data', data => {
    console.log(`You entered: ${data}`);
});
```
- stoping standart output
```javascript 
process.exit();
```

5) Delays with setTimeout and setInterval
- setTimeout delays the execution of a function:
```javascript
setTimeout(() => {
    console.log('Executed after 2 seconds');
}, 2000);
```
- setInterval executes a function repeatedly at specified intervals:
```javascript
setInterval(() => {
    console.log('This will run every 3 seconds');
}, 3000);
```




## Node Modules
- The require() function is used to include modules in Node.js.
```javascript
const fs = require('fs');
```
- The readline module allows you to handle input/output from the terminal.
```javascript
const readline = require('readline');
const rl = readline.createInterface({
    input: process.stdin,
    output: process.stdout
});

rl.question('What is your name? ', answer => {
    console.log(`Hello, ${answer}!`);
    rl.close();
});
```
- Some core modules include fs, http, path, os, etc.
```javascript
const EventEmitter = require('events');
const emitter = new EventEmitter();

emitter.on('event', () => {
    console.log('An event occurred!');
});

emitter.emit('event');
```

## File Management and Streams
Writing and Appending Files
- Use fs.writeFile() to write to a file.
- Use fs.appendFile() to append data to an existing file.
- Creating Directories example
```javascript
fs.mkdirSync('new-directory');

fs.mkdir('new-directory', { recursive: true }, err => {
    if (err) throw err;
});
```