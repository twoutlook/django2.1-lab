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


    *** edit polls/static/polls/style.css
    *** add polls/templates/base.html
    *** edit polls/templates/index.html
    *** edit polls/templates/detail.html
    *** edit polls/templates/results.html
    (venv)$ python manage.py test

* polls/static/polls/style.css::


    body{
      margin-top: 12px;
    }

    li a {
        color: black;
    }


* polls/templates/base.html::


    {% load static %}
    <!doctype html>
    <html lang="en">
      <head>
        <!-- Required meta tags -->
        <meta charset="utf-8">
        <meta name="viewport" content="width=device-width, initial-scale=1, shrink-to-fit=no">

        <!-- Bootstrap CSS -->
        <link rel="stylesheet" href="https://stackpath.bootstrapcdn.com/bootstrap/4.2.1/css/bootstrap.min.css" integrity="sha384-GJzZqFGwb1QTTN6wy59ffF1BuGJpLSa9DkKMp0DgiMDm4iYMj70gZWKYbI706tWS" crossorigin="anonymous">
        <link rel="stylesheet" type="text/css" href="{% static 'polls/style.css' %}">
        <title>Lab</title>
      </head>
      <body>
        <div class="container">
          <h1><a href='/polls/'>Django2.1 Tutotrial Lab</a></h1>
              <div class="row">
                <div class="col-md-8">
                {% block content %}
                {% endblock %}
                </div>
            </div>
        </div>
        <!-- Optional JavaScript -->
        <!-- jQuery first, then Popper.js, then Bootstrap JS -->
        <script src="https://code.jquery.com/jquery-3.3.1.slim.min.js" integrity="sha384-q8i/X+965DzO0rT7abK41JStQIAqVgRVzpbzo5smXKp4YfRvH+8abtTE1Pi6jizo" crossorigin="anonymous"></script>
        <script src="https://cdnjs.cloudflare.com/ajax/libs/popper.js/1.14.6/umd/popper.min.js" integrity="sha384-wHAiFfRlMFy6i5SRaxvfOCifBUQy1xHdJ/yoi7FRNXMRBu5WHdZYu1hA6ZOblgut" crossorigin="anonymous"></script>
        <script src="https://stackpath.bootstrapcdn.com/bootstrap/4.2.1/js/bootstrap.min.js" integrity="sha384-B0UglyR+jN6CkvvICOB2joaf5I4l3gm9GU6Hc1og6Ls7i6U/mkkaduKaBhlAXv9k" crossorigin="anonymous"></script>
      </body>
    </html>

        
* polls/templates/index.html::


    {% extends 'polls/base.html' %}
    {% block content %}

    {% if latest_question_list %}
      <h3><ul>
      {% for question in latest_question_list %}
        <li><a href="{% url 'polls:detail' question.id %}">{{ question.question_text }}</a></li>
      {% endfor %}
    </ul></h3>
    {% else %}
      <p>No polls are available.</p>
    {% endif %}
    {% endblock %}
  
        
* polls/templates/detail.html::


    {% extends 'polls/base.html' %}
    {% block content %}
    <h3>{{ question.question_text }}</h3>

    {% if error_message %}<p><strong>{{ error_message }}</strong></p>{% endif %}

    <form action="{% url 'polls:vote' question.id %}" method="post">
    {% csrf_token %}
    {% for choice in question.choice_set.all %}
        <input type="radio" name="choice" id="choice{{ forloop.counter }}" value="{{ choice.id }}">
        <label for="choice{{ forloop.counter }}">{{ choice.choice_text }}</label><br>
    {% endfor %}
    <input class='btn btn-success' type="submit" value="Vote">
    </form>
    {% endblock %}

* polls/templates/results.html::


    {% extends 'polls/base.html' %}
    {% block content %}
    <h2>{{ question.question_text }}</h2>

    <ul>
    {% for choice in question.choice_set.all %}
        <li>{{ choice.choice_text }} -- {{ choice.votes }} vote{{ choice.votes|pluralize }}</li>
    {% endfor %}
    </ul>

    <a class='btn btn-success' href="{% url 'polls:detail' question.id %}">Vote again?</a>
    {% endblock %}

.. figure:: _static/img6-1-1.png
    :align: center
    
.. figure:: _static/img6-1-2.png
    :align: center
    
.. figure:: _static/img6-1-3.png
    :align: center
    


.. warning::
    You might need to 'Clear Browsing Data' to let css working during development.
 

 

 
 
