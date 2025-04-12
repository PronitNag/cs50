# Development Setup for ReactJS - Hosting a ReactJS App on Vercel

This guide walks through the process of setting up a ReactJS development workflow and hosting the app on Vercel.

## 🚀 Workflow Overview

1. **You** → Commit / Push → **GitHub**
2. GitHub Triggers Build
3. Build Deploys to **Hosting/CDN Provider** (e.g., Vercel, Netlify)
4. **You & Your Users** → Browse the App on CDN

```text
You → GitHub → Build → Deploy → CDN → Users
```

### 🛠️ Tools Used

- **Version Control System (VCS):** GitHub
- **Hosting/CDN Providers:** Vercel, Netlify

Once you push code to GitHub:
- A build starts automatically.
- The app gets deployed to a public URL on the CDN.
- This makes the app available both locally and publicly for testing.

---

# Getting Started with React Development

## 🎯 Easiest Way to Start

Use CDN links for development:

```html
<script src="react.development.js"></script>
<script src="react-dom.development.js"></script>
```

## 🧱 Types of Builds

1. **Development Build**
2. **Production Build**

## ⚙️ JSX and Transpilation

JSX is React-specific and browsers do not understand it directly.

- Needs transpilation using tools like:
  - **Babel**
  - **Webpack**

You can configure these manually, or use Create React App.

---

# Setting Up React App Using Create React App (CRA)

## ✅ Prerequisites

- Install **Node.js** on your system.

## 📦 Installation Methods

### Global Installation

```bash
npm install -g create-react-app
```

Then create an app:

```bash
create-react-app hello-world
```

### Local (Preferred) Installation

```bash
npx create-react-app my-app
```

- `npx` runs the package without installing it globally.

## 📁 After Installation

- Open the project folder in **Visual Studio Code**.
- Explore the structure:
  - `node_modules/`
  - `package.json`
  - etc.

---

# React App Entry Point and Starting the Server

## 🔁 Navigate into App Folder

```bash
cd hello-world/
```

## 🧾 Entry HTML File

Path: `public/index.html`

```html
<div id="root"></div>
```

- This is where all your React code will be injected.

## 🧠 Entry JS File

Path: `src/index.js`

```jsx
ReactDOM.render(
  <React.StrictMode>
    <App />
  </React.StrictMode>,
  document.getElementById('root')
);
```

### 🧹 Clean Up

Keep only:

- `index.html`
- `index.js`

## ▶️ Run the App

Using **Yarn**:

```bash
yarn start
```

Using **npm**:

```bash
npm start
```

- This boots up a local server (e.g., `localhost:3000`)

---

# Editing `App.js` and Deploying to Vercel

## 📝 Edit `App.js`

Path: `src/App.js`

```jsx
function App() {
  return (
    <div className="App">
      <h1>Hello World!!!</h1>
    </div>
  );
}

export default App;
```

## ☁️ Deployment with Vercel

### Step 1: Push Code

- Commit and push your code to GitHub.

Example repo path:

```
github/react/react-environment/hello-world
```

### Step 2: Go to Vercel

- Click **New Project**
- Click **Import GitHub Project**

### Step 3: Choose Framework

- **Framework Preset:** React

### Step 4: Build and Deploy

- Select the folder containing your project.
- Let Vercel build it.
- Click **Deploy**.

### Step 5: Domain Setup

- Go to **Dashboard** → **Click Domain**
- You can change this domain anytime.

## 🎉 Benefits

- Easily share your app with anyone.
- No need to worry about local environment issues.
- What you see locally is what’s deployed.

---

Happy Coding! 🚀

