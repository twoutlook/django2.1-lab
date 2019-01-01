=====================================
Writing your first Django app, part 3
=====================================

* Django Getting started, `part 3 <https://docs.djangoproject.com/en/2.1/intro/tutorial03/>`_
* Read The Docs, `part 3 <https://django21-tutorial-lab.readthedocs.io/en/latest/intro/tutorial03.html>`_
  

    
3-1. Polls Index 
==================

Lab::

    *** edit polls/views.py
    *** add polls/templates/polls/index.html



* polls/views.py::

    from django.shortcuts import render
    from .models import Question

    def index(request):
        latest_question_list = Question.objects.order_by('-pub_date')[:5]
        context = {'latest_question_list': latest_question_list}
        return render(request, 'polls/index.html', context)
        
        
* polls/templates/polls/index.html::

    {% if latest_question_list %}
      <ul>
      {% for question in latest_question_list %}
        <li><a href="/polls/{{ question.id }}/">{{ question.question_text }}</a></li>
      {% endfor %}
      </ul>
    {% else %}
      <p>No polls are available.</p>
    {% endif %} 
        

.. figure:: _static/img3-1-1.png
    :align: center
    
.. figure:: _static/img3-1-2.png
    :align: center
 

.. note::
    Admin vs. customized page. 
 

3-2. Polls Detail 
==================

Lab::

    *** edit polls/urls.py
    *** edit polls/views.py
    *** add polls/templates/polls/index.html

* polls/views.py::

    from django.urls import path
    from . import views

    urlpatterns = [
      path('', views.index, name='index'),
      path('<int:question_id>/', views.detail, name='detail')
    ]


* polls/views.py::

    from django.shortcuts import render,get_object_or_404
    from .models import Question

    def index(request):
        latest_question_list = Question.objects.order_by('-pub_date')[:5]
        context = {'latest_question_list': latest_question_list}
        return render(request, 'polls/index.html', context)

    def detail(request, question_id):
        question = get_object_or_404(Question, pk=question_id)
        return render(request, 'polls/detail.html', {'question': question})

        
        
* polls/templates/polls/index.html::

    <h1>{{ question.question_text }}</h1>
    <ul>
    {% for choice in question.choice_set.all %}
        <li>{{ choice.choice_text }}</li>
    {% endfor %}
    </ul>
        

.. figure:: _static/img3-2-1.png
    :align: center
    
.. figure:: _static/img3-2-2.png
    :align: center
 

.. note::
    Admin vs. customized page. 
 

 

 
 