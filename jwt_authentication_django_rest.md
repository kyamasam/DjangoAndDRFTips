## How to set up jwt in django rest using simplejwt

### Install SimpleJWT

```
pip install djangorestframework_simplejwt
```

### Add the following to settings.py

```
REST_FRAMEWORK = {
    'DEFAULT_AUTHENTICATION_CLASSES': [
        'rest_framework_simplejwt.authentication.JWTAuthentication',
    ],
}
```

### In your urls.py

```
from django.urls import path
from rest_framework_simplejwt import views as jwt_views

urlpatterns = [
    # Other Urls...
    path('api/token/', jwt_views.TokenObtainPairView.as_view(), name='token_obtain_pair'),
    path('api/token/refresh/', jwt_views.TokenRefreshView.as_view(), name='token_refresh'),
]
```

### Setting token expiry times
#### Add the following in your settings.py
```
SIMPLE_JWT = {
    'ACCESS_TOKEN_LIFETIME': timedelta(hours=4),
    'REFRESH_TOKEN_LIFETIME': timedelta(days=14),
}
```


### Note that this is a minimal tutorial. For More Information, visit:

[SimpleJWTGit](https://github.com/jazzband/djangorestframework-simplejwt)
[SimpleIsBetterThanComplex](https://simpleisbetterthancomplex.com/tutorial/2018/12/19/how-to-use-jwt-authentication-with-django-rest-framework.html)