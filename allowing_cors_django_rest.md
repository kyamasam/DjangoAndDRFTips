## How To Allow Cors In DjangoRest

### Install the app from pip
```
pip install django-cors-headers

```

### Add it to installed apps

```
INSTALLED_APPS = [
    ...
    'corsheaders',
    ...
]

```
Make sure you add the trailing comma or you might get a ModuleNotFoundError


### Add the following middleware classes to listen in on responses
```
MIDDLEWARE = [
    ...
    'corsheaders.middleware.CorsMiddleware',
    'django.middleware.common.CommonMiddleware',
    ...
]
```
These should be added as high as possible

### Note that this is a minimal tutorial. To view the full guide, visit [this page](https://pypi.org/project/django-cors-headers/)