# 🚀 Django Starter Template

A minimal Django project boilerplate to kickstart your development quickly.

## 📌 Setup & Installation

Follow these steps to get started with the Django Starter Template:

### 1️⃣ Create and Activate Virtual Environment
```bash
python -m venv venv
source venv/bin/activate  # For macOS/Linux
venv\Scripts\activate     # For Windows
```

### 2️⃣ Install Django
```bash
pip install django
```

### 3️⃣ Create Django Project & Start App
```bash
django-admin startproject project .
python manage.py startapp home
```

### 4️⃣ Run Initial Migrations
```bash
python manage.py migrate
```

### Start the Development Server
```bash
python manage.py runserver
```
Now, open your browser and go to **`http://127.0.0.1:8000/`** 🎉

---

## 📁 Project Structure
```bash
project/
│-- manage.py
│-- project/
│   │-- __init__.py
│   │-- settings.py
│   │-- urls.py
│   │-- wsgi.py
│   │-- asgi.py
│-- home/
│   │-- __init__.py
│   │-- views.py
│   │-- urls.py
│   │-- templates/
│   │   │-- home/
│   │       │-- index.html
│   │-- static/
│   │   │-- home/
│   │       │-- style.css
```

---

## 📜 File Explanations

### 🔹 `manage.py`
Django's command-line utility for administrative tasks.

### 🔹 `project/settings.py`
- Configures installed apps, middleware, database settings, static files, etc.
- **Templates & Static Settings:**
  ```python
  TEMPLATES = [
      {
          'BACKEND': 'django.template.backends.django.DjangoTemplates',
          'DIRS': [BASE_DIR / 'home/templates'],
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
  STATICFILES_DIRS = [BASE_DIR / 'home/static']
  ```

### 🔹 `project/urls.py`
```python
from django.contrib import admin
from django.urls import path, include
from django.conf import settings
from django.conf.urls.static import static
from django.contrib.auth import views as auth_views
# from exam import views as auth_view
admin.site.site_header = 'Dashboard'                    # default: "Django Administration"
admin.site.index_title = 'Admin Panel'                   # default: "Site administration"
admin.site.site_title = 'Sajid Admin Panel'               # default: "Django site admin"
urlpatterns = [
    path('admin/', admin.site.urls),
    path('', include('home.urls')),

    path('ckeditor/', include('ckeditor_uploader.urls')),
] + static(settings.MEDIA_URL, document_root=settings.MEDIA_ROOT)
urlpatterns  += static(settings.STATIC_URL,document_root=settings.STATIC_ROOT)

```

### 🔹 `home/views.py`
```python
from django.shortcuts import render

def index(request):
    return render(request, 'home/index.html')
```

### 🔹 `home/urls.py`
```python
from django.urls import path
from .views import index

urlpatterns = [
    path('', index, name='home'),
]
```

### 🔹 `home/templates/home/index.html`
A simple homepage:
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Home</title>
    <link rel="stylesheet" href="/static/home/style.css">
</head>
<body>
    <h1>Welcome to Django Starter Template</h1>
</body>
</html>
```

### 🔹 `home/static/home/style.css`
Basic styling:
```css
body {
    font-family: Arial, sans-serif;
    background-color: #f4f4f4;
    text-align: center;
}
```

---

## 🛠 GitHub Setup

### 1️⃣ Initialize Git & Add Remote
```bash
git init
git remote add origin https://github.com/YOUR-USERNAME/django-starter-template.git
```

### 2️⃣ Push Your Code
```bash
git add .
git commit -m "Initial commit"
git branch -M main
git push -u origin main
```

---

## 🎯 Summary
✅ Minimal Django setup
✅ Pre-configured URLs & templates
✅ Static & template settings included
✅ Ready-to-use boilerplate for future projects

Enjoy coding with Django! 🚀
