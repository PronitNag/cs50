# Git Stashing aur Undoing Kaise Kaam Karta Hai

## Git के चार क्षेत्र (Four Areas of Git)

```
+-------------------+      +----------------+      +----------------+      +----------------+
|                   |      |                |      |                |      |                |
|   Working Area    | -->  |  Staging Area  | -->  |   Local Repo   | -->  |   Remote Repo  |
|                   |      |                |      |                |      |                |
+-------------------+      +----------------+      +----------------+      +----------------+
     (Changes)              (git add)              (git commit)            (git push)
```

## Stashing Kya Hai?

Stashing ek temporary storage hai jahan aap apne incomplete changes ko save kar sakte hain bina commit kiye. Ye Git ke main four areas ke alawa ek alag jagah hai.

```
+-------------------+      +----------------+      +----------------+      +----------------+
|                   |      |                |      |                |      |                |
|   Working Area    | -->  |  Staging Area  | -->  |   Local Repo   | -->  |   Remote Repo  |
|                   |      |                |      |                |      |                |
+-------------------+      +----------------+      +----------------+      +----------------+
       ^  |
       |  |
       |  v
+-------------------+
|                   |
|    Stash Area     |
|                   |
+-------------------+
```

### Stashing के Use Cases

1. **Branch Switch Karna**: Jab aap ek branch par kaam kar rahe hain aur doosre branch par switch karna chahte hain, lekin abhi commit nahi karna chahte.

2. **Urgent Bugfix**: Aapko koi urgent bug fix karna hai, lekin current changes abhi incomplete hain.

### Common Stashing Commands

```
# Changes ko stash karna
git stash

# Stash ko wapas apply karna aur stash list se remove karna
git stash pop

# Stash ko wapas apply karna lekin stash list mein rehne dena
git stash apply

# Stash list dekhna
git stash list

# Specific stash apply karna
git stash apply stash@{2}

# Stash ko drop karna
git stash drop stash@{1}

# Sabhi stashes ko clear karna
git stash clear
```

## Undoing Changes in Git

Git mein changes ko undo karne ke alag-alag tareeke hain, jo depend karta hai ki aap kis "area" mein changes ko undo karna chahte hain.

### 1. Working Area Mein Undoing

```
# Ek specific file ko undo karna
git checkout -- filename.txt

# Ya phir
git restore filename.txt

# Sabhi changes ko undo karna
git checkout -- .
git restore .
```

### 2. Staging Area Mein Undoing (Unstaging)

```
# File ko staging se working area mein wapas lana
git reset HEAD filename.txt

# Ya modern command
git restore --staged filename.txt
```

### 3. Local Repository Mein Undoing

```
# Last commit ko undo karna, lekin changes working area mein rakhna
git reset --mixed HEAD~1

# Last commit ko puri tarah se undo karna (changes bhi delete ho jayenge)
git reset --hard HEAD~1

# Last commit ko modify karna
git commit --amend
```

### 4. Remote Repository Mein Undoing

```
# Local mein revert commit create karke push karna
git revert commit_hash
git push origin branch_name

# Force push (WARNING: Iska use sirf tab karna jab aap sure ho)
git push -f origin branch_name
```

## Undoing aur Stashing Area-wise Summary

```
+-------------------+      +----------------+      +----------------+      +----------------+
|                   |      |                |      |                |      |                |
|   Working Area    | -->  |  Staging Area  | -->  |   Local Repo   | -->  |   Remote Repo  |
|                   |      |                |      |                |      |                |
+-------------------+      +----------------+      +----------------+      +----------------+
    git checkout           git reset HEAD         git reset --mixed       git revert
    git restore            git restore --staged   git reset --hard        git push -f
                                                  git commit --amend
       ^  |
       |  |
       |  v
+-------------------+
|                   |
|    Stash Area     |  <-- git stash / git stash pop / git stash apply
|                   |
+-------------------+
```

## Yaad Rakhne Wali Important Baatein

1. **Stash** temporary storage hai - ye aapke changes ko save karta hai bina commit kiye.

2. **Working Area** mein changes ko undo karne ke liye `git checkout` ya `git restore` use karein.

3. **Staging Area** se files ko unstage karne ke liye `git reset HEAD` ya `git restore --staged` use karein.

4. **Local Repository** mein commits ko undo karne ke liye `git reset` ya `git commit --amend` use karein.

5. **Remote Repository** mein changes ko undo karne ka safe tarika `git revert` hai.

6. `git reset --hard` ka use carefully karein, kyunki ye aapke changes ko permanently delete kar deta hai.

7. `git push -f` (force push) ka use sirf tab karein jab aap 100% sure ho, kyunki isse doosre developers ke workflow mein problem ho sakti hai.

Ye concepts samajhna Git ke saath efficiently kaam karne ke liye bahut zaroori hai. Command line par practice karke inhe aur better samjhein!
