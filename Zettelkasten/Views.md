2407131923

Status: #idea

Tags: [[Python]], [[Django]]

# Views

Views in Django are pieces of code that take a request as an argument and return a response. Views can be associated with a specific url in urls.py, and url parameters can be passed as arguments to the view. Views can be either class-based or function-based.

```python
from django.http import (
    HttpRequest,
    HttpResponse
)

def some_view(
    request: HttpRequest
) -> HttpResponse:
    return HttpResponse('Hello World')
```


---
# References
https://www.mattlayman.com/understand-django/urls-lead-way/