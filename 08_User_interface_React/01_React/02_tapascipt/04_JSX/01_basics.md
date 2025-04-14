# ReactJS aur JSX Guide in Hinglish

## 1. Introduction
ReactJS ek JavaScript library hai jo interactive UI banane ke kaam aati hai. Iska main focus components pe hota hai, jisse reusability aur maintainability badh jati hai. JSX React ka ek extension hai jo JavaScript ke andar HTML jaise syntax ko allow karta hai.

## 2. Basics of JSX. What it is and How to Use it?
JSX ek syntax extension hai jo JavaScript ke andar HTML likhne ki suvidha deta hai. Yeh React ke components ko define karne mein help karta hai.

```jsx
const element = <h1>Hello, world!</h1>;
```

Isko browser samajhne ke liye Babel jaise transpiler ki zarurat padti hai jo JSX ko valid JavaScript mein convert karta hai.

## 3. Using Comments in JSX
JSX mein comments likhne ke liye curly braces ke andar JavaScript style comments use kiye jaate hain.

```jsx
const element = (
  <div>
    {/* Yeh ek comment hai */}
    <h1>Hello JSX</h1>
  </div>
);
```

## 4. JavaScript in JSX
JSX mein JavaScript expressions ko curly braces `{}` ke andar likha ja sakta hai.

```jsx
const name = 'Rahul';
const element = <h1>Hello, {name}!</h1>;
```

Aap koi bhi JavaScript function ya variable JSX ke andar embed kar sakte ho.

## 5. How to handle boolean in JSX?
Boolean values directly render nahi hoti. Lekin unka istemal conditionally elements show/hide karne ke liye hota hai.

```jsx
const isLoggedIn = true;
const element = (
  <div>
    {isLoggedIn && <p>Welcome back!</p>}
  </div>
);
```

## 6. How to apply conditions in JSX?
Conditional rendering ternary operator ya `&&` operator ke zariye ki ja sakti hai.

```jsx
const isAdmin = false;
const element = (
  <div>
    {isAdmin ? <h2>Admin Panel</h2> : <h2>User Panel</h2>}
  </div>
);
```

## 7. JSX and Arrays - How to use loops in JSX?
Loop ke liye `.map()` method ka use hota hai. Har item ko unique `key` prop dena zaroori hota hai.

```jsx
const pets = ['Dog', 'Cat', 'Parrot'];
const element = (
  <ul>
    {pets.map((pet, index) => <li key={index}>{pet}</li>)}
  </ul>
);
```

## 8. The Pets app: ReactJS Project to understand JSX
Ek simple React project jisme pet names list honge:

```jsx
function PetsApp() {
  const pets = ['Dog', 'Cat', 'Rabbit'];
  return (
    <div>
      <h1>My Pets</h1>
      <ul>
        {pets.map((pet, index) => (
          <li key={index}>{pet}</li>
        ))}
      </ul>
    </div>
  );
}
```

## 9. JSX and Styling: How to apply CSS Styles to the Pets App?
Inline styles object ke form mein diye jaate hain ya external CSS file se className ka use kiya jata hai.

```jsx
const style = {
  color: 'blue',
  fontSize: '20px'
};

function StyledPets() {
  return <h2 style={style}>Styled Pets App</h2>;
}
```

Ya className ke saath:

```jsx
// App.css
// .pet-title { color: green; font-size: 24px; }

function StyledPets() {
  return <h2 className="pet-title">Styled Pets App</h2>;
}
```

## 10. Wrapping up & What's Next?
Ab aapko JSX ke basics samajh aa gaye hain:
- JSX kya hai aur kaise use hota hai
- JavaScript expressions ka istemal
- Conditional rendering & loops
- Styling
- Ek chhota project

**Next Steps:**
- React components (functional vs class)
- State and props
- Event handling

Happy coding! 🚀
