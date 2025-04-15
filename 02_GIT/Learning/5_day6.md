# 🌿 Git ke 4 Areas aur Branching Concept (Hinglish + ASCII Art)

Git ka workflow chaar main areas mein divide hota hai:

1. **Working Directory (ya Working Area)** – Jahan tum files create/edit/delete karte ho.
2. **Staging Area (ya Index)** – Jahan tum `git add` se files ko temporarily rakhte ho commit ke liye.
3. **Local Repository** – Jahan tumhara pura commit history hota hai (using `git commit`).
4. **Remote Repository** – GitHub/GitLab jaise remote server par saved code.

---

## 📂 Git Areas with ASCII Diagram

```text
       +----------------------+
       |  Remote Repository   |
       |  (GitHub/GitLab)     |
       +----------▲-----------+
                  |
              git push / pull
                  |
       +----------▼-----------+
       |   Local Repository   | <---- Branching happens here 🌿
       |  (Commits & Branches)|
       +----------▲-----------+
                  |
              git commit
                  |
       +----------▼-----------+
       |    Staging Area      |
       | (git add)            |
       +----------▲-----------+
                  |
        Editing / Updating
                  |
       +----------▼-----------+
       |  Working Directory   |
       | (Tumhara actual code)|
       +----------------------+
```

---

## 🌿 Branching Kahan hoti hai?

> ✅ **Branching Local Repository mein hoti hai.**

Jab tum `git branch`, `git checkout -b` ya `git switch` use karte ho, to ye sab **local repo ke andar hi hota hai**. Har branch ek alag line of development hoti hai jiska apna commit history hota hai.

### Example Commands:

```bash
git branch feature-login        # ek nayi branch banao
git switch feature-login        # us branch pe switch karo
git commit -m "added login UI"  # commit us branch pe hota hai
```

Remote pe branch bhejne ke liye:

```bash
git push origin feature-login
```

---

Agar aur visuals ya real-life example chahiye toh batao, ek chhota sa demo bana deta hoon.
