2407131958

Status: #idea

Tags: [[Django]], [[Python]]

# url name and reverse()

A path can be assigned a 'name' keyword argument, which gives it an independent name (separate from its route) that can be referenced elsewhere in the codebase. `Reverse` is commonly used within a view function to look up a url by its 'name' as specified in urls.py and return its route. This is beneficial in cases when a url is being updated, as the name can still be referenced.
```python
# project/urls.py
from django.urls import path

from blog import views

urlpatterns = [
    ...
    path(
        "/marketing/blog/categories/",
        views.categories,
        name="blog_categories"
    ),
    ...
]
```

```python
# application/views.py
from django.http import (
    HttpResponseRedirect
)
from django.urls import reverse

def old_blog_categories(request):
    return HttpResponseRedirect(
        reverse("blog_categories")
    )
```


---
# References
https://www.mattlayman.com/understand-django/urls-lead-way/
