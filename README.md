# python_django_commands

python3 -m pip install Django
django-admin startproject <my_project_name>
python3 manage.py runserver
python3 manage.py startapp <name_of_my_app>

Inside the app folder, go to views.py and paste the following code

```
from django.shortcuts import render
from django.http import HttpResponse

# Create your views here.


def index(request):
    return HttpResponse('This works!')

```

Inside the app folder, create a urls.py file and paste the following code (it's just an example so change it accordingly)

```
from django.urls import path
from . import views

urlpatterns = [
    path("january", views.index)
]
```
Navigate to the project's urls.py file and make sure the code looks like the following.

```
from django.contrib import admin
from django.urls import path, include

urlpatterns = [
    path('admin/', admin.site.urls),
    path('challenges/', include("challenges.urls"))
]
```

How to make the app's (by app I mean the subproject) urls dynamic.
First, navigate to the specific app's urls.py and make sure the code looks like the following.
```
from django.urls import path
from . import views

urlpatterns = [
    path("<month>", views.monthly_challenge)
]
```

Then go to the specific app's views.py and change the code to the following.
```
from django.shortcuts import render
from django.http import HttpResponse, HttpResponseNotFound

# Create your views here.


def monthly_challenge(request, month):
    data = None
    if month == 'january':
        data = 'Eat no meat for the entire month!'
        return HttpResponse(data)
    elif month == 'february':
        data = "Walk for at least 20 minutes every day!"
        return HttpResponse(data)
    elif month == 'march':
        data = "Learn Django for at least 20 minutes every day!"
        return HttpResponse(data)
    else:
        return HttpResponseNotFound("Can't find the url!")
```

Note that monthly_challenge takes in "month" as the second parameter. It has to be the same as the value in the brackets.



