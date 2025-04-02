# What is a component in React?
```text
Component is a self-contained section of code that functions as a reusable building block, Like Lego
we can build a compilcated structure like Lego
```

# What is JSX in React?
```text
Jsx means Javascript XML which allows to write HTML code inside JS file
```

# What is Virtual DOM?
```text
It is a light weight version of real DOM of a webpage
we can keep track of any changes in virtual DOM and then
and apply those changes in real DOM
```

# Why we need node?
```text
Node is a backend javascript runtime enviroment that lets
javascript executes outside web browser, so download node
```

# Issues with React:
- It is not designed for what you are using.
- Hence lot of GAP's.
- Lot of 3rd party implementations are required

# Q) what are the steps needed to download and run react?
#### 1- To start programming with React, you'll need to have three things:

- A web browser
- A code editor
- Node.js

 #### 2 - Open command prompt on your PC and test

		C:\> node  -v				
		C:\> npm  -v

	Note: Make sure that you have the latest version of Node 20x & Npm 10x.

#### 3. Download extensions of VS Code

		a) Live Server
		b) vscode-icons
		c) IntelliSense for CSS class names in HTML
		d) ESLint
  
#### 4. Create a folder named Website and open with VS code, then go to hamburger menu and open terminal

In the terminal type

```sh
npm create vite@latest
```

```plaintext
Ok to proceed? (y) y
│
◇  Project name:
│  my-react-app
│
◇  Select a framework:
│  React
│
◇  Select a variant:
│  JavaScript
│
◇  Scaffolding project in M:\Website\my-react-app...
│
└  Done. Now run:

  cd my-react-app
  npm install
  npm run dev
```

Remember **npm run dev** is to kick start the server

# what is the Project structure in react?
#### Project Structure

| File / Folder       | Description |
|---------------------|-------------|
| `public`           | Contains static resources like HTML, images, docs, etc. |
| `src`              | Contains dynamic resources like SCSS, CSS, JS, JSX, TS, TSX, etc. |
| `node_modules`     | Contains all external library files and packages installed using NPM package manager. |
| `package.json`     | Contains project meta data. contained in key value pair|
| `package-lock.json` | Contains complete dependencies list that are used for the project. |
| `.gitignore`       | Configures the resources to ignore while publishing to GIT. |
| `README.md`        | Contains help documentation. |

# WHat are the files that we need to delete in the file?
# How do we run a server in react?
# what are the basic step to build a component in react?
