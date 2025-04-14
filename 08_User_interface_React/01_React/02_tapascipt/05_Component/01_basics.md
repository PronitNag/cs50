# 🎬 React Movie App Guide (Hinglish Edition)

## 01 - Introduction
React ek JavaScript library hai jo user interfaces banane ke liye use hoti hai. Ye Facebook ne develop ki thi aur iska main focus hota hai reusable components banakar fast aur responsive UI create karna.

**Basic React App banane ke steps:**
```bash
npx create-react-app movie-app
cd movie-app
npm start
```

## 02 - React Components
React mein sab kuch component-based hota hai. Component ek JavaScript function ya class hota hai jo JSX (HTML-like syntax) return karta hai.

```jsx
function Welcome() {
  return <h1>Welcome to React Movie App 🎥</h1>;
}
```

## 03 - Components, State, and Props
**State**: Component ka apna data.
**Props**: Parent component se aane wala data.

```jsx
function Movie(props) {
  return <h2>{props.title}</h2>;
}

function App() {
  return <Movie title="Inception" />;
}
```

**State example:**
```jsx
import { useState } from 'react';

function Counter() {
  const [count, setCount] = useState(0);

  return (
    <div>
      <p>You clicked {count} times</p>
      <button onClick={() => setCount(count + 1)}>Click me</button>
    </div>
  );
}
```

## 04 - Build a Movie App
Ek simple movie list dikhane wali app banate hain:

```jsx
function MovieList() {
  const movies = ["Inception", "Interstellar", "Tenet"];

  return (
    <div>
      <h2>My Favorite Movies</h2>
      <ul>
        {movies.map((movie, index) => <li key={index}>{movie}</li>)}
      </ul>
    </div>
  );
}
```

## 05 - How to Structure Your Components?

Folder structure kuch is tarah ho sakti hai:
```
src/
├── components/
│   ├── MovieList.js
│   └── MovieCard.js
├── App.js
└── index.js
```

Har component ka kaam alag-alag hona chahiye. Jaise `MovieCard` sirf ek movie ko show karega.

## 06 - Style the Movie App
CSS use karke app ko achha look de sakte hain. CSS modules ya styled-components use kar sakte hain.

```css
/* App.css */
.movie-card {
  border: 1px solid #ccc;
  padding: 1rem;
  margin: 1rem;
  border-radius: 8px;
}
```

```jsx
// MovieCard.js
import './MovieCard.css';

function MovieCard({ title }) {
  return <div className="movie-card">{title}</div>;
}
```

## 07 - Conclusion
Ab tak humne seekha:
- React kya hota hai
- Components, state, aur props kaise kaam karte hain
- Simple movie app banana
- Components ko structure karna
- App ko style karna

## 08 - Wrapping Up and What's Next?
Aap yeh explore kar sakte ho next:
- API se movies fetch karna (like OMDB API)
- Routing with React Router
- Context API for global state
- Deploying the app on Netlify/Vercel

Happy Coding! 🚀
