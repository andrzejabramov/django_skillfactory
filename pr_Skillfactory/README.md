1. Создаем проект Django
```commandline
django-admin startproject project
```
2. Переходим в директорию проекта
3. Запускаем сервер проекта
```commandline
python manage.py runserver
```
4. Создаем БД
```commandline
python manage.py migrate
```
5. Создаем суперюзера:
```commandline
python manage.py createsuperuser
```
6. Заходим в админку
http://127.0.0.1:8000/admin/
7. В settings.py переменную INSTALLED_APPS добавляем приложения:
```
    "django.contrib.sites",
    "django.contrib.flatpages",
```
8. Ниже переменной INSTALLED_APPS добавляем переменную 

SITE_ID = 1

9. Обновляем миграцию для добавления в БД объектов этих приложений
10. В переменную MIDDLEWARE добавляем строку 
```
    "django.contrib.flatpages.middleware.FlatpageFallbackMiddleware" 
```
11. Переходим в файл url.py: 
в from django.urls import path добпавляем include
12. В переменную urlpatterns добавляем значение:
```commandline
    path('pages/', include('django.contrib.flatpages.urls')),
```
13. Заходим в админку и в поле Flat pages жмем плюсик Add. 
Добавляем /about/, в поле title пишем Hello from Django, в Content: Привет от Skillfactory,
в Sites: atotx.su, сохраняем
14. Чтобы эта страница заработала - создадим папку templates в директории с manage.py
15. В директории templates создаем директорию flatpages с файлом default.html
16. Переходим в файл settinds.py и в переменной TEMPLATES по ключу 'DIRS' прописываем путь к шаблонам:
```
os.path.join(BASE_DIR, 'templates')
```
при этом должен автоматом добавиться import os.path
17. 