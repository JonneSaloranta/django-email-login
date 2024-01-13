# How to use this project

## .env

```python
SECRET_KEY=djan
DEBUG=True
```

## Settings.py

```
INSTALLED_APPS = [
    ...

    'custom_login',
    'email_login',

]
```

```python
from decouple import config
```

```python
SECRET_KEY = config("SECRET_KEY")

DEBUG = config("DEBUG", default=False, cast=bool)
```

```python
AUTH_USER_MODEL = 'email_login.User'
```

```python
STATIC_URL = 'static/'
STATIC_ROOT = BASE_DIR / 'staticfiles'
STATICFILES_DIRS = [
    BASE_DIR / 'static',
]

MEDIA_URL = '/media/'
MEDIA_ROOT = BASE_DIR / 'uploads'
```

## core/urls.py

```python
from django.contrib import admin
from django.urls import path, include
from django.conf import settings
from django.conf.urls.static import static

urlpatterns = [
    path('admin/', admin.site.urls),
    path('', include('custom_login.urls')),
] + static(settings.MEDIA_URL, document_root=settings.MEDIA_ROOT)

```
