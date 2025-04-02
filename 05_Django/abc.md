# Django Polls App Tutorial - All 8 Parts (Hinglish मे समझाया गया)

## विषय-सूची (Table of Contents)

1. [Part 1: Project Setup aur Initial App](#part-1-project-setup-aur-initial-app)
2. [Part 2: Models aur Admin Interface](#part-2-models-aur-admin-interface)
3. [Part 3: Views aur Templates](#part-3-views-aur-templates)
4. [Part 4: Forms aur Generic Views](#part-4-forms-aur-generic-views)
5. [Part 5: Testing](#part-5-testing)
6. [Part 6: Static Files](#part-6-static-files)
7. [Part 7: Admin Interface Customization](#part-7-admin-interface-customization)
8. [Part 8: Reusable Apps](#part-8-reusable-apps)

## Part 1: Project Setup aur Initial App

### 1.1 Django Installation

```bash
# Django install karein
pip install django

# Version check karein
python -m django --version
```

### 1.2 Project Creation

```bash
# New project create karein
django-admin startproject mysite

# Project directory structure
mysite/
    manage.py
    mysite/
        __init__.py
        settings.py
        urls.py
        asgi.py
        wsgi.py
```

**Hinglish explanation:** `startproject` command se django ek naya project folder structure create karta hai. `manage.py` ek command-line utility hai jo project ke management mein help karta hai. `mysite/` folder actual Python package hai jo hamara project hai.

### 1.3 Development Server Run Karna

```bash
# Project directory mein jaakar command run karein
cd mysite
python manage.py runserver
```

**Hinglish explanation:** Ye command development server start karta hai. Default port 8000 pe server start hoga. Browser mein `http://127.0.0.1:8000/` open karke check kar sakte hain.

### 1.4 Polls App Create Karna

```bash
# Project root directory mein command run karein
python manage.py startapp polls

# App directory structure
polls/
    __init__.py
    admin.py
    apps.py
    migrations/
        __init__.py
    models.py
    tests.py
    views.py
```

**Hinglish explanation:** `startapp` command se django ek new app structure create karta hai. Ek project mein multiple apps ho sakte hain.

### 1.5 First View Create Karna

```python
# polls/views.py
from django.http import HttpResponse

def index(request):
    return HttpResponse("Hello, world. You're at the polls index.")
```

**Hinglish explanation:** Yeh humara pehla view function hai jo sirf ek simple text return karta hai.

### 1.6 URL Configuration

```python
# polls/urls.py (create this file)
from django.urls import path
from . import views

urlpatterns = [
    path('', views.index, name='index'),
]
```

```python
# mysite/urls.py
from django.contrib import admin
from django.urls import include, path

urlpatterns = [
    path('polls/', include('polls.urls')),
    path('admin/', admin.site.urls),
]
```

**Hinglish explanation:** URLs se views ko map karte hain. `include()` function se polls app ke URLs ko main URLs mein include kiya jata hai.

## Part 2: Models aur Admin Interface

### 2.1 Database Setup

```python
# mysite/settings.py (partial)
DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.sqlite3',
        'NAME': BASE_DIR / 'db.sqlite3',
    }
}
```

**Hinglish explanation:** By default Django SQLite3 database use karta hai. Production mein PostgreSQL, MySQL ya other database use kar sakte hain.

### 2.2 Models Define Karna

```python
# polls/models.py
from django.db import models
import datetime
from django.utils import timezone

class Question(models.Model):
    question_text = models.CharField(max_length=200)
    pub_date = models.DateTimeField('date published')
    
    def __str__(self):
        return self.question_text
    
    def was_published_recently(self):
        now = timezone.now()
        return now - datetime.timedelta(days=1) <= self.pub_date <= now

class Choice(models.Model):
    question = models.ForeignKey(Question, on_delete=models.CASCADE)
    choice_text = models.CharField(max_length=200)
    votes = models.IntegerField(default=0)
    
    def __str__(self):
        return self.choice_text
```

**Hinglish explanation:** 
- `Question` model mein ek question text aur publish date hai
- `Choice` model mein choice text, votes count, aur foreign key se question se relation hai
- `__str__` method is used for human-readable representation
- `was_published_recently` method check karta hai ki question pichle 24 ghanton mein publish hua tha ya nahi

### 2.3 App ko INSTALLED_APPS mein Add Karna

```python
# mysite/settings.py (partial)
INSTALLED_APPS = [
    'polls.apps.PollsConfig',  # Add this line
    'django.contrib.admin',
    'django.contrib.auth',
    'django.contrib.contenttypes',
    'django.contrib.sessions',
    'django.contrib.messages',
    'django.contrib.staticfiles',
]
```

**Hinglish explanation:** Django ko batate hain ki polls app installed hai.

### 2.4 Migrations Create aur Apply Karna

```bash
# Migrations create karein
python manage.py makemigrations polls

# Migration dekh sakte hain (optional)
python manage.py sqlmigrate polls 0001

# Migrations apply karein
python manage.py migrate
```

**Hinglish explanation:** 
- `makemigrations` command model changes ki based par migration files create karta hai
- `sqlmigrate` se actual SQL queries dekh sakte hain
- `migrate` se database mein tables create ho jate hain

### 2.5 Django Shell ka Use

```bash
# Django shell start karein
python manage.py shell
```

```python
# Shell mein test code
>>> from polls.models import Choice, Question
>>> from django.utils import timezone
>>> q = Question(question_text="What's new?", pub_date=timezone.now())
>>> q.save()
>>> q.id
1
>>> q.question_text
"What's new?"
>>> q.pub_date
datetime.datetime(2023, 5, 18, 12, 30, 45, tzinfo=<UTC>)
>>> Question.objects.all()
<QuerySet [<Question: What's new?>]>
```

**Hinglish explanation:** Django shell se interactive way mein database operations test kar sakte hain.

### 2.6 Admin User Create Karna

```bash
# Create superuser
python manage.py createsuperuser
```

### 2.7 Admin Interface mein Models Register Karna

```python
# polls/admin.py
from django.contrib import admin
from .models import Question

admin.site.register(Question)
```

**Hinglish explanation:** Admin module mein Question model register karte hain taki admin interface mein edit kar sakein.

## Part 3: Views aur Templates

### 3.1 More Views Add Karna

```python
# polls/views.py
from django.http import HttpResponse
from .models import Question

def index(request):
    latest_question_list = Question.objects.order_by('-pub_date')[:5]
    output = ', '.join([q.question_text for q in latest_question_list])
    return HttpResponse(output)

def detail(request, question_id):
    return HttpResponse(f"You're looking at question {question_id}.")

def results(request, question_id):
    return HttpResponse(f"You're looking at the results of question {question_id}.")

def vote(request, question_id):
    return HttpResponse(f"You're voting on question {question_id}.")
```

**Hinglish explanation:** Ye additional views hain jo different functionality provide karte hain.

### 3.2 URLs Update Karna

```python
# polls/urls.py
from django.urls import path
from . import views

app_name = 'polls'  # Namespace for the app
urlpatterns = [
    path('', views.index, name='index'),
    path('<int:question_id>/', views.detail, name='detail'),
    path('<int:question_id>/results/', views.results, name='results'),
    path('<int:question_id>/vote/', views.vote, name='vote'),
]
```

**Hinglish explanation:** `app_name` add karne se URL namespacing ho jata hai. Path patterns mein `<int:question_id>` se URL se parameters capture kar sakte hain.

### 3.3 Templates Directory Create Karna

```
polls/
    templates/
        polls/
            index.html
```

### 3.4 Template File Create Karna

```html
<!-- polls/templates/polls/index.html -->
{% if latest_question_list %}
    <ul>
    {% for question in latest_question_list %}
        <li><a href="/polls/{{ question.id }}/">{{ question.question_text }}</a></li>
    {% endfor %}
    </ul>
{% else %}
    <p>No polls are available.</p>
{% endif %}
```

**Hinglish explanation:** Template mein Django Template Language (DTL) ka use karke dynamic content display karte hain.

### 3.5 View ko Template ke Saath Update Karna

```python
# polls/views.py (index view update)
from django.shortcuts import render
from .models import Question

def index(request):
    latest_question_list = Question.objects.order_by('-pub_date')[:5]
    context = {'latest_question_list': latest_question_list}
    return render(request, 'polls/index.html', context)
```

**Hinglish explanation:** `render()` function templates ke saath context data pass karke HTML response generate karta hai.

### 3.6 404 Error Handle Karna

```python
# polls/views.py (detail view update)
from django.shortcuts import get_object_or_404, render

def detail(request, question_id):
    question = get_object_or_404(Question, pk=question_id)
    return render(request, 'polls/detail.html', {'question': question})
```

**Hinglish explanation:** `get_object_or_404()` function se object get karne ki koshish karte hain, object na milne par 404 error raise hota hai.

### 3.7 Detail Template Create Karna

```html
<!-- polls/templates/polls/detail.html -->
<h1>{{ question.question_text }}</h1>
<ul>
{% for choice in question.choice_set.all %}
    <li>{{ choice.choice_text }}</li>
{% endfor %}
</ul>
```

**Hinglish explanation:** Detail template mein question ke choices display karte hain.

### 3.8 URL Template Tag Use Karna

```html
<!-- polls/templates/polls/index.html (updated) -->
{% if latest_question_list %}
    <ul>
    {% for question in latest_question_list %}
        <li><a href="{% url 'polls:detail' question.id %}">{{ question.question_text }}</a></li>
    {% endfor %}
    </ul>
{% else %}
    <p>No polls are available.</p>
{% endif %}
```

**Hinglish explanation:** Hardcoded URLs ki jagah `{% url %}` template tag use karte hain, jisse URL patterns change hone par bhi links sahi rahenge.

## Part 4: Forms aur Generic Views

### 4.1 Vote Form Create Karna

```html
<!-- polls/templates/polls/detail.html (updated) -->
<h1>{{ question.question_text }}</h1>

{% if error_message %}<p><strong>{{ error_message }}</strong></p>{% endif %}

<form action="{% url 'polls:vote' question.id %}" method="post">
{% csrf_token %}
{% for choice in question.choice_set.all %}
    <input type="radio" name="choice" id="choice{{ forloop.counter }}" value="{{ choice.id }}">
    <label for="choice{{ forloop.counter }}">{{ choice.choice_text }}</label><br>
{% endfor %}
<input type="submit" value="Vote">
</form>
```

**Hinglish explanation:** 
- Vote karne ke liye form create kiya hai
- `{% csrf_token %}` security ke liye CSRF protection add karta hai
- Radio buttons se user choice select kar sakta hai

### 4.2 Vote Function Implement Karna

```python
# polls/views.py (vote function updated)
from django.http import HttpResponseRedirect
from django.shortcuts import get_object_or_404, render
from django.urls import reverse
from .models import Choice, Question

def vote(request, question_id):
    question = get_object_or_404(Question, pk=question_id)
    try:
        selected_choice = question.choice_set.get(pk=request.POST['choice'])
    except (KeyError, Choice.DoesNotExist):
        # Redisplay the question voting form.
        return render(request, 'polls/detail.html', {
            'question': question,
            'error_message': "You didn't select a choice.",
        })
    else:
        selected_choice.votes += 1
        selected_choice.save()
        # Always return an HttpResponseRedirect after successfully dealing
        # with POST data. This prevents data from being posted twice if a
        # user hits the Back button.
        return HttpResponseRedirect(reverse('polls:results', args=(question.id,)))
```

**Hinglish explanation:** 
- User ke vote ko process karta hai
- Error handling karta hai agar koi choice select nahi ki
- Vote increment karke save karta hai
- POST success ke baad HttpResponseRedirect karta hai double submission se bachne ke liye

### 4.3 Results View Update Karna

```python
# polls/views.py (results view updated)
def results(request, question_id):
    question = get_object_or_404(Question, pk=question_id)
    return render(request, 'polls/results.html', {'question': question})
```

### 4.4 Results Template Create Karna

```html
<!-- polls/templates/polls/results.html -->
<h1>{{ question.question_text }}</h1>

<ul>
{% for choice in question.choice_set.all %}
    <li>{{ choice.choice_text }} -- {{ choice.votes }} vote{{ choice.votes|pluralize }}</li>
{% endfor %}
</ul>

<a href="{% url 'polls:detail' question.id %}">Vote again?</a>
```

**Hinglish explanation:** 
- Results page par choices aur unke votes display karte hain
- `pluralize` filter se grammatically correct display (vote/votes) karte hain

### 4.5 Generic Views Use Karna

```python
# polls/views.py (using generic views)
from django.views import generic

class IndexView(generic.ListView):
    template_name = 'polls/index.html'
    context_object_name = 'latest_question_list'
    
    def get_queryset(self):
        """Return the last five published questions."""
        return Question.objects.order_by('-pub_date')[:5]

class DetailView(generic.DetailView):
    model = Question
    template_name = 'polls/detail.html'

class ResultsView(generic.DetailView):
    model = Question
    template_name = 'polls/results.html'

# vote function remains the same
```

**Hinglish explanation:** 
- Generic views se common patterns implement karna simple ho jata hai
- `ListView` list of objects display karne ke liye
- `DetailView` single object detail display karne ke liye

### 4.6 Generic Views ke Liye URLs Update Karna

```python
# polls/urls.py (updated for generic views)
from django.urls import path
from . import views

app_name = 'polls'
urlpatterns = [
    path('', views.IndexView.as_view(), name='index'),
    path('<int:pk>/', views.DetailView.as_view(), name='detail'),
    path('<int:pk>/results/', views.ResultsView.as_view(), name='results'),
    path('<int:question_id>/vote/', views.vote, name='vote'),
]
```

**Hinglish explanation:** Generic views use karne ke liye URLs ko update kiya hai. Function-based views ki jagah class-based views ke liye `.as_view()` method use karte hain.

## Part 5: Testing

### 5.1 Bug Discovery

```python
# polls/models.py (bug in was_published_recently)
def was_published_recently(self):
    return self.pub_date >= timezone.now() - datetime.timedelta(days=1)
```

**Hinglish explanation:** Is function mein bug hai - ye future dates ke liye bhi `True` return karta hai, jo incorrect hai.

### 5.2 Test Case Create Karna

```python
# polls/tests.py
import datetime
from django.test import TestCase
from django.utils import timezone
from .models import Question

class QuestionModelTests(TestCase):
    def test_was_published_recently_with_future_question(self):
        """was_published_recently() returns False for questions whose pub_date is in the future."""
        time = timezone.now() + datetime.timedelta(days=30)
        future_question = Question(pub_date=time)
        self.assertIs(future_question.was_published_recently(), False)
```

**Hinglish explanation:** Test case create kiya hai jo check karta hai ki future date ke questions ke liye `was_published_recently()` `False` return karta hai ya nahi.

### 5.3 Bug Fix Karna

```python
# polls/models.py (fixed was_published_recently)
def was_published_recently(self):
    now = timezone.now()
    return now - datetime.timedelta(days=1) <= self.pub_date <= now
```

**Hinglish explanation:** Function ko fix kiya hai taki ye sirf past date ke recent questions ke liye `True` return kare, future date ke liye nahi.

### 5.4 More Tests Add Karna

```python
# polls/tests.py (additional tests)
def test_was_published_recently_with_old_question(self):
    """was_published_recently() returns False for questions whose pub_date is older than 1 day."""
    time = timezone.now() - datetime.timedelta(days=1, seconds=1)
    old_question = Question(pub_date=time)
    self.assertIs(old_question.was_published_recently(), False)

def test_was_published_recently_with_recent_question(self):
    """was_published_recently() returns True for questions whose pub_date is within the last day."""
    time = timezone.now() - datetime.timedelta(hours=23, minutes=59, seconds=59)
    recent_question = Question(pub_date=time)
    self.assertIs(recent_question.was_published_recently(), True)
```

**Hinglish explanation:** Additional tests add kiye hain jo different scenarios check karte hain.

### 5.5 View Test Karna

```python
# polls/tests.py (view tests)
from django.urls import reverse

def create_question(question_text, days):
    """
    Create a question with the given `question_text` and published the
    given number of `days` offset to now (negative for questions published
    in the past, positive for questions that have yet to be published).
    """
    time = timezone.now() + datetime.timedelta(days=days)
    return Question.objects.create(question_text=question_text, pub_date=time)

class QuestionIndexViewTests(TestCase):
    def test_no_questions(self):
        """If no questions exist, an appropriate message is displayed."""
        response = self.client.get(reverse('polls:index'))
        self.assertEqual(response.status_code, 200)
        self.assertContains(response, "No polls are available.")
        self.assertQuerysetEqual(response.context['latest_question_list'], [])

    def test_past_question(self):
        """Questions with a pub_date in the past are displayed on the index page."""
        create_question(question_text="Past question.", days=-30)
        response = self.client.get(reverse('polls:index'))
        self.assertQuerysetEqual(
            response.context['latest_question_list'],
            ['<Question: Past question.>']
        )

    def test_future_question(self):
        """Questions with a pub_date in the future aren't displayed on the index page."""
        create_question(question_text="Future question.", days=30)
        response = self.client.get(reverse('polls:index'))
        self.assertContains(response, "No polls are available.")
        self.assertQuerysetEqual(response.context['latest_question_list'], [])

    def test_future_question_and_past_question(self):
        """Even if both past and future questions exist, only past questions are displayed."""
        create_question(question_text="Past question.", days=-30)
        create_question(question_text="Future question.", days=30)
        response = self.client.get(reverse('polls:index'))
        self.assertQuerysetEqual(
            response.context['latest_question_list'],
            ['<Question: Past question.>']
        )

    def test_two_past_questions(self):
        """The questions index page may display multiple questions."""
        create_question(question_text="Past question 1.", days=-30)
        create_question(question_text="Past question 2.", days=-5)
        response = self.client.get(reverse('polls:index'))
        self.assertQuerysetEqual(
            response.context['latest_question_list'],
            ['<Question: Past question 2.>', '<Question: Past question 1.>']
        )
```

**Hinglish explanation:** View testing ke liye test cases add kiye hain. Different scenarios test karte hain jaise ki no questions, past questions, future questions, etc.

### 5.6 Test ko Run Karna

```bash
# Run tests
python manage.py test polls
```

### 5.7 View Logic ko Improve Karna

```python
# polls/views.py (improved get_queryset)
def get_queryset(self):
    """
    Return the last five published questions (not including those set to be
    published in the future).
    """
    return Question.objects.filter(
        pub_date__lte=timezone.now()
    ).order_by('-pub_date')[:5]
```

**Hinglish explanation:** `get_queryset` method ko improve kiya hai taki sirf published questions (future questions nahi) display hon.

### 5.8 DetailView ko Future Questions se Protect Karna

```python
# polls/views.py (DetailView update)
class DetailView(generic.DetailView):
    model = Question
    template_name = 'polls/detail.html'
    
    def get_queryset(self):
        """
        Excludes any questions that aren't published yet.
        """
        return Question.objects.filter(pub_date__lte=timezone.now())
```

**Hinglish explanation:** DetailView ko bhi update kiya hai taki future questions ko access na kiya ja sake.

## Part 6: Static Files

### 6.1 Static Directory Create Karna

```
polls/
    static/
        polls/
            style.css
            images/
                background.png
```

### 6.2 CSS File Create Karna

```css
/* polls/static/polls/style.css */
li a {
    color: green;
}

body {
    background: white url("images/background.png") no-repeat;
}
```

**Hinglish explanation:** Simple CSS file create kiya hai jo links ko green color karta hai aur background image set karta hai.

### 6.3 Template mein Static Files Include Karna

```html
<!-- polls/templates/polls/index.html (updated) -->
{% load static %}

<link rel="stylesheet" type="text/css" href="{% static 'polls/style.css' %}">

<!-- Rest of the template remains same -->
```

**Hinglish explanation:** `{% load static %}` se static files load karte hain aur `{% static %}` tag se static file ka path get karte hain.

## Part 7: Admin Interface Customization

### 7.1 Admin Form Customization

```python
# polls/admin.py
from django.contrib import admin
from .models import Question, Choice

class ChoiceInline(admin.TabularInline):
    model = Choice
    extra = 3

class QuestionAdmin(admin.ModelAdmin):
    fieldsets = [
        (None,               {'fields': ['question_text']}),
        ('Date information', {'fields': ['pub_date'], 'classes': ['collapse']}),
    ]
    inlines = [ChoiceInline]

admin.site.register(Question, QuestionAdmin)
```

**Hinglish explanation:** 
- `ChoiceInline` se related Choices ko inline edit kar sakte hain
- `fieldsets` se fields ko groups mein organize karte hain
- `classes: ['collapse']` se date section collapsible ho jata hai

### 7.2 List Display Customize Karna

```python
# polls/admin.py (updated)
class QuestionAdmin(admin.ModelAdmin):
    # ... previous code ...
    list_display = ('question_text', 'pub_date', 'was_published_recently')
    list_filter = ['pub_date']
    search_fields = ['question_text']
```

**Hinglish explanation:** 
- `list_display` se questions list mein multiple columns dikhate hain
- `list_filter` se side filter panel add karte hain
- `search_fields` se search box add karte hain

### 7.3 Admin Look and Feel Customize Karna

```python
# polls/admin.py (was_published_recently customization)
class Question(models.Model):
    # ... previous code ...
    
    def was_published_recently(self):
        now = timezone.now()
        return now - datetime.timedelta(days=1) <= self.pub_date <= now
    was_published_recently.admin_order_field = 'pub_date'
    was_published_recently.boolean = True
    was_published_recently.short_description = 'Published recently?'
```

**Hinglish explanation:** 
- `admin_order_field` se column ko sortable banate hain
- `boolean` se value ko icon ke form mein dikhate hain
- `short_description` se column header text customize karte hain

### 7.4 Admin Template Override Karna

```
mysite/
    templates/
        admin/
            base_site.html
```

```html
<!-- mysite/templates/admin/base_site.html -->
{% extends "admin/base.html" %}

{% block title %}{% if subtitle %}{{ subtitle }} | {% endif %}{{ title }} | Polls Admin{% endblock %}

{% block branding %}
<h1 id="site-name"><a href="{% url 'admin:index' %}">Polls Administration</a></h1>
{% endblock %}
```

**Hinglish explanation:** Admin template override karke branding customize kar sakte hain.

### 7.5 Admin Template Path Add Karna

```python
# mysite/settings.py
TEMPLATES = [
    {
        'BACKEND': 'django.template.backends.django.DjangoTemplates',
        'DIRS': [BASE_DIR / 'templates'],  # Add this path
        'APP_DIRS': True,
        'OPTIONS': {
            # ... other options ...
        },
    },
]
```

**Hinglish explanation:** Project-level templates ko Django ko batate hain taki wo override templates ko use kar sake.

## Part 8: Reusable Apps

### 8.1 Package Karne ke Liye Project Structure

```
polls/
    __init__.py
    admin.py
    apps.py
    migrations/
        __init__.py
    models.py
    static/
        polls/
            ...
    templates/
        polls/
            ...
    tests.py
    urls.py
    views.py
```

### 8.2 setup.cfg File Create Karna

```ini
# setup.cfg
[metadata]
name = django-polls
version = 0.1
description = A Django app to conduct Web-based polls.
long_description = file: README.rst
url = https://www.example.com/
author = Your Name
author_email = yourname@example.com
license = BSD-3-Clause
classifiers =
    Environment :: Web Environment
    Framework :: Django
    Framework :: Django :: X.Y
    Intended Audience :: Developers
    License :: OSI Approved :: BSD License
    Operating System :: OS Independent
    Programming Language :: Python
    Programming Language :: Python :: 3
    Programming Language :: Python :: 3 :: Only
    Programming Language :: Python :: 3.8
    Programming Language :: Python :: 3.9
    Topic :: Internet :: WWW/HTTP
    Topic :: Internet :: WWW/HTTP :: Dynamic Content

[options]
include_package_data = true
packages = find:
python_requires = >=3.8
install_requires =
    Django >= X.Y
```

**Hinglish explanation:** Configuration file hai jo package ke metadata define karta hai.

### 8.3 pyproject.toml File Create Karna

```toml
# pyproject.toml
[build-system]
requires = ['setuptools>=42']
build-backend = 'setuptools.build_meta'
```

**Hinglish explanation:** Build system ki requirements define karta hai.

### 8.4 MANIFEST.in File Create Karna

```
# MANIFEST.in
include LICENSE
include README.rst
recursive-include polls/static *
recursive-include polls/templates *
recursive-include docs *
```

**Hinglish explanation:** Package mein kaun se additional files include karne hain ye batata hai.

### 8.5 README.rst aur LICENSE Files Create Karna

```
# README.rst
=====
Polls
=====

Polls is a Django app to conduct Web-based polls. For each
question, visitors can choose between a fixed number of answers.

Detailed documentation is in the "docs" directory.

Quick start
-----------

1. Add "polls" to your INSTALLED_APPS setting like this::

    INSTALLED_APPS = [
        ...
        'polls',
    ]

2. Include the polls URLconf in your project urls.py like this::

    path('polls/', include('polls.urls')),

3. Run ``python manage.py migrate`` to create the polls models.

4. Start the development server and visit http://127.0.0.1:8000/admin/
   to create a poll (you'll need the Admin app enabled).

5. Visit http://127.0.0.1:8000/polls/ to participate in the poll.
```

**Hinglish explanation:** Documentation jo package ke use karne ke instructions provide karta hai.

### 8.6 Package ko Build Karna

```bash
# Build package
python -m build
```

**Hinglish explanation:** Built package `dist/` directory mein create hoga.

### 8.7 Package ko Install aur Uninstall Karna

```bash
# Install package
python -m pip install --user django-polls/dist/django-polls-0.1.tar.gz

# Uninstall package
python -m pip uninstall django-polls
```

**Hinglish explanation:** Package ko install aur uninstall k
