2407131936

Status: #idea

Tags: [[Django]] [[Python]] 

# url re_path()

URL paths can use regular expressions to match complex patterns, such as a specific date or an integer of a specific length.

```python
re_path(
    r"^blog/(?P<year>[0-9]{4})/(?P<slug>[\w-]+)/$",
    views.blog_post
),
```


---
# References

[[Understand Django]]