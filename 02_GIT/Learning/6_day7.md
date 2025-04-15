# 🔀 Git Merge aur Diff Ka Detailed Explanation (Hinglish + ASCII Art)

## 🔁 1. Git Merge Kya Hota Hai?

Jab tum ek branch ka kaam complete kar lete ho (jaise `feature-1`), aur uska code tum `main` branch mein lana chahte ho, tab **merge** ka use hota hai.

---

### 🔧 Merge ka Basic Flow:

```bash
git switch main         # pehle main branch pe jao
git merge feature-1     # ab feature-1 ka code main mein le aao
```

---

### 📊 ASCII Diagram - Before Merge

```text
       main
         |
         C1 --- C2
                        feature-1   C3 --- C4
```

### ✅ After `git merge feature-1`

```text
       main
         |
         C1 --- C2 ------- M
                 \       /
       feature-1   C3---C4
```

🔸 `M` is the **merge commit** jo dono branches ko combine karta hai.

---

### 🤯 Merge Conflicts (Agar dono branches ne same file ke same line ko change kiya ho)

```bash
Auto-merging file.txt
CONFLICT (content): Merge conflict in file.txt
```

❗ Is case mein tumhe manually file edit karke conflict resolve karna padta hai.

---

## 🔍 2. Git Diff Kya Hota Hai?

`git diff` se tum changes compare kar sakte ho. Ye batata hai ki kya-kya changes kiye gaye hain files mein.

---

### 📊 ASCII Diagram

```text
       main
         |
         C1 --- C2
                 \
       feature     C3
```

Agar tum compare karna chahte ho `feature` aur `main` ke beech ka difference:

```bash
git diff main..feature
```

Ya agar tum sirf unstaged changes dekhna chahte ho:

```bash
git diff
```

### 🛠 Types of Diff Commands:

| Command | Use |
|--------|-----|
| `git diff` | Working directory aur staging area ke beech ke changes |
| `git diff --staged` | Staging area aur last commit ke beech ke changes |
| `git diff branch1..branch2` | Do branches ke beech ka diff |

---

### 🧪 Sample Output:

```diff
- console.log("Old Line");
+ console.log("New Line");
```

Red (minus) = Remove kiya gaya  
Green (plus) = Add kiya gaya

---

Agar tumhe practical example ke sath samajhna ho toh bolna, main ek chhota demo scenario likh deta hoon! 💻
