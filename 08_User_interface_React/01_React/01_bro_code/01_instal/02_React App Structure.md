## React App Structure (Hinglish)

### 1️⃣ **index.html (public/index.html)**
Ye HTML file hoti hai, jisme ek `<div id="root"></div>` diya jata hai. React isi `root` div ke andar pura UI render karta hai.

```html
<body>
    <div id="root"></div>
    <script type="module" src="/src/main.jsx"></script>
</body>
```

👉 Yahan `<script>` me `main.jsx` file ko joda gaya hai, jo React ko start karne ka kaam karegi.

---

### 2️⃣ **main.jsx (src/main.jsx)**
Ye file ReactDOM ko use karke pure React app ko `index.html` ke `root` div me mount (mount) karti hai.

```jsx
import React from "react";
import ReactDOM from "react-dom/client";
import { StrictMode } from "react";
import App from "./App";

ReactDOM.createRoot(document.getElementById("root")).render(
  <StrictMode>
    <App />
  </StrictMode>
);
```

👉 Yahan `createRoot(document.getElementById("root"))` `index.html` me diye gaye `root` div ko pakadta hai aur `App` component ko uske andar render kar deta hai.

---

### 3️⃣ **App.jsx (src/App.jsx)**
Ye aapka main component hota hai, jisme baaki ke sabhi UI components hote hain.

```jsx
import Header from "./Header";
import Food from "./Food";
import Footer from "./Footer";

function App() {
  return (
    <>
      <Header />
      <Food />
      <Footer />
    </>
  );
}

export default App;
```

👉 Yahan `<Header />`, `<Food />`, aur `<Footer />` alag-alag components hain, jo `src` folder me bane honge.

---

### 4️⃣ **Header.jsx (src/Header.jsx)**
Ek basic header component:

```jsx
function Header() {
  return <h1>Welcome to My Food App</h1>;
}

export default Header;
```

---

### 5️⃣ **Food.jsx (src/Food.jsx)**
Ek aur component, jo food items dikhayega:
Notice isme hum logo ne Js ko dynamically add kiya hai with **{}**

```jsx
function Food() {
    const pasta = "Pasta";
    const salad = "Salad";

    return(
        <div class="menu">
                <h1>Food Menu</h1>
                <div class="item"><strong>Pizza</strong> - $10</div>
                <div class="item"><strong>Burger</strong> - $5</div>
                <div class="item"><strong>Pasta</strong> - $8</div>
                <div class="item"><strong>Salad</strong> - $6</div>
                <li>{pasta}</li>
                <li>{salad}</li>
        </div>
    );

export default Food;
```

---

### 6️⃣ **Footer.jsx (src/Footer.jsx)**
Footer component:

```jsx
function Footer() {
  return <p>© 2025 My Food App</p>;
}

export default Footer;
```

---

### **Pura Flow 🔄**  

1. `index.html` me `<div id="root"></div>` hota hai, jahan React app load hota hai.
2. `main.jsx` `App` ko `root` me render karta hai.
3. `App.jsx` alag-alag components ko import karta hai aur unhe UI me dikhata hai.
4. Har component (`Header`, `Food`, `Footer`) apna-apna HTML render karta hai.

✨ **Is tarah pura React app start hota hai aur browser me UI dikhta hai!** 🚀

## 📂 Project Files

You can access additional project files from Google Drive:

🔗 [Download Project Files](https://drive.google.com/file/d/1JbBQyjo7AtoPtOauBawojsrc2EVm_sWc/view?usp=drive_link)
[Download file](https://drive.google.com/file/d/14bEql4q-pyXp5bjFOs26patCuc9zKSRW/view?usp=sharing)
