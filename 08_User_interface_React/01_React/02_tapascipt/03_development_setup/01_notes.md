
Filename: README.md

markdown
Copy
Edit
# Development Setup for ReactJS - Hosting a ReactJS App on Vercel

We are going to learn about a workflow that will help us to set up the entire pipeline, such that the moment we want to do anything incremental into our application, it is made publicly available for someone to view.

## Workflow Overview

1. **You** → Commit / Push → **Git-based VCS (e.g., GitHub)**
2. GitHub Triggers Build
3. Build Deploys to **Hosting/CDN Provider** (e.g., Vercel, Netlify)
4. **You & Your Users** → Browse the App on CDN

```text
You → GitHub → Build → Deploy → CDN/ADN → Users
Tools Used
Version Control System (VCS): GitHub

Hosting/CDN Providers: Vercel, Netlify

Key Points
Once we push code to GitHub, a build kicks off.

After the build happens, it can be automatically deployed for us on some CDN.

So, the app becomes kind of publicly available.

It is securely available and provides a URL to access this particular app.

This setup will help us to test locally and publicly.

This document helps understand how to automate deployment of a ReactJS application using tools like GitHub and hosting platforms like Vercel or Netlify.

# Getting Started with React Development

## Easiest Way to Start React Development

The easiest way that we can get started with React development is by pointing to a couple of scripts via CDN links.

Using our own script, we can point to two important things:

1. `react.development.js`
2. `react-dom.development.js`

## Types of Builds

There are two types of builds:

1. Development
2. Production

## JSX and Transpilation

JSX is very much React-specific syntax, which browsers do not understand.

Browsers only understand HTML and JS.

So, this means everything we are writing in JSX format has to be transpiled to something that the browser understands.

We have to take care of those transpilation steps, and for that we need to learn tools like:

- **Babel**
- **Webpack**

...or do certain configuration manually.

## Create React App (CRA)

So instead, we are going to learn **Create React App Tool (CRA)** → it will do everything for us!

ilename: setup-react-app.md

markdown
Copy
Edit
# Setting Up React App Using Create React App (CRA)

## Prerequisites

- We need to have **Node.js** installed on our local machine.

## Installation Methods

We can install Create React App globally using:

```bash
npm install -g create-react-app
This will create the React app tool globally.

But if we want to create React apps locally (recommended because it's needed only once), we can use:

bash
Copy
Edit
npx create-react-app my-app
npx: Node Package Executor

Alternate Installation
You can also use:

bash
Copy
Edit
npm install -g create-react-app
create-react-app hello-world
But this will create a new environment globally and install packages.

Whereas, using npx, the tool is not installed permanently on your local box — it just runs the setup.

After Installation
Open the app folder in Visual Studio Code.

Explore what the folder structure looks like.

Notes
Node modules like @babel are used by React itself.

A special file called package.json contains all the library definitions and dependencies.

yaml
Copy
Edit

Filename: react-entry-point.md

markdown
Copy
Edit
# React App Entry Point and Starting the Server

## Navigate into Your App

```bash
cd hello-world/
Entry HTML File
Path: hello-world/public/index.html

html
Copy
Edit
<div id="root"></div>
This is the entry point of the application.

Everything we write in our React application will appear inside this <div> tag dynamically.

Entry JS File
Path: hello-world/src/index.js

js
Copy
Edit
ReactDOM.render(
  <React.StrictMode>
    <App />
  </React.StrictMode>,
  document.getElementById('root')
);
Simplifying the Folder
If we don't need most of the files, we can clean them up, except for:

index.html

index.js

Running the Project
To run the project and see the output:

Using Yarn:

bash
Copy
Edit
yarn start
Or using npm:

bash
Copy
Edit
npm start
What Happens When We Start?
Once you start the application, it:

Boots up a server locally

Makes the application available locally

Lets your project run from that local server on a particular URL (like localhost:3000)

Filename: react-app-js-vercel.md

markdown
Copy
Edit
# Editing `App.js` and Deploying to Vercel

## Edit the `App.js` File

Path: `src/App.js`

- Once the development server is running on your local host,
- Go to the `App.js` file and remove the logo part.

```jsx
function App() {
  return (
    <div className="App">
      <h1>Hello World!!!</h1>
    </div>
  );
}

export default App;
Deployment with Vercel
Steps to Deploy:
Commit and Push Code

Commit your code.

Push it to your GitHub repository.

Example repo path:

bash
Copy
Edit
github/react/react-environment/hello-world
Go to Vercel

Click New Project.

Click Import and select the GitHub project you pushed.

Choose Framework

Framework Preset: React

Build and Deploy

Select the folder.

Let Vercel handle the build.

Click Deploy.

Dashboard and Domain

Go to Dashboard → Click the Domain.

You can change the domain name anytime.

Share the domain link with anybody.

Benefits
No need to worry about local environment.

What's happening in development may or may not happen in production.
