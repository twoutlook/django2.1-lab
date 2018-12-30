=====================================
Writing your first Django app, part 2
=====================================

.. admonition:: References:

  https://docs.djangoproject.com/en/2.1/intro/tutorial02/
    
  
2-1. Use Django Admin
==================

Lab::

    (venv)$ python manage.py migrate 
    (venv)$ python manage.py createsuperuser
    (venv)$ python manage.py runserver
    *** Use browser to visit 127.0.0.1:8000/admin

.. note::
    For beginner or rapid local development, use default database.

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


.. code-block:: python
    :caption: polls/models.py

    from django.db import models


    class Question(models.Model):
        question_text = models.CharField(max_length=200)
        pub_date = models.DateTimeField('date published')


    class Choice(models.Model):
        question = models.ForeignKey(Question, on_delete=models.CASCADE)
        choice_text = models.CharField(max_length=200)
        votes = models.IntegerField(default=0)


.. note::
    Always consider to maintian Model and Admin together.

   
2-2. Add App to Settings 
==================

Lab::

    *** edit poll/models.py
    (venv)$ python manage.py makemigrations
    (venv)$ python manage.py migrate
    (venv)$ python manage.py runserver
    *** Use browser to visit 127.0.0.1:8000/admin


.. code-block:: python
    :caption: mysite/settings.py

    INSTALLED_APPS = [
      'polls',
      'django.contrib.admin',
      ...


