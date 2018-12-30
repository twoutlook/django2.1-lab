=====================================
Writing your first Django app, part 2
=====================================

.. admonition:: References:

  https://docs.djangoproject.com/en/2.1/intro/tutorial02/
    
  
2-1. Migrate
==================

Lab::

    (venv)$ python manage.py migrate 
    (venv)$ python manage.py createsuperuser
    (venv)$ python manage.py runserver
    *** Use browser to visit 127.0.0.1:8000/admin

.. note::
    For beginner or rapid local development, use default database.

.. warning::
    Consider python manage.py shell as another topic

 
    
2. Start Project and Run Development Server
==================

Lab::

    (venv)$ django-admin startproject mysite
    (venv)$ cd mysite
    (venv)$ python manage.py runserver
    *** Use browser to visit 127.0.0.1:8000

.. note::
    You should see a rocket on the page.

    
3. Start App and Maintain View and URLs
==================

Lab::

    $ python manage.py startapp polls . 
    *** edit mysite/urls.py
        add path('polls/', include('polls.urls')), above or below path('admin/', admin.site.urls),
        add include to the line from django.urls import path
    
    *** new polls/urls.py
        from django.urls import path
        from . import views

        urlpatterns = [
            path('', views.index, name='index'),
        ]
    
    *** add def index to polls/views.py
        from django.http import HttpResponse    
        def index(request):
            return HttpResponse("Hello, world. You're at the polls index.")

    
    (venv)$ python manage.py runserver
    *** browser, visit 127.0.0.1:8000/polls
    
    

.. note::
    To ensure App is working.

.. warning::
    Be aware 127.0.0.1:8000 is damaged!





