## How to generate automatic documentation for your api

### Install recommended plugins

```
pip install Pygments

```

```
pip install Markdown
```

### Add the docs route in urlconf

```
from rest_framework.documentation import include_docs_urls

urlpatterns = [
    ...
    path('docs/', include_docs_urls(title='My API title'))
]
```

### Documenting views
#### Including docs strings in your views 
```
class UserList(generics.ListAPIView):
    """
    Return a list of all the existing users.
    """
```
#### To document each view, use:
```
class UserList(generics.ListCreateAPIView):
    """
    get:
    Return a list of all the existing users.

    post:
    Create a new user instance.
    """
```

### This is a short guide for adding docs to your djangorest API. To view more information visit the official [site](https://www.django-rest-framework.org/coreapi/from-documenting-your-api/)