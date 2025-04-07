# How to initialze and use git to keep track of changes?
First initialize using **git init**

then see if git is initialized using **dir /a**

# 🧠 How Git Tracks Code Changes Using Snapshots (with VS Code on Windows)

Git doesn't save every file version completely — it saves **snapshots** of the files **only when changes happen**, and only for files you've **staged** and **committed**.

Here’s how you can see this in action.

---

## ✅ 1. Setup Git in Your Folder (One-Time)

```bash
git init
🔹 Creates a hidden .git folder that stores all versioning data.

To see it:

bash
Copy
Edit
dir /a      # Windows
ls -a       # Mac/Linux
📁 2. Make a File and Edit It
Create a file:

bash
Copy
Edit
echo Hello World > hello.txt
Make changes to it:

bash
Copy
Edit
echo Second line >> hello.txt
📝 3. Track and Commit Changes
bash
Copy
Edit
git add hello.txt               # Stage the file
git commit -m "Initial commit" # Save a snapshot
Make another change:

bash
Copy
Edit
echo Another line >> hello.txt
Then check what's changed:

bash
Copy
Edit
git status                     # Shows modified files
git diff                       # Shows exact line changes
🕰 4. See the Snapshots (Commits)
bash
Copy
Edit
git log
🔹 Shows the history of commits (snapshots):

Commit hash

Author

Date

Message

Use:

bash
Copy
Edit
git show HEAD
🔹 Shows the latest snapshot in detail (code diff).

👀 5. Visual Git Tools in VS Code
Click on the Source Control icon (🟢) on the left sidebar.

You can view:

Staged changes

Unstaged changes

Commit history (via GitLens extension or Git Graph)

🧾 Summary of Key Git Commands
Command	Purpose
git init	Initialize Git in folder
git add <file>	Stage changes
git commit -m ""	Save a snapshot
git status	View current change state
git diff	See what changed line-by-line
git log	View commit history
git show	View specific commit details
✅ Final Tip
Git tracks only what you commit. Until then, it just sees changes. So think of Git as a camera 📷 — it only takes a new photo (snapshot) when you click "commit"!

vbnet
Copy
Edit

Let me know if you want me to explain branching, undoing mistakes, or pushing to GitHub too!
