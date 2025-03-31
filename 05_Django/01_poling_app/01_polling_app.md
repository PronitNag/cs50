# Django Project Setup - Hinglish

## 1. **Command Prompt Open Karo**
Windows me `Win + R` dabao, `cmd` likho aur `Enter` dabao.

## 2. **djangotutorial Folder Me Jao**
Agar tumhara folder `Documents` me hai, toh ye command chalao:
```sh
cd C:\Users\YourUsername\Documents\djangotutorial
```
Agar kahin aur hai toh uska path likho.

## 3. **Virtual Environment Banao (Recommended)**
```sh
python -m venv myenv
```
Phir activate karo:
```sh
myenv\Scripts\activate
```

## 4. **Django Install Karo**
```sh
pip install django
```

## 5. **Naya Django Project Banao**, PRoject ka naam hai mysite jo ki djangotutorial me bana haii
```sh
django-admin startproject mysite
```

## 6. **Project Folder Me Jao**
```sh
cd mysite
```

## 7. **Server Start Karo**
```sh
python manage.py runserver
```
Agar sab sahi hai toh ye dikhega:
```
Starting development server at http://127.0.0.1:8000/
```
Browser me jaake ye URL open karo aur Django ka welcome page dekho. 🎉

Ye sare kam command prompt se karo, then **ctrl+c** to exit, uske baad go to vs code

make sure that you are in the same directory as **manage.py** then type out the command

use **dir** and **cd** to do that

uske baad type kare 

```sh
py manage.py startapp polls
```
