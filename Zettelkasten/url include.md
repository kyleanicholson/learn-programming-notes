2407131938

Status: #idea

Tags: [[Django]] [[Python]] 

# url include()

*The use of `include` gives each Django app autonomy in what views it needs to define. The project can be blissfully “ignorant” of what the application is doing.*

Instead of manually specifying subpaths, you can use `include()` to handle routes to a  sub-application's urls, which are defined within that application's directory.

```python
# project/urls.py
from django.urls import include, path

urlpatterns = [
    path(
        "workouts/",
        include("workouts.urls"),
    ),
    path(
        "exercises/",
        include("exercises.urls"),
    ),
]

```

```python
# schools/urls.py
from django.urls import path
from workouts import views

urlpatterns = [
    path("", views.index),
    path(
        "<int:workout_id>/",
        views.workout_detail
    ),
]
```

---
# References

https://www.mattlayman.com/understand-django/urls-lead-way/