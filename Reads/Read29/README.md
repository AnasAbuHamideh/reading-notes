# Django Custom User Model
Django ships with a built-in User model for authentication and if you'd like a basic tutorial on how to implement log in, log out, sign up and so on see the Django Login and Logout tutorial for more.

However, for a real-world project, the official Django documentation highly recommends using a custom user model instead. This provides far more flexibility down the line so, as a general rule, always use a custom user model for all new Django projects.

But how to implement one? The official documentation example is not actually what many Django experts recommend using. There is a far easier yet still powerful approach to starting off new Django projects with a custom user model which I'll demonstrate here.

Setup
To start, create a new Django project from the command line. We need to do several things:

create and navigate into a dedicated directory called accounts for our code install Django make a new Django project called django_project make a new app accounts start the local web server Here are the commands to run:

> cd onedrive\desktop\code
> mkdir pages
> cd pages
> python -m venv .venv
> .venv\Scripts\Activate.ps1
> python -m pip install django~=4.0.0
> django-admin startproject django_project .
> python manage.py startapp accounts
> python manage.py runserver

AbstractUser vs AbstractBaseUser
There are two modern ways to create a custom user model in Django: AbstractUser and AbstractBaseUser. In both cases we can subclass them to extend existing functionality however AbstractBaseUser requires much, much more work. So we'll use AbstractUser which actually subclasses AbstractBaseUser but provides more default configuration.

Custom User Model
Creating our initial custom user model requires four steps:

update django_project/settings.py create a new CustomUser model create new UserCreation and UserChangeForm update the admin In settings.py we'll add the accounts app and use the AUTH_USER_MODEL config to tell Django to use our new custom user model in place of the built-in User model. We'll call our custom user model CustomUser.

Within INSTALLED_APPS add accounts at the bottom. Then at the bottom of the entire file, add the AUTH_USER_MODEL config.

Superuser
It's helpful to create a superuser that we can use to log in to the admin and test out log in/log out. On the command line type the following command and go through the prompts.

> python manage.py createsuperuser
Conclusion
Now that our custom user model is configured you can easily and at any time add additional fields to it. See the Django docs for further instructions.

You can also check out DjangoX, which is an open-source Django starter framework that includes a custom user model, email/password by default instead of username/email/password, social authentication, and more.