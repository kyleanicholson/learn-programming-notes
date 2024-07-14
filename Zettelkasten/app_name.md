2407132016

Status: #idea

Tags: [[Python]], [[Django]]

# app_name

The app_name variable within urls.py allows you to assign a namespace to that app's urls. This helps with url reuse -- for example, in case there are multiple 'index' routes in different parts of the project that are referenced by project views. The `reverse` function ([[url name and reverse()]]) can then be used to call a url from that specific namespace.

```python
# schools/urls.py
from django.urls import path

from schools import views

app_name = "schools"
urlpatterns = [
    path("", views.index, name="index"),
    path(
        "<int:school_id>/",
        views.school_detail,
        name="detail"
    ),
]

# project/views.py
reverse("schools:index") == "/schools/"
```



---
# References
