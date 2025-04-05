## Phele setting wale file me jane ka fir usme jo variable hai usme dheko kya variable hai jaise

-Installed Apps(Overview of differnet default app present){some of these app use at least one database table}
-Middleware
-Databases

- Notice we use sqllite, we can change it too

- Adjust Time_zone to **Asia/Kolkata** but abhi ke liye **UTC** bhi chalega

- Use migrate command to make table in data base

  ```sh
  py manage.py migrate
  ```

 - agar humlog interested hai to **.tables** command use kar ke tables dhek bhi sakte haii


 - if you don't need all of these installed apps prior to migrating them we could have also commented out the ones we don't need and then those migrations would have been skipped

 - we are also going to work with some additional entries in the database and to create those we need to define our models and a model is basically a database layout

-	that we define so a model is basically a single definite source of information about our data and it contains the essential fields and behavior of the data that we are storing and this also includes migrations so once we define the models we would then create migrations and migrate them to actually create those entries in the database so to make it specific
  
-	-we need for our polls app is a way to keep track of the questions that we want to ask and also of the choices that are available and since these are part of the polls

-now we create two classes

```py
from django.db import models


class Question(models.Model):
    question_text = models.CharField(max_length=200)
    pub_date = models.DateTimeField("date published")


class Choice(models.Model):
    question = models.ForeignKey(Question, on_delete=models.CASCADE)
    choice_text = models.CharField(max_length=200)
    votes = models.IntegerField(default=0)
```

# Remember the three-step guide to making model changes:

### 1 Change your models (in models.py).

### 2 Run [**python manage.py makemigrations**] to create migrations for those changes
  ```text
  By running makemigrations, you’re telling Django that you’ve made some changes to your models (in this case, you’ve made new ones) 
  and that you’d like the changes to be stored as a migration
  ```

### 3 Run [**python manage.py migrate**] to apply those changes to the database.
  ```text
   To make migrations create those model tables in your database. The migrate command takes all the migrations that haven’t been applied
   (Django tracks which ones are applied using a special table in your database called django_migrations)
   and runs them against your database - essentially,
   synchronizing the changes you made to your models with the schema in the database.
  ```

### to invoke the Python shell, use this command:

$ python manage.py shell


# 🛠️ Django Models to Database: Step-by-Step Flow

This table explains how changes in Django models are translated into database updates.

| Step | Description                          | Command                        | Output/Effect                                                 |
|------|--------------------------------------|--------------------------------|----------------------------------------------------------------|
| 1️⃣   | **Update Models**                   | _No command_                   | Modify `models.py` (add/edit/delete fields or models).         |
| 2️⃣   | **Create Migrations**               | `python manage.py makemigrations` | Creates migration files (in `migrations/` folder) based on model changes. |
| 3️⃣   | **Apply Migrations to Database**    | `python manage.py migrate`     | Executes the migration files to update the actual database.   |

---

## 🧠 Summary (Analogy)

| Part                | Like in Real Life                     |
|---------------------|----------------------------------------|
| `models.py`         | Blueprint / Design of the building     |
| `makemigrations`    | Approval of blueprint / Planning phase |
| `migrate`           | Construction of the building (actual DB update) |

