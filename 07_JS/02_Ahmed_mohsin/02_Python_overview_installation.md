# Python Environment Setup Guide (Hinglish)

## 4. First Code aur IDE

Programming shuru karne ke liye, aapko ek basic code aur IDE (Integrated Development Environment) ki zaroorat hogi. IDE ek software hai jo coding ko easy banata hai.

### Python ka Pehla Code

Python mein aapka pehla code bahut simple ho sakta hai. Aaiye ek basic "Hello World" program se shuru karte hain:

```python
print("Hello, World!")
```

Is simple code ko run karne par, screen par "Hello, World!" display hoga.

Aap calculator ki tarah bhi Python ka use kar sakte hain:

```python
print(5 + 3)  # Output: 8
print(10 * 2)  # Output: 20
```

### Basic Syntax

Python ki kuch important syntax rules:
- Indentation (spacing) ka use blocks of code define karne ke liye hota hai
- Comments `#` symbol se shuru hote hain
- Variables ko declare karne ki zaroorat nahi hoti

```python
# Yeh ek comment hai
name = "Rahul"  # Variable declaration
age = 25

if age > 18:
    print(name, "adult hai")  # Indentation important hai
```

## 5. IDE Walk Through

### Popular Python IDEs

#### 1. PyCharm
PyCharm professional Python developers ke liye ek powerful IDE hai.

**Features:**
- Code completion
- Syntax highlighting
- Project management
- Integrated debugger
- Version control support

**Interface:**
- Editor window (code likhne ke liye)
- Project panel (left side)
- Terminal (bottom)
- Run/Debug controls

#### 2. Visual Studio Code (VS Code)
VS Code ek lightweight editor hai jo extensions ke saath powerful IDE ban jata hai.

**Features:**
- Python extension support
- Integrated terminal
- Debugging capabilities
- Git integration
- Customizable interface

**Interface:**
- Editor area (center)
- Explorer (left sidebar)
- Extensions panel
- Terminal (bottom)
- Status bar (bottom)

#### 3. Jupyter Notebook
Data science aur interactive coding ke liye perfect.

**Features:**
- Code aur output ek saath display
- Markdown support
- Interactive visualizations
- Cell-by-cell execution

**Interface:**
- Cells (code ya markdown)
- Toolbar (top)
- File browser (left)
- Kernel status (right top)

## 6. What is Virtual Environment

Virtual environment Python ka ek isolated environment hota hai jahan aap specific projects ke liye alag packages aur dependencies install kar sakte hain. Yeh aapke system ke global Python installation ko affect kiye bina project-specific setup maintain karne mein help karta hai.

### Virtual Environment Ke Fayde

1. **Isolation:** Har project ke liye alag environment, conflicts se bachne ke liye
2. **Dependency Management:** Project-specific packages aur unke versions ko maintain karna
3. **Portability:** Dusre systems par easily reproduce karna
4. **Clean Development:** System Python ko clutter-free rakhna

Virtual environment ke bina, har new package global Python installation mein install hoga, jisse dependency conflicts ho sakte hain.

## 7. Installing and Creating Virtual Environment

### Installation

Python 3.3+ mein `venv` module pre-installed aata hai. Purane versions mein, aapko `virtualenv` install karna pad sakta hai.

```bash
# Agar zaroorat ho to virtualenv install karne ke liye
pip install virtualenv
```

### Virtual Environment Create Karna

#### Using venv (Python 3.3+)

```bash
# Windows par
python -m venv myproject_env

# Linux/Mac par
python3 -m venv myproject_env
```

#### Using virtualenv

```bash
# Windows par
virtualenv myproject_env

# Linux/Mac par
virtualenv myproject_env
```

Is command se "myproject_env" naam ka folder create hoga jisme Python interpreter aur pip ka isolated copy hoga.

## 8. Activating Virtual Environment

Virtual environment ko use karne ke liye, usse activate karna zaroori hai.

### Windows Par

```bash
myproject_env\Scripts\activate
```

### Linux/Mac Par

```bash
source myproject_env/bin/activate
```

Jab virtual environment activate hota hai, to command prompt/terminal mein environment ka naam dikhai dega, jaise:

```
(myproject_env) C:\Users\Username\Projects>
```

### Virtual Environment Deactivate Karna

Virtual environment se bahar aane ke liye, simply type karein:

```bash
deactivate
```

## 9. Run Code and Keyboard Shortcuts

### Code Run Karna

#### Command Line Se Run Karna

```bash
# Simple Python file run karna
python myscript.py

# Arguments ke saath
python myscript.py arg1 arg2
```

#### IDE Mein Code Run Karna

Alag-alag IDEs mein code run karne ke different tarike hain:

1. **PyCharm:**
   - "Run" button click karein
   - Right-click karke "Run" select karein
   - Run menu se "Run" select karein

2. **VS Code:**
   - File open karke top-right corner mein "Play" button click karein
   - Terminal mein manual command type karein

3. **Jupyter Notebook:**
   - Cell run karne ke liye "Run" button ya Shift+Enter press karein

### Keyboard Shortcuts

#### PyCharm Keyboard Shortcuts

| Action | Windows/Linux | Mac |
|--------|--------------|-----|
| Run | Shift+F10 | Control+R |
| Debug | Shift+F9 | Control+D |
| Save | Ctrl+S | Command+S |
| Format Code | Ctrl+Alt+L | Command+Option+L |
| Find | Ctrl+F | Command+F |
| Replace | Ctrl+R | Command+R |
| Comment/Uncomment | Ctrl+/ | Command+/ |
| Complete code | Ctrl+Space | Control+Space |

#### VS Code Keyboard Shortcuts

| Action | Windows/Linux | Mac |
|--------|--------------|-----|
| Run Python File | F5 | F5 |
| Save | Ctrl+S | Command+S |
| Format Document | Shift+Alt+F | Shift+Option+F |
| Toggle Comment | Ctrl+/ | Command+/ |
| Search | Ctrl+F | Command+F |
| Replace | Ctrl+H | Command+Option+F |
| Open Terminal | Ctrl+` | Control+` |
| Intellisense | Ctrl+Space | Command+Space |

#### Jupyter Notebook Keyboard Shortcuts

| Action | Shortcut |
|--------|----------|
| Run Cell | Shift+Enter |
| Run Cell & Insert Below | Alt+Enter |
| Insert Cell Above | A |
| Insert Cell Below | B |
| Delete Cell | D, D (press twice) |
| Switch to Markdown | M |
| Switch to Code | Y |
| Save Notebook | Ctrl+S / Command+S |

### Tips for Efficient Coding

1. **Keyboard shortcuts seekhein:** IDE ki efficiency badhane ke liye
2. **Autocomplete ka use karein:** Tab ya Ctrl+Space se suggestions dekhen
3. **Error highlighting par dhyan dein:** Red underlines ko ignore na karein
4. **Code formatting regularly karein:** Clean code maintain karein
5. **Version control use karein:** Git ke saath code ko track karein

Virtual environment aur IDE ke saath efficient coding workflow develop karna aapke programming journey mein bahut important hai. Regular practice se in tools par expertise develop hogi.
