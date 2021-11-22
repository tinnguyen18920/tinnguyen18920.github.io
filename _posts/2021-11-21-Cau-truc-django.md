---
title: Cấu trúc thư mục một project Django
date: 2021-11-21 10:57:00 PM
last_modified_at: 2021-11-22 07:19:00 AM
description: Cấu trúc yêu thích thư mục một project Django hiện tại.
tags: django python
caterogry: programming

---

Cấu trúc thư mục yêu thích hiện khi bắt đầu một project Django: tách `settings`, `apps`, ... thành các module riêng. Quan điểm cá nhân sau khi thực hiện theo cấu trúc này thì:
- Phân biệt các cấu hình giữa môi trường (development, production, test)
- Dễ dàng tùy chỉnh các apps cần dùng cho môi trường development như `django-debug-toolbar`

Còn nhược điểm thì ..., để sau.

Cấu trúc của project sau khi thực thi lênh `django-admin startproject` và `django-admin startapp`
```
project
| manage.py
| backend
|   __init__.py
|   asgi.py
|   settings.py
|   wsgi.py
|   urls.py
| app
|   __init__.py
|   admin.py
|   apps.py
|   models.py
|   views.py
|   tests.py
| requirements.txt

```

Ta sẽ tiến hành thay đổi cấu trúc như sau:
```
project
| manage.py
| backend
|   __init__.py
|   asgi.py
|   apps
|     api
|       __init__.py
|       admin.py
|       apps.py
|       models.py
|       views.py
|       tests
|         __init__.py
|         views.py
|         models.py
|   settings
|     __init__.py
|     base.py
|     development.py
|     production.py
|   wsgi.py
|   urls.py
| requirements
|   base.txt
|   development.txt
|   production.txt
|   test.txt
```

Sau đó thì có vài điều cần chỉnh sửa lại:

```diff
Các chỉnh sửa cho file cấu hình base.py
- BASE_DIR = Path(__file__).resolve().parent.parent.parent
+ BASE_DIR = Path(__file__).resolve().parent.parent.parent.parent

INSTALLED_APPS = [
    ...
-   "api"
+   "backend.apps.api"
]

Khi startapp thì chỉnh sửa apps.py

class ApiConfig(AppConfig):
    default_auto_field = "django.db.models.BigAutoField"
-   name = "api"
+   name = "backend.apps.api"


urlpatterns = [
-   path("api/", include("api.urls")),
+   path("api/", include("backend.apps.api.urls"))
]

```
