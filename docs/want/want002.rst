===============
To understand Django
===============


Prepare envrionment to study Django::

    $ pwd
    /Users/pinglingchen/ksndjs/django001/django
    $ ls
    django
    $ cd django
    $ git remote -v
    origin	https://github.com/twoutlook/django.git (fetch)
    origin	https://github.com/twoutlook/django.git (push)
    $ cd ..
    $ ls
    django
    $ python3.6 -m venv venv
    $ . venv/bin/activate
    (venv) $ pip freeze
    (venv) $ pip install -e django
    Obtaining file:///Users/pinglingchen/ksndjs/django001/django/django
    Collecting pytz (from Django==2.2.dev20190102231945)
      Using cached https://files.pythonhosted.org/packages/f8/0e/2365ddc010afb3d79147f1dd544e5ee24bf4ece58ab99b16fbb465ce6dc0/pytz-2018.7-py2.py3-none-any.whl
    Collecting sqlparse (from Django==2.2.dev20190102231945)
      Using cached https://files.pythonhosted.org/packages/65/85/20bdd72f4537cf2c4d5d005368d502b2f464ede22982e724a82c86268eda/sqlparse-0.2.4-py2.py3-none-any.whl
    Installing collected packages: pytz, sqlparse, Django
      Running setup.py develop for Django
    Successfully installed Django pytz-2018.7 sqlparse-0.2.4
    You are using pip version 10.0.1, however version 18.1 is available.
    You should consider upgrading via the 'pip install --upgrade pip' command.
    (venv) $ pip freeze
    -e git+https://github.com/twoutlook/django.git@b5fe97a34ea527d4254b58c2e828450e7c32157f#egg=Django
    pytz==2018.7
    sqlparse==0.2.4
    You are using pip version 10.0.1, however version 18.1 is available.
    You should consider upgrading via the 'pip install --upgrade pip' command.
    (venv) $ 
