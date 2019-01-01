=====================================
Writing your first Django app, part 6
=====================================

* Django Getting started, `part 6 <https://docs.djangoproject.com/en/2.1/intro/tutorial06/>`_
* Django Girls Tutorials, `Template extending <https://tutorial.djangogirls.org/en/template_extending/>`_
* Boostrap v4.2, `Starter template <https://getbootstrap.com/docs/4.2/getting-started/introduction/>`_

* Read The Docs, `part 6 <https://django21-tutorial-lab.readthedocs.io/en/latest/intro/tutorial06.html>`_
  

    
6-1. Test 
==================

Lab::


    *** edit mysite/urls.py
    *** edit polls/tests.py
    *** add polls/templates/index.html
    (venv)$ python manage.py test

* polls/urls.py::

    from django.contrib import admin
    from django.urls import path,include
    from django.views.generic import TemplateView

    urlpatterns = [
        path('admin/', admin.site.urls),
        path('polls/', include('polls.urls')),
        path('', TemplateView.as_view(template_name="index.html"),name='index'),
    ]


* polls/tests.py::

    from django.test import TestCase
    from django.utils import timezone
    from django.urls import reverse
    import datetime

    from .models import Question

    class QuestionModelTests(TestCase):

        def test_was_published_recently_with_future_question(self):
            """
            was_published_recently() returns False for questions whose pub_date
            is in the future.
            """
            time = timezone.now() + datetime.timedelta(days=30)
            future_question = Question(pub_date=time)
            self.assertIs(future_question.was_published_recently(), False)

        def test_hello_world(self):
            response = self.client.get(reverse('index'))
            self.assertEqual(response.status_code, 200)
            self.assertContains(response, "Hello World!")        


        
* polls/templates/index.html::

    Hello World!
        


.. figure:: _static/img6-1-1.png
    :align: center
    
.. figure:: _static/img6-1-2.png
    :align: center
.. figure:: _static/img6-1-3.png
    :align: center
 

.. note::
    Fix / with 'Hello World!' using CBV.
 

 

 
 
