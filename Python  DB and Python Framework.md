Embedding HTML within Python using web frameworks is the foundation of modern web development with python. Frameworks like Flask and Django allow you to write backend logic in Python while rendering HTML pages that users see in their browser.



Below is a beginner-friendly introduction.



1\. Why HTML Needs to work with python



HTML alone creates static pages. Python frameworks make them dynamic by:

• processing user input(forms, logins)

• Fetching data from databases

• Generating dynamic content

• Handling routing (URLs --> pages)



Example:

Instead of writing 100 static pages for 100 users, python can generate them dynamically using templates.



Basic Flask Example



step 1: Install Flask



pip install flask



step 2: Python File(app.py)



from flask import Flask, render\_template



app = Flask(\_\_name\_\_)



@app.route("/")

def home():

&#x09;name = "Rahul"

&#x09;return render\_template("index.html", username=name)



if\_\_name\_\_ == "\_\_main\_\_":

&#x09;app.run(debug=True)





step 3 : 	HTML template (templates/index.html)



<!DOCTYPE html>

<html>

<head>

&#x20;   <title>Flask Example</title>

</head>

<body>



<h1>Hello {{ username }}!</h1>

<p>Welcome to my Flask website.</p>



</body>

</html>



3\. Embedding HTML Using Django



Django is a full-featured Python web framework with built-in features like authentication, admin panel, and ORM.



it uses the Django Template Language(DTL) to embed Python data into HTML.



Basic Django Template Example



from Django.shortcuts import render



def home(request):

&#x09;context = {

&#x09;    "username" : "Rahul"	

}

return render(request, "index.html", context)



index.html



<!DOCTYPE html>

<html>

<head>

&#x20;   <title>Django Example</title>

</head>

<body>



<h1>Hello {{ username }}</h1>



</body>

</html>



Advantages of Embedding HTML with python



• Allows creation of dynamic web pages

• Separates business logic (python) from presentation(HTML)

• Makes websites easier to maintain and update

• Supports interaction with databases and user input.



Conclusion



Embedding HTML within Python using frameworks like Flask and Django enables developers to build dynamic and interactive web applications. These frameworks use template engines to combine Python logic with HTML, allowing data to be displayed dynamically on web pages while keeping the code organized and maintainable.





•Generating Dynamic HTML Content Using Django Templates.



Generating Dynamic HTML Content Using Django Templates



Generating dynamic HTML content means creating web pages whose content changes automatically based on data, user input, or database information. In the Django framework, this is done using the Django Template System, which allows developers to insert dynamic data into HTML files.



What Are Django Templates?



A Django template is an HTML file that contains special syntax for displaying data passed from Python code (views). The template uses template tags and variables to generate dynamic content.



This system separates:



Backend logic (Python) in views



Frontend layout (HTML) in templates



This separation makes the application easier to maintain and manage.



Passing Data from View to Template



In Django, data is from a view function to an HTML template using a context dictionary.



Example-views.py



from django.shortcuts import render



def home(request):

&#x20;   data = {

&#x20;       "name": "Student",

&#x20;       "course": "Web Development"

&#x20;   }

&#x20;   return render(request, "index.html", data)



Displaying Data in the Template



Inside the HTML template, Django uses double curly braces{{}} to display variables.



index.html



<html>

<body>



<h1>Hello {{ name }}</h1>

<p>Course: {{ course }}</p>



</body>

</html>



when the page loads, Django replaces the variables with actual values from the view.



Output in browser.



Hello student

Course: Web Development



Using Loops in Django Templates



Django templates allow loops to display multiple items dynamically.



def students(request):

&#x20;   data = {

&#x20;       "students": \["Rahul", "Priya", "Amit"]

&#x20;   }

&#x20;   return render(request, "students.html", data)



students.html



<ul>

{% for student in students %}

&#x20;  <li>{{ student }}</li>

{% endfor %}

</ul>



Using Conditional Statements



{% if user %}

&#x20;  <h1>Welcome {{ user }}</h1>

{% else %}

&#x20;  <h1>Please login</h1>

{% endif %}



This allows content to change depending on the situation.



Advantages of Django Templates

• Generates dynamic web pages

• keeps HTML and Python code separate

• Easy to maintain and modify

• Supports loops, conditions, and filters



**CONCLUSION**



**Generating dynamic HTML content using Django templates allows developers to display data dynamically on web pages. By passing data from views to templates and using template syntax such as variables, loops, and conditions, Django makes it easy to create interactive and data-driven websites.**



**LAB :** Write a python program to render an HTML file using Django's template system.



Python Program to Render an HTML File Using Django’s Template System



In the Django framework, HTML files are rendered using the Django template system. A Python view sends data to an HTML template, and Django replaces template variables with actual values to generate dynamic web pages.



Below is a simple program demonstrating how to render an HTML file using Django.



1.Create a View in views.py



from django.shortcuts import render



def home(request):

&#x20;   data = {

&#x20;       "title": "Welcome Page",

&#x20;       "message": "Hello! This page is rendered using Django templates."

&#x20;   }

&#x20;   return render(request, "index.html", data)



2.create the HTML Template



<!DOCTYPE html>

<html>

<head>

&#x20;   <title>{{ title }}</title>

</head>

<body>



<h1>{{ message }}</h1>

<p>This content is generated dynamically using Django.</p>



</body>

</html>



Explanation:



• {{ title }} and {{ message }} are template variables.

• Django replaces them with values provided in the view.



3\. Configure URL in urls.py



from django.urls import path

from . import views



urlpatterns = \[

&#x20;   path('', views.home, name='home'),

]



4\. Output



When the server runs and the pages is opened in the browser. Django renders the HTML template and displays:



Hello! This page is rendered using Django templates.

This content is generated dynamically using Django.



Conclusion:

Django’s template system allows Python programs to render HTML files dynamically by passing data from views to templates, making it easier to build interactive and dynamic web applications.



2\. CSS in python



Theory:



• Integrating CSS with Django templates.



In Django, CSS is integrated with templates using the static files system. CSS files are stored in a static folder, and Django loads them into HTML templates so that web pages can be styled.



CSS helps improve the appearance, layout, colors, and fonts of a web page created using Django templates.



1.Create a Static Folder



project/

│

├── app/

│   ├── templates/

│   │   └── index.html

│   ├── static/

│   │   └── css/

│   │       └── style.css



• templates/ -> stores HTML files

• static/ -> stores CSS, javaScript, and images





2.Create the CSS files



Create a file style.css inside static/css/.



body {

&#x20;   background-color: lightblue;

&#x20;   font-family: Arial;

}



h1 {

&#x20;   color: darkblue;

&#x20;   text-align: center;

}



This CSS file defines styles for the webpage.



3\. Load Static Files in the Django Templates



In the HTML. Template, use Django's static template tag.



index.html



{% load static %}



<!DOCTYPE html>

<html>

<head>

&#x20;   <title>Django CSS Example</title>



&#x20;   <link rel="stylesheet" href="{% static 'css/style.css' %}">

</head>



<body>



<h1>Welcome to Django Website</h1>

<p>This page uses CSS styling.</p>



</body>

</html>



Explanation:



{% load static %} loads Django's static file system.



{% static 'css/style.css' %} tells Django where the CSS file is located.



4\. Configure Static Files in settings.py



Make sure the static URL is defined.



STATIC\_URL = '/static/'



5\. Output



When the webpage runs:



The HTML structure comes from the template.



The CSS file applies styles such as colors, fonts, and layout.



• Conclusion



Integrating CSS with Django templates allows developers to separate design (CSS) from content (HTML) and logic (Python). Using Django’s static file system ensures that stylesheets and other static resources are properly loaded and applied to web pages.


•How to serve static files (like css, javascript) in Django.

1. Configure STATIC_URL

In your settings.py, define the base URL for static files:

STATIC_URL = '/static/'

Tell Django where your static files are stored:

import os

STATICFILES_DIRS = [
    os.path.join(BASE_DIR, 'static'),
]

Create a folder structure like:

project/
    static/
        css/
            style.css
        js/
            script.js

Use {% load static %} in Templates

{% load static %}

4. Link Static Files in Templates

<link rel="stylesheet" href="{% static 'css/style.css' %}">

5. Add django.contrib.staticfiles

INSTALLED_APPS = [
    'django.contrib.staticfiles',
]

6. Serving Static Files in Development

python manage.py runserver

7. (Important for Exams) Production Setup

In production, Django does NOT serve static files directly.

Step 1: Set STATIC_ROOT

STATIC_ROOT = os.path.join(BASE_DIR, 'staticfiles')

Step 2: Run collectstatic

python manage.py collectstatic

Step 3: Use Web Server

Serve static files using:

Nginx

Apache

3. Java script with python.

•Using java script for client-side interactivity in Django templates.

How It Works

•jango sends HTML (via templates) to the browser

•javascript runs in the browser

It interacts with:

• HTML elements.

• User actions (click, input etc.)

•Django data rendered in templates.

1. Add JavaScript in Django Template

<script>
    function showMessage() {
        alert("Hello from Django template!");
    }
</script>

<button onclick="showMessage()">Click Me</button>

2. Use External JavaScript File (Best Practice)

static/js/script.js

function greetUser(name) {
    alert("Hello " + name);
}

Step 2: Load Static in Template

{% load static %}
<script src="{% static 'js/script.js' %}"></script>

<button onclick="greetUser('Student')">Click</button>

3. Pass Django Data to JavaScript

<script>
    var username = "{{ user.username }}";
    console.log("Welcome " + username);
</script>

4. Event Handling Example

<button id="btn">Click Me</button>

<script>
document.getElementById("btn").addEventListener("click", function() {
    alert("Button clicked!");
});
</script>

5. AJAX (Fetch API) with Django

<script>
fetch('/get-data/')
    .then(response => response.json())
    .then(data => {
        console.log(data);
    });
</script>

•Linking external or internal javascript files in Django.

In Django, JavaScript can be included in templates either:

Internally (inside the HTML file), or

Externally (separate .js file using static files)

1. Internal JavaScript (Inline Script)

<!DOCTYPE html>
<html>
<head>
    <title>Internal JS</title>
</head>
<body>

<button onclick="showMessage()">Click Me</button>

<script>
function showMessage() {
    alert("Hello from internal JavaScript!");
}
</script>

</body>
</html>

2. External JavaScript (Recommended)

static/js/script.js

function greet() {
    alert("Hello from external JavaScript!");
}

Step 2: Load Static in Template

{% load static %}

step 3: Link js file

<script src="{% static 'js/script.js' %}"></script>

<button onclick="greet()">Click Me</button>

Linking External JavaScript from CDN

You can also use online JavaScript libraries (like Bootstrap, jQuery).

<script src="https://code.jquery.com/jquery-3.6.0.min.js"></script>


4. Django introduction

•Overview of Django: Web development framework.

Introduction

Django is a high-level, open-source web development framework written in Python. It enables developers to build secure, scalable, and maintainable web applications quickly.

Key Features of Django

1. Rapid Development

Provides built-in tools and libraries

Reduces development time

2. Architecture (MVT Pattern)

Django follows MVT (Model-View-Template) architecture:

Model → Handles database

View → Contains business logic

Template → Manages UI (HTML)

3. Security

Django protects against:

SQL Injection

Cross-Site Scripting (XSS)

Cross-Site Request Forgery (CSRF)

4. Built in admin panel

• Automatic generated admin panel face
• Easy database management

5. ORM (Object Relational Mapping)

Interacts with database using Python code

No need to write raw SQL

6. scalability

Suitable for small to large applications

Used by popular websites

• Advantages of Django (e.g., Scalability , security)

Django is a powerful Python web framework known for its simplicity, speed, and robust features. It provides many built-in advantages that make web development efficient and secure.

1.Scalability

Django can handle high traffic and large applications

Used by big platforms like Instagram and Pinterest

Supports scaling from small projects to enterprise-level apps

2.Security

Protects against common attacks:

SQL Injection

Cross-Site Scripting (XSS)

Cross-Site Request Forgery (CSRF)

Has built-in authentication system

Secure password hashing

3. Rapid development

Built-in features reduce coding time

Developers can build applications quickly

Follows DRY (Don’t Repeat Yourself) principle

4. Clean and Organized Structure

Uses MVT architecture (Model-View-Template)

Separates logic, data, and UI

Makes code easy to maintain

5. Built-in Admin Panel

Automatically generated admin interface

Easy database management without extra coding

6. Powerful ORM

Interacts with databases using Python instead of SQL

Supports multiple databases like MySQL, PostgreSQL, SQLite

7. Versatility

Can be used for:

Websites

APIs

CMS

E-commerce platforms

8. Large Community Support

Extensive documentation

Many third-party packages available

Active developer community

9. Reusability

Components and apps can be reused

Reduces development effort

• Django vs flask Comparison : which to choose and why.

Django and Flask are both popular Python web frameworks, but they differ significantly in their approach and use cases. Django is a high-level, full-featured framework that comes with built-in tools such as an admin panel, authentication system, and ORM, making it ideal for large-scale, complex applications where security, scalability, and rapid development are important. On the other hand, Flask is a lightweight and minimal framework that provides only the essential components, giving developers more flexibility and control to choose their own tools and structure. While Django follows a structured approach using the MVT architecture, Flask is more flexible and suitable for small projects, APIs, or applications where simplicity is preferred. Therefore, Django is generally chosen for large, secure, and feature-rich web applications, whereas Flask is preferred for smaller projects, microservices, or when developers want greater customization and simplicity.

5. Virtual environment

• Understanding  the importance of a virtual environment in python projects.

A virtual environment in Python is an isolated workspace that allows developers to install and manage project-specific dependencies without affecting the global Python installation. Its importance lies in preventing conflicts between different projects that may require different versions of the same libraries. By using a virtual environment, each project maintains its own set of packages, ensuring consistency, stability, and easier debugging. It also makes collaboration more efficient, as developers can replicate the exact environment using a requirements file. Overall, virtual environments help in maintaining clean project organization, avoiding dependency issues, and ensuring that applications run reliably across different systems.

• Using  venv or virtualenv to create isolated environments.

In Python, isolated environments can be created using tools like **`venv`** (built-in module) or **`virtualenv`** (third-party package) to manage project-specific dependencies separately. The `venv` module is included with Python (version 3.3 and above) and allows developers to create a lightweight virtual environment using a simple command like `python -m venv env`, which generates a folder containing a separate Python interpreter and libraries. On the other hand, `virtualenv` is an external tool that offers similar functionality but with additional features and compatibility with older Python versions. After creating the environment, it must be activated (`source env/bin/activate` on Linux/Mac or `env\Scripts\activate` on Windows), allowing packages to be installed locally using `pip` without affecting the global environment. This approach ensures better dependency management, avoids version conflicts, and keeps Python projects clean and portable.


6. Project and app creation.

• Steps to create a Django project and individual apps within the project

To create a Django project, first ensure that Django is installed and a virtual environment is activated. Then, use the command `django-admin startproject projectname` to create a new project. This generates a project folder containing important files like `settings.py`, `urls.py`, and `manage.py`. Navigate into the project directory using `cd projectname`, and run the development server with `python manage.py runserver` to verify that the project is set up correctly. To create an individual app within the project, use the command `python manage.py startapp appname`, which creates a separate module with files such as `models.py`, `views.py`, and `apps.py`. After creating the app, it must be registered in the `INSTALLED_APPS` list inside `settings.py` so Django can recognize it. Finally, apps can be connected to the project by defining URLs and creating views and templates, allowing the developer to build modular and organized web applications within a single Django project.

• Understanding the role of manage.py,urls.py and views.py.

In a Django project, manage.py, urls.py, and views.py play essential roles in the functioning of the application. The manage.py file is a command-line utility that allows developers to interact with the Django project by running tasks such as starting the development server, applying migrations, and creating apps. The urls.py file acts as a URL dispatcher, mapping web addresses (URLs) to specific views, thereby determining which part of the application should handle a user’s request. The views.py file contains the core logic of the application, where functions or classes process incoming requests, interact with models if needed, and return responses such as HTML pages or JSON data. Together, these components ensure smooth handling of requests and responses, forming the backbone of a Django web application.

7. MVT pattern Architecture.

• Django’s MVT (Model-View-Template) architecture and how it handles request-response cycles.

Django follows the MVT (Model–View–Template) architecture, which helps in organizing code by separating concerns. The Model represents the data layer and defines the structure of the database using Python classes. The View acts as the business logic layer, processing user requests, interacting with the model, and deciding what data should be sent to the template. The Template is responsible for the presentation layer, handling how the data is displayed to the user using HTML along with Django Template Language. When a user sends a request (such as accessing a webpage), Django first matches the URL through urls.py, which directs the request to the appropriate view. The view processes the request, retrieves or modifies data using the model if necessary, and then passes the data to a template. The template renders the final HTML page, which is sent back as a response to the user’s browser. This structured flow ensures clean code organization, better maintainability, and efficient handling of web requests in Django applications.

8. Django Admin panel

• Introduction of built in Django admin panel.

The built-in Django Admin Panel is a powerful feature provided by Django that allows developers to manage application data through a user-friendly web interface without writing additional code. It is automatically created when a Django project is set up and can be accessed by creating a superuser using the `python manage.py createsuperuser` command and logging into the `/admin` URL. The admin panel is tightly integrated with Django’s models, meaning that once a model is registered in `admin.py`, it automatically provides options to add, update, delete, and view records in the database. It also includes features like search, filtering, authentication, and user management. This makes it extremely useful for developers and administrators to efficiently handle backend data operations, test applications, and maintain content without needing a separate interface.

• Customizing the Django admin interface to manage database records.

Django provides a highly customizable admin interface that allows developers to efficiently manage database records according to application needs. After registering a model in admin.py, customization can be done by creating a class that extends ModelAdmin. This allows control over how data is displayed and managed in the admin panel. Developers can specify fields to display in the list view using list_display, add search functionality with search_fields, and enable filtering using list_filter. Additionally, fields can be grouped or ordered using fieldsets and ordering, improving usability for administrators. Inline models can also be used to edit related data on the same page. These customizations make the admin panel more organized, user-friendly, and efficient for handling large amounts of data, ultimately enhancing the overall management of database records in a Django application.

9. URL patterns and template integration

• Setting up URL patterns in urls.py for routing requests to views.

In Django, URL patterns are defined in the urls.py file to map incoming web requests to the appropriate views, enabling proper routing within the application. This is done using a list called urlpatterns, where each URL pattern is associated with a specific view function or class. The path() function is commonly used to define routes by specifying the URL path and the corresponding view. For example, a URL like path('home/', views.home) directs requests for /home/ to the home view in views.py. Django processes each incoming request by checking these patterns in order and selecting the first match. Additionally, projects can include multiple apps by using the include() function, allowing modular URL management. This structured routing system ensures that user requests are efficiently directed to the correct logic, forming a crucial part of Django’s request-response cycle.

• Integrating templates with views  to render dynamic HTML content.

In Django, templates are integrated with views to generate dynamic HTML content that is sent to the user’s browser. The view acts as a bridge between the data and the presentation layer by processing the request and passing relevant data to the template. This is typically done using the render() function, which takes the request, the template file, and a context dictionary containing data. The template then uses Django Template Language (DTL) to display this data dynamically using variables, loops, and conditional statements. For example, a view can send user information or database records to a template, which then renders them into HTML for display. This integration allows developers to separate business logic from presentation, making the application more organized, maintainable, and capable of delivering dynamic content based on user interactions or database data.

10. Form validation using javascript.

• Using javascript for fron-end form validation.

JavaScript is widely used for front-end form validation to ensure that user inputs meet the required criteria before being sent to the server. It operates on the client side, providing immediate feedback to users by checking fields such as empty inputs, correct email format, password strength, and valid numeric values. This is typically implemented using event listeners like onsubmit or addEventListener, where a validation function is triggered when the user attempts to submit the form. If any input is invalid, JavaScript prevents form submission and displays appropriate error messages, allowing users to correct their data instantly. This approach improves user experience, reduces server load, and enhances data accuracy by catching errors early in the process.


11. Django Database Connectivity (MySQL or SQLite)

• Connecting Django to a database (SQLite or MySQL).

Django provides built-in support for connecting to databases such as SQLite and MySQL, making it easy to store and manage application data. By default, Django uses SQLite, a lightweight file-based database, which requires no additional setup and is configured automatically in the settings.py file under the DATABASES section. For more scalable applications, developers often use MySQL, which requires installing a database connector (such as mysqlclient) and updating the database configuration in settings.py with details like database name, user, password, host, and port. After configuring the database, Django’s ORM (Object Relational Mapping) is used to interact with it using Python code instead of SQL. Finally, commands like python manage.py makemigrations and python manage.py migrate are executed to create and apply database tables. This setup allows Django applications to efficiently handle data storage, retrieval, and management.


•Using Django ORM for database queries.

Django’s ORM (Object Relational Mapping) allows developers to interact with the database using Python code instead of writing raw SQL queries. It works by mapping database tables to Python classes called models, enabling easy creation, retrieval, updating, and deletion of data. Using the ORM, developers can perform queries such as fetching all records with Model.objects.all(), filtering specific data using filter(), retrieving a single object with get(), and ordering results with order_by(). It also supports complex queries, relationships (like foreign keys), and aggregation functions. This approach improves code readability, reduces the chances of SQL errors, and enhances security by protecting against SQL injection. Overall, Django ORM simplifies database operations and makes them more efficient and maintainable.

12. ORM and QuerySets

• Understanding Django’s ORM and how QuerySets are used to interact with the database.

Django’s ORM (Object Relational Mapping) is a powerful feature that allows developers to interact with the database using Python objects instead of writing raw SQL queries. In this system, database tables are represented as models, and operations such as creating, retrieving, updating, and deleting records are performed using Python methods. A key component of the ORM is the QuerySet, which is a collection of database queries used to retrieve data from the database. QuerySets are lazy, meaning they are not executed until the data is actually needed, which improves performance. Developers can use QuerySets to filter data (filter()), retrieve single objects (get()), order results (order_by()), and perform aggregations. They can also be chained together to create complex queries in a readable and efficient way. Overall, QuerySets provide a flexible and efficient interface for interacting with the database, making Django ORM both powerful and easy to use.


13. Django forms and Authentication.

Django provides built-in support for handling forms and user authentication, making it easier to develop secure and interactive web applications. Django Forms are used to collect and validate user input efficiently. They can be created using forms.Form or forms.ModelForm, allowing developers to define fields, apply validation rules, and render HTML forms automatically. Forms also handle data cleaning and error reporting, ensuring that only valid data is processed.

On the other hand, Django Authentication is a built-in system that manages user accounts, including features like login, logout, password management, and user registration. It provides models such as User, along with authentication functions to verify credentials and control access to different parts of the application. Developers can restrict access to certain views using decorators like login_required. Together, Django Forms and Authentication help in securely collecting user data and managing user identity, making web applications more robust, user-friendly, and secure.

•Using Django's built-in form handling.

Django’s built-in form handling system simplifies the process of creating, validating, and processing forms in web applications. It allows developers to define forms using Python classes (forms.Form or forms.ModelForm), where fields and validation rules are specified. When a user submits a form, Django automatically handles data binding and validation using methods like is_valid(), ensuring that the input meets the required criteria. If the data is valid, it can be processed or saved to the database; otherwise, error messages are displayed back in the template. The render() function is used to display forms in HTML templates, and Django Template Language helps in easily rendering form fields and errors. This built-in system reduces the need for manual validation, improves code organization, and ensures secure and efficient handling of user input in Django applications.


• Implementing Django’s authentication system (sign up, login, logout, password management).

Implementing authentication in Django is straightforward because it comes with a powerful built-in system in Django. Below is a clean, practical guide covering signup, login, logout, and password management.

 1. Setup Django Authentication

Django already includes authentication apps. Ensure these are in your settings.py:

INSTALLED_APPS = [
    'django.contrib.admin',
    'django.contrib.auth',
    'django.contrib.contenttypes',
    'django.contrib.sessions',
    'django.contrib.messages',
    'django.contrib.staticfiles',
]

 2. User Signup (Registration)

# forms.py
from django.contrib.auth.forms import UserCreationForm
from django.contrib.auth.models import User

class RegisterForm(UserCreationForm):
    class Meta:
        model = User
        fields = ['username', 'email', 'password1', 'password2']

3. Login System

# urls.py
from django.contrib.auth import views as auth_views

urlpatterns = [
    path('login/', auth_views.LoginView.as_view(template_name='login.html'), name='login'),
]

4. Logout System

# urls.py
path('logout/', auth_views.LogoutView.as_view(), name='logout'),

5. Protecting Views (Authentication Required)

from django.contrib.auth.decorators import login_required

@login_required
def dashboard(request):
    return render(request, 'dashboard.html')

6. Password Management

urlpatterns = [
    path('password_change/', auth_views.PasswordChangeView.as_view(), name='password_change'),
    path('password_change_done/', auth_views.PasswordChangeDoneView.as_view(), name='password_change_done'),

    path('password_reset/', auth_views.PasswordResetView.as_view(), name='password_reset'),
    path('password_reset_done/', auth_views.PasswordResetDoneView.as_view(), name='password_reset_done'),

    path('reset/<uidb64>/<token>/', auth_views.PasswordResetConfirmView.as_view(), name='password_reset_confirm'),
    path('reset_done/', auth_views.PasswordResetCompleteView.as_view(), name='password_reset_complete'),
]

14. CRUD operations using AGEX.

• Using AJAX for making asynchronous requests to the server without reloading the page.

Using AJAX (Asynchronous JavaScript and XML) allows your web page to communicate with the server in the background—so you can update parts of the page without a full reload. This is widely used with Django to build smooth, modern web apps.

<button onclick="loadData()">Load Data</button>
<div id="result"></div>

<script>
function loadData() {
    fetch('/get-data/')
    .then(response => response.json())
    .then(data => {
        document.getElementById('result').innerHTML = data.message;
    })
    .catch(error => console.log(error));
}
</script>

Back end Django view.

from django.http import JsonResponse

def get_data(request):
    return JsonResponse({'message': 'Hello from Django!'})

URL

from django.urls import path
from . import views

urlpatterns = [
    path('get-data/', views.get_data),
]

SENDING DATA TO SERVER (POST REQUEST)

function sendData() {
    fetch('/post-data/', {
        method: 'POST',
        headers: {
            'Content-Type': 'application/json',
            'X-CSRFToken': getCSRFToken()
        },
        body: JSON.stringify({
            name: "John"
        })
    })
    .then(res => res.json())
    .then(data => console.log(data));
}

Django view

import json
from django.http import JsonResponse

def post_data(request):
    if request.method == 'POST':
        data = json.loads(request.body)
        return JsonResponse({'received': data['name']})

CSRF Token (Important in Django)

function getCSRFToken() {
    return document.cookie.split('; ')
        .find(row => row.startsWith('csrftoken'))
        .split('=')[1];
}


15. customizing the Django admin panel 

Customizing the Django admin panel is one of the fastest ways to turn a basic backend into a powerful, user-friendly dashboard. The built-in admin in Django is highly extensible—you can tweak everything from how data is displayed to how it behaves.

1. Basic model registration

# admin.py
from django.contrib import admin
from .models import Item

admin.site.register(Item)

2. Custom model admin class

# admin.py
class ItemAdmin(admin.ModelAdmin):
    list_display = ('name', 'description')
    search_fields = ('name',)
    list_filter = ('name',)

admin.site.register(Item, ItemAdmin)

3. Improve list view (Better UI)

class ItemAdmin(admin.ModelAdmin):
    list_display = ('name', 'created_at')
    list_editable = ('name',)
    ordering = ('-created_at',)
    list_per_page = 10

4. Customizing forms in admin

Customizing the Django admin panel in Django lets you turn the default backend into a powerful, clean, and role-specific management interface. Below are the most important techniques—ranging from basic tweaks to advanced customization.

1. Custom ModelAdmin (Core Customization)

# admin.py
from django.contrib import admin
from .models import Item

@admin.register(Item)
class ItemAdmin(admin.ModelAdmin):
    list_display = ('name', 'created_at', 'status')
    search_fields = ('name',)
    list_filter = ('status',)
    ordering = ('-created_at',)

2. Improve list View UX

class ItemAdmin(admin.ModelAdmin):
    list_display = ('name', 'status')
    list_editable = ('status',)
    list_per_page = 20
    date_hierarchy = 'created_at'

3. Customize Forms Layout

class ItemAdmin(admin.ModelAdmin):
    fields = ('name', 'status', 'description')

Group fields

class ItemAdmin(admin.ModelAdmin):
    fieldsets = (
        ('Basic Info', {
            'fields': ('name', 'status')
        }),
        ('Extra Details', {
            'fields': ('description',),
            'classes': ('collapse',)
        }),
    )

4. Inline models

# models.py
class Comment(models.Model):
    item = models.ForeignKey(Item, on_delete=models.CASCADE)
    text = models.TextField()

# admin.py
class CommentInline(admin.TabularInline):
    model = Comment
    extra = 1

class ItemAdmin(admin.ModelAdmin):
    inlines = [CommentInline]

5.Search & Filtering Enhancements

class ItemAdmin(admin.ModelAdmin):
    search_fields = ('name', 'description')
    list_filter = ('status', 'created_at')


6. Permissions & Access Control

class ItemAdmin(admin.ModelAdmin):
    def has_add_permission(self, request):
        return request.user.is_superuser

    def has_delete_permission(self, request, obj=None):
        return False

7. Custom Admin Actions

def mark_published(modeladmin, request, queryset):
    queryset.update(status='published')

class ItemAdmin(admin.ModelAdmin):
    actions = [mark_published]

8. Override Save/Delete Behavior

class ItemAdmin(admin.ModelAdmin):
    def save_model(self, request, obj, form, change):
        obj.updated_by = request.user
        super().save_model(request, obj, form, change)

9. Customize admin UI

admin.site.site_header = "My Company Admin"
admin.site.site_title = "Dashboard"
admin.site.index_title = "Welcome Panel"

10. Add custom CSS/JS

class ItemAdmin(admin.ModelAdmin):
    class Media:
        css = {
            'all': ('css/admin.css',)
        }
        js = ('js/admin.js',)

11. custom templates

templates/admin/base_site.html
templates/admin/change_list.html

12. Readonly fields

class ItemAdmin(admin.ModelAdmin):
    readonly_fields = ('created_at',)


16. Payment integration using paytm'

• Introduction to integrating payment gateways (like Paytm) in Django projects.

Integrating a payment gateway into a Django project allows your application to securely accept online payments via cards, UPI, wallets, or net banking. Gateways like Paytm act as a bridge between your app and financial institutions.

17. Git hub project deploy ment

Prerequisites

Make sure you have:

Git installed → Git

A GitHub account → GitHub

Your Django project ready

1. Navigate to Your Project Folder

cd path/to/your/django-project

2. Initialize Git Repository

git init

3. Create a .gitignore File (Important!)

touch .gitignore

Add this content

__pycache__/
*.pyc
db.sqlite3
.env
venv/
.env/
*.log
staticfiles/
media/

4. Add files to git

git add .

5. Commit your code

git commit -m "Initial commit - Django project"

6. Create a Repository on GitHub

Go to GitHub

Click New Repository

Give it a name (e.g., django-payment-app)

Click Create Repository

7. Connect Local Repo to GitHub

git remote add origin https://github.com/your-username/your-repo-name.git

8. Push code to GitHub

git branch -M main
git push -u origin main


18. Live project deployment

• Introduction to deploying Django projects to live servers like PythonAnywhere.

Introduction to Deploying Django Projects (PythonAnywhere Example)

Deploying a Django project means making it accessible on the internet so users can visit your app through a URL instead of running it locally. Platforms like PythonAnywhere make this process beginner-friendly by handling servers, networking, and much of the configuration for you.


What Does “Deployment” Mean?

When you deploy a Django app:

Your code moves from your local machine → a live server

The server runs your Django project continuously

Users can access it via a domain (e.g., yourname.pythonanywhere.com)

Basic Deployment Workflow

1. Upload Your Project

You can:

Upload via GitHub (recommended)

Or upload files manually

Example (using Git):

git clone https://github.com/your-username/your-django-project.git

Basic Deployment Workflow

1. Upload Your Project

You can:

Upload via GitHub (recommended)

Or upload files manually

Example (using Git):

git clone https://github.com/your-username/your-django-project.git

2. Set up virtual environment

mkvirtualenv myenv --python=python3.10
pip install django
pip install -r requirements.txt

3. Configure Django settings

update settings.py:

•Add your domain:

ALLOWED_HOSTS = ['yourusername.pythonanywhere.com']

• Set static files:

STATIC_ROOT = os.path.join(BASE_DIR, 'staticfiles')

4. Configure Web App on PythonAnywhere

In the dashboard:

• Go to Web tab

• Click Add a new web app

• Choose:
	• domain name:
	• Django version:


5. Link your Django project

Edit the WSGI configuration file:

import sys
path = '/home/yourusername/your-project-folder'
if path not in sys.path:
    sys.path.append(path)

from django.core.wsgi import get_wsgi_application
application = get_wsgi_application()

6. Apply Migration 

python manage.py migrate

7. Collect static files

python manage.py collectstatic

8. Reload the web

Important Consideration

• DEBUG = False in production
• keep secret keys safe
• Use environment variable for sensitive data
• Configure static & media files properly

Testing your live app

After deployment:

• Visit your URL
• Test forms, login, payments (if any)
• Check error logs in pythonAnywhere

19. Social Authentication

Social login integration in Django allows users to authenticate using third-party platforms such as Google, Facebook, and GitHub instead of creating a new account manually. This is typically implemented using the OAuth2 (Open Authorization 2.0) protocol, which enables secure access to user information without exposing their passwords to the application. In a Django project, social authentication is commonly handled using libraries like django-allauth, which simplifies the integration process. The setup involves registering the application with each provider to obtain a Client ID and Client Secret, configuring these credentials in the Django admin panel, and adding the necessary apps and authentication backends in the settings file. When a user selects a social login option, they are redirected to the provider’s authentication page, where they grant permission. After successful authentication, the provider sends user details back to the Django application through a callback URL, and the user is automatically logged in. This approach enhances user experience, improves security, and reduces the need for managing passwords within the application.


20. Google Maps API

• Integrating Google Maps API into Django projects.

Integrating the Google Maps API into Django projects allows developers to add location-based features such as maps, markers, directions, and geolocation services within a web application. The Google Maps API provides a set of tools that enable embedding interactive maps and accessing geographic data. To integrate it into a Django project, the developer must first obtain an API key from the Google Cloud Platform by enabling the required Maps services. This API key is then included in the frontend template, typically within a script tag, to load the Google Maps JavaScript API. In Django, views are used to pass location data (such as latitude and longitude) to templates, where the map is rendered using JavaScript. Developers can customize the map by adding markers, info windows, and routes based on dynamic data from the backend. Additionally, Django models can store location coordinates, which can be displayed on the map for real-time or database-driven visualization. Proper security practices, such as restricting API keys and using environment variables, should be followed to prevent misuse. Overall, integrating Google Maps enhances the functionality and user experience of Django applications by providing interactive and visually rich location services.





























