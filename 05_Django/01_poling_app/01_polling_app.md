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

# Hum log apna first view likhege, Open the file polls/views.py and put the following Python code in it

```python
from django.http import HttpResponse

def index(request):
    return HttpResponse("Hello, world. You're at the polls index.")
```

#To access it in a browser, we need to map it to a URL - and for this we need to define a URL configuration, or “URLconf” for short. These URL configurations are defined inside each Django app, and they are Python files named urls.py.

To define a URLconf for the polls app, create a file polls/urls.py with the following content

# Is messege ko browser se access karne ke liye, hum log isko map karege ek URL me, uske liye we define a URL configuration, ya "URLconf" short me,
## ye configuration defined hai django app me, matlab mysite me aur wo python file named urls.py file me
## polls app ke liye bhi URLconf  karege, create a file polls/urls.py with the following content
### matlab file create karo urls.py in polls then copy and paste

```python
from django.urls import path

from . import views

urlpatterns = [
    path("", views.index, name="index"),
]
```



