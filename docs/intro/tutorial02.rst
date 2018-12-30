=====================================
Writing your first Django app, part 2
=====================================

.. admonition:: References:

  https://docs.djangoproject.com/en/2.1/intro/tutorial02/
    
  
2-1. Make Django Admin Available
==================

Lab::

    (venv)$ python manage.py migrate 
    (venv)$ python manage.py createsuperuser
    (venv)$ python manage.py runserver
    *** Use browser to visit 127.0.0.1:8000/admin

.. note::
    For beginner or rapid local development, use default database.
    
    You should see AUTHENTICATION AND AUTHORIZATION and your newly created user.

.. warning::
    Consider python manage.py shell as another topic. 

 
    
2-2. Create Models 
==================

Lab::

    *** edit poll/models.py
    (venv)$ python manage.py makemigrations
    (venv)$ python manage.py migrate
    (venv)$ python manage.py runserver
    *** Use browser to visit 127.0.0.1:8000/admin

* polls/models.py::


    from django.db import models


    class Question(models.Model):
        question_text = models.CharField(max_length=200)
        pub_date = models.DateTimeField('date published')


    class Choice(models.Model):
        question = models.ForeignKey(Question, on_delete=models.CASCADE)
        choice_text = models.CharField(max_length=200)
        votes = models.IntegerField(default=0)


.. note::
     You should see POLLS and Questions and Choices
   
2-3. Add App to Settings and Make Script
==================

Lab::

    *** edit mysite/settings.py
    *** edit go.py


* mysite/settings.py
.. code-block:: python
    :caption: mysite/settings.py

    INSTALLED_APPS = [
      'polls',
      'django.contrib.admin',
      ...
    
* go.py   
.. code-block:: python
    :caption: mysite/go.py
    python manage.py makemigrations
    python manage.py migrate
    python manage.py runserver
 
 
 go.py::

    python manage.py makemigrations
    python manage.py migrate
    python manage.py runserver
 

2-4. Maintain Poll's Admin
==================

Lab::

    *** edit poll/admin.py


* polls/admin.py
.. code-block:: python
    :caption: polls/admin.py
    
  from django.contrib import admin

  from .models import Question,Choice

  admin.site.register(Question)
  admin.site.register(Choice)

.. warning::
    Be aware there's different approach, not exactly as official tutorial.


2-5. Go
==================

Lab::

    (venv)$ . go

.. note::
    From right now, whenever you maintain model, Ctrl+C to stop server and source go to run again with database ready.
