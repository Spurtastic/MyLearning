---
date: 2024-07-30T20:03
tags:
  - Python
  - django
---
## Django Setup process with tailwind


### Virtual environment setup process

```
conda create --name python django

## you can specify the version like this

conda create --name python=3.5 django=1.11

```

### Creating project in django
```
django-admin startproject project_name_here

cd project_name

python manage.py runserver **note it default starts in debug mode remember to switch it off
```


### Creating an app within the project
So most of the tiny components are managed as apps
how you instantiate them is

```
python manage.py startapp app_name_here
```
### Setting up django-tailwind plug ins

if you havent installed it yet
```
if in base terminal (ideally avoid this)
pip install django-admin

if in conda or venv
python -m pip install django-admin
```

Initiallize then install

```
in settings.py

TAILWIND_APP_NAME = 'theme'

INSTALLED_APPS = [
	# other apps
    'tailwind',
    'theme',
]

```

then in the terminal
```
python manage.py tailwind init

#when they ask for name put theme or anything but remember whatever you name it there will be reflected in the templates
python manage.py tailwind install
```

under urls.py of the mainproj folder
```
path('__reload__/', include('django_browser_reload.urls')),
```

like this

```
from django.contrib import admin
from django.urls import path, include
# from django.conf.urls import include
from myapp import views

urlpatterns = [
    path('tailwindy/', include('myapp.urls')),
    path('admin/', admin.site.urls),
    path('__reload__/', include('django_browser_reload.urls')),
]

```


```
# add this at the top
TEMPLATE_DIR =os.path.join(BASE_DIR,"theme/templates")

# this will be somewhere below in the settings.py file
TEMPLATES = [
    {
        'BACKEND': 'django.template.backends.django.DjangoTemplates',
        'DIRS': [TEMPLATE_DIR,],
        'APP_DIRS': True,
        'OPTIONS': {
            'context_processors': [
                'django.template.context_processors.debug',
                'django.template.context_processors.request',
                'django.contrib.auth.context_processors.auth',
                'django.contrib.messages.context_processors.messages',
            ],
        },
    },
]
```

once all that is done 

have one terminal start

```
python manage.py tailwind start
```

then run another terminal parallel 
```
python manage.py runserver
```
