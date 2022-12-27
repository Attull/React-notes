<h1 align="center">
  React Fundamentals Notes
</h1>

<p align="center">
   <a style="text-decoration:none">
    <img src="https://img.shields.io/badge/Still%20Evolving-grey" alt="version" />
  </a> 
</p>

## Introduction

* React is a Javascript library focused on building rich user interfaces.
* It is not a framework.
* It does not handle ```http``` and ```requests```, but has a rich ecosystem to get that work done.
* It has a component based architecture.
* React follows a [Declaritive paradigm](https://en.wikipedia.org/wiki/Declarative_programming) instead of the conventional [Imperative paradigm](https://en.wikipedia.org/wiki/Imperative_programming).

## Creating a React Project

* There are **two** ways to create a React project

    1. Using ```npx``` :✔️<br/> 
      - **Node Package Runner**, which gets installed while installing Node<br/>
      - It allows to directly run create-react-app without installing it<br/>
      - Use command: ```npx create-react-app project_name```
    
    2. Using ```npm```: <br/>
      - It requires to install the ```create-react-app```globally and then use it to generate projects<br>
      - Use command: ```npm install create-react-app -g```<br>
    and then ```create-react-app project_name```

## Folder Structure

Creating a react project comes with some files, which we need to understand. Following are the files which we need to know for every react project we create.

* ```package.json```: This files contains the dependencies and scripts required for the project.

* ```node_modules```: This folder contains all the installed dependencies. It is generated either when you run **create-react-app** command or when you run **npm install** command.

* ```public```: This folder has an entry point to our react app.

  * ```index.html```: This is the only ```.html ``` file in our application as react is a single page application. This is the entry point which is served on the client side and typically no code is added to this file. 

  * ```manifest.json```: It is related to the progressive web applications.

  * ```favicon.ico```: Title bar icon file.

* ```src```: This is the folder where the actual code is written and organized. 

  * ```index.js```: This is the very first file which is called by the entry file i.e ```index.html```.

  * ```App.js```: This is the root component of our react app. All the other components are enclosed within this component. It is responsible for all the html displayed on the browser. ```index.js``` imports this App component. 

  * ```App.css```: Global styling options are written in this file. Eg. App theme can be written in this file.

  * ```App.test.js```: This file is used to write unit test cases.

  * ```index.css```: It applies styling to the body tag.

  * ```logo.svg```: reference in the App component

  * ```serviceworker.js```: It is related to the progressive web applications.

## Components

* The entire react app is made up of small individual modules called as Components. 
* The **App** component is the root component (```App.js```)
* It contains all the other component.
* **Naming Convention**: Components are always named in Pascal Case i.e the starting character is always in uppercase. 
* Components are resuable.
* That means, same components can be reused with different **props** (properties) and **state** (data) to display different information.
* Component can contain another component. 
* Eg: 
![image](https://user-images.githubusercontent.com/37962354/87883461-2980b180-c9cd-11ea-9626-e02dbaab2bdf.png)
* All these are individual components are enclosed in the **App** component which is the root component.
* A component code is placed inside a Javascript file.✔️
* However, we can also have seperate components files with ```.jsx``` extension. 
* There are two types of Components: 
  * Functional Components
  * Class Components

