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
## 11-Create Model:
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





