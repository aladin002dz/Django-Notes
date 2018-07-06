# Django Notes
These notes are taken from [Traversy Media Course](https://www.youtube.com/watch?v=D6esTdOLXh4).

## 1- Install python with pip(the package manager for python, npm of python).
## 2- Verify python and pip are correctelly installed:
```
$ python --version
$ python 2.7.4
$ pip --version
$ pip 9.0.1 from c:\python27\lib\sites-packages (python 2.7)
```
## 3- Install "Virtual Environment":
```
$ pip install virtualenvwrapper-win
```
## 4- Go to your Django projects folder:
```
$ cd \django\projects
```
## 5- Create Virtual Environment:
```
C:\django\projects>mkvirtualenv py1
```
## 6- Install Django:
```
(py1) C:\django\projects>pip install django
```
## 7- Start project:
```
$ django-admin startproject djangoproject
```
### 8- Run the server
```
$ cd djangoproject
$ python manage.py runserver
```
it should give a message that it is running on "http://127.0.0.1:8000"
and on the browser: 
  
![alt text](https://github.com/aladin002dz/Django-Notes/blob/master/welcome.png "welcome django page")

## 9- Install MySql Client:  
```
$ pip install mysqlclient
```
## 10- Create an app:
Create "posts" app for example
```
$ python manage.py startapp posts
```
## 11- Create Templates Folder:
- under the app folder "Posts", create a folder "templates" and under this folder create a folder "posts".
- udpate views file views.py under the app folder:
```py
# -*- coding: utf-8 -*-
from __future__ import unicode_literals

from django.shortcuts import render
from django.http import HttpResponse

# Create your views here.
def index(request):
    #return HttpResponse('Hello from Posts')
    return render(request, 'posts/index.html', {
        'title': 'Latest Posts'
    })
```
- Create layout.html under templates folder:
```html
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>AladinStudio Blog</title>
    <!-- Compiled and minified CSS -->
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/materialize/1.0.0-rc.2/css/materialize.min.css">
</head>
<body>
    <header class="container center-align">
        <h1>AladinStudio Blog</h1>
    </header>
    <div class="container">
        {% block content %}
        {% endblock %}
    </div>
</body>
</html>
```
- Create index.html under templates folder:
```py
{% extends 'posts/layout.html' %}

{% block content %}
<h3 class="center-align red lighten-3">{{title}}</h3>
{% endblock %}
```
- update urls.py under the app folder:
```py
from django.conf.urls import url
from . import views

urlpatterns = [
    url(r'^$', views.index, name='index')
];
```
- update urls.py under djangoproject
```py
from django.conf.urls import url, include
from django.contrib import admin

urlpatterns = [
    url(r'^admin/', admin.site.urls),
    url(r'^posts/', include('posts.urls'))
]
```
![alt text](https://github.com/aladin002dz/Django-Notes/blob/master/Template.png "django template page")
## 12-Create Model:
in the file models.py
```py
# -*- coding: utf-8 -*-
from __future__ import unicode_literals

from django.db import models
from datetime import datetime

# Create your models here.
class Posts(models.Model):
    title = models.CharField(max_length=200)
    body = models.TextField()
    created_at = models.DateTimeField(default=datetime.now, blank=True)
```
## 13-Create Migration:
```
$ C:\django\projects\djangoproject\python manage.py makemigrations posts
```
## 14-Add Model to Database:
```
$ C:\django\projects\djangoproject\python manage.py migrate
```

                                         ** [Code](https://github.com/bradtraversy/djangocrashcourse) **
