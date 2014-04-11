#Package.json in Node.js

From Nodejs Doc:
>The most important things in your package.json are the name and version fields. Those are actually required, and your package won’t install without them. The name and version together form an identifier that is assumed to be completely unique.
 
In project root folder package.json describes your application properties such as
*	name
*	dependencies
*	scripts
*	dependencies

An example of package.json
>{
     “name”: “application-name”, //Your application/package name
     “version”: “0.0.1″, //application/package version
     “private”: true, 
     “scripts”: {
     “start”: “node app.js” 
},
    “dependencies”: { 
           “express”: “3.2.4″,
           “jade”: “*”
    }
}

When you run the command from the root folder

>npm install

It will create a node_modules folder and the declared dependencies are installed in this folder. To run a script file using package.json, first include the script(scriptfilename.js) in package.json and the command

>npm scriptfilename

will run that script.

If you have a npm account and you want to publish your package in npm, the version field is used to track the version of your package. To publish the package use the command

>npm publish

To start a project, create a folder, and run “npm init” in that folder.Then when installing npm modules use: 

>npm install <name> –save

This adds them as dependencies to your package.json.

##Version:
Version must be parseable by node-semver. Check node-semver at https://github.com/isaacs/node-semver. To install node-semver use the command

>npm install semver

##Description :
This helps people discover your package, as it’s listed in npm search.

##Keywords :
It’s an array of strings. This helps people discover your package as it’s listed in npm search.
homepage. The url to the project homepage.

##License :
Specify a license for your package so that people know how they are permitted to use it, and any restrictions you’re placing on it.

example

>{ “license” : “BSD-3-Clause” }

##Reference:

* package.json – https://www.npmjs.org/doc/json.html
* npm-scripts – https://www.npmjs.org/doc/misc/npm-scripts.html
* Running Scripts with npm – http://anders.janmyr.com/2014/03/running-scripts-with-npm.html

