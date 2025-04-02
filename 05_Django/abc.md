# Django Polls App Tutorial (Hinglish मे समझाया गया)

## परिचय (Introduction)

Ye Django documentation ka famous "Polls" application tutorial hai, jisme users questions ko vote kar sakte hain. Is tutorial mein hum ek complete poll application banayenge jisme:

1. Public site jahan users polls dekh aur vote kar sakte hain
2. Admin site jahan polls add, change aur delete kar sakte hain

## Project Structure

```
mysite/
    manage.py
    mysite/
        __init__.py
        settings.py
        urls.py
        asgi.py
        wsgi.py
    polls/
        __init__.py
        admin.py
        apps.py
        migrations/
            __init__.py
            0001_initial.py
        models.py
        static/
            polls/
                style.css
                images/
                    background.png
        templates/
            polls/
                index.html
                detail.html
                results.html
        tests.py
        urls.py
        views.py
```

## Part 1: Project Setup aur Model Creation

### Project Setup

Sabse pehle, Django install karna hoga aur project create karna hoga:

```bash
pip install django
django-admin startproject mysite
cd mysite
python manage.py startapp polls
```

### Models (models.py)

Ab hum database models define karenge. Polls app mein do models hai:
- Question: ek question aur publication date
- Choice: choice text aur vote count

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

**Code samjhein**: Yahan `Question` model mein ek question ka text aur publication date hai. `Choice` model mein har choice text, votes count, aur related question hai (Foreign Key se). `__str__` method se hum objects ko string mein represent kar sakte hain. `was_published_recently` function check karta hai ki kya question pichle 24 ghanton mein publish hua tha.

### App Registration

```python
# mysite/settings.py (partial)
INSTALLED_APPS = [
    'polls.apps.PollsConfig',
    'django.contrib.admin',
    'django.contrib.auth',
    'django.contrib.contenttypes',
    'django.contrib.sessions',
    'django.contrib.messages',
    'django.contrib.staticfiles',
]
```

### Create Migrations aur Database

```bash
python manage.py makemigrations polls
python manage.py migrate
```

**Hinglish explanation**: `makemigrations` command se Django hamari models ke changes detect karke migrations files create karta hai. `migrate` command in migrations ko execute karke database mein tables create karta hai.

## Part 2: Admin Site

### Create Superuser

```bash
python manage.py createsuperuser
```

### Register Models with Admin

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
        ('Date information', {'fields': ['pub_date']}),
    ]
    inlines = [ChoiceInline]
    list_display = ('question_text', 'pub_date', 'was_published_recently')
    list_filter = ['pub_date']
    search_fields = ['question_text']

admin.site.register(Question, QuestionAdmin)
```

**Code samjhein**: `admin.py` mein hum admin interface ko customize kar rahe hain. `ChoiceInline` se hum Question ke page par hi related Choices add kar sakte hain. `QuestionAdmin` class se hum admin interface mein fields, filtering, searching wagera setup kar rahe hain.

## Part 3: Views aur Templates

### URL Configuration

Pehle project URL configuration update karein:

```python
# mysite/urls.py
from django.contrib import admin
from django.urls import include, path

urlpatterns = [
    path('polls/', include('polls.urls')),
    path('admin/', admin.site.urls),
]
```

Ab polls app ke URLs define karein:

```python
# polls/urls.py
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

**Code samjhein**: Yahan `app_name` se hum namespace define kar rahe hain, taki template mein URL references ko `polls:detail` jaise format mein use kar sakein. URL patterns define karte hain ki konsa URL konse view function ya class ko call karega.

### Views

```python
# polls/views.py
from django.http import HttpResponseRedirect
from django.shortcuts import get_object_or_404, render
from django.urls import reverse
from django.views import generic
from django.utils import timezone

from .models import Choice, Question

class IndexView(generic.ListView):
    template_name = 'polls/index.html'
    context_object_name = 'latest_question_list'
    
    def get_queryset(self):
        """Return the last five published questions (not including those set to be published in the future)."""
        return Question.objects.filter(
            pub_date__lte=timezone.now()
        ).order_by('-pub_date')[:5]

class DetailView(generic.DetailView):
    model = Question
    template_name = 'polls/detail.html'
    
    def get_queryset(self):
        """Excludes any questions that aren't published yet."""
        return Question.objects.filter(pub_date__lte=timezone.now())

class ResultsView(generic.DetailView):
    model = Question
    template_name = 'polls/results.html'

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

**Code samjhein**: Is file mein:
- `IndexView`: Latest questions dikhata hai
- `DetailView`: Question detail page dikhata hai jisme voting kar sakte hain
- `ResultsView`: Vote results dikhata hai
- `vote` function: POST request handle karta hai jab koi vote karta hai

Generic views (`ListView` aur `DetailView`) se boilerplate code kam ho jata hai. `get_queryset` method se hum filter kar rahe hain ki sirf published questions hi dikhayi dein.

### Templates

```html
<!-- polls/templates/polls/index.html -->
{% load static %}

<link rel="stylesheet" type="text/css" href="{% static 'polls/style.css' %}">

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

```html
<!-- polls/templates/polls/detail.html -->
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

**Templates samjhein**: 
- `index.html`: Questions ki list display karta hai
- `detail.html`: Ek question ke details aur voting form dikhata hai
- `results.html`: Voting results dikhata hai

`{% url %}` template tag se URLs generate hote hain, jisse hardcoded URLs ki zaroorat nahi padti.

## Part 4: Static Files (CSS)

```css
/* polls/static/polls/style.css */
li a {
    color: green;
}

body {
    background: white url("images/background.png") no-repeat;
}
```

**CSS samjhein**: Simple styling jisme links green color ke hain aur background mein ek image hai.

## Part 5: Tests

```python
# polls/tests.py
import datetime

from django.test import TestCase
from django.utils import timezone
from django.urls import reverse

from .models import Question

class QuestionModelTests(TestCase):
    def test_was_published_recently_with_future_question(self):
        """was_published_recently() returns False for questions whose pub_date is in the future."""
        time = timezone.now() + datetime.timedelta(days=30)
        future_question = Question(pub_date=time)
        self.assertIs(future_question.was_published_recently(), False)

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

**Tests samjhein**: Yahan hum unit tests likh rahe hain jo check karte hain ki:
1. `was_published_recently()` function sahi se kaam kar raha hai ya nahi
2. Index view sirf past questions dikha raha hai, future questions nahi

## Chalne ke liye Commands

```bash
# Run server
python manage.py runserver

# Admin ke liye (dashboard)
# Browser mein http://127.0.0.1:8000/admin/ kholo

# Polls app dekhne ke liye
# Browser mein http://127.0.0.1:8000/polls/ kholo
```

## Conclusion

Is tutorial mein, humne seekha:
1. Django project aur app kaise create karte hain
2. Models kaise define karte hain
3. Admin site kaise customize karte hain
4. Views aur templates kaise banate hain
5. Static files kaise use karte hain
6. Tests kaise likhte hain

Ye basic polls application create karke aapne Django ke most important concepts ko samajh liya hai. Ab aap is knowledge ko use karke apne own applications develop kar sakte hain.
