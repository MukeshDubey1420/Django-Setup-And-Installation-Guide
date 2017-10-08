## **I Hope that You Guys had Read the previous instructions carefully, Now we are moving to our next part i.e. Workflow For Request Response Cycle in Django. & Connecting the project with APP.**


### **Let's Have A Rough Idea That How Request Response Cycle Works In Django. How Request is Generated Via Client And how It returns data and template to the client.**


![Djangoworkflow](Djangoworkflow.jpeg)

##               <-------Workflow Explanation --------->
#### It all starts with a request. The request reaches to the controller(The  controller is responsible for grabbing all of the necessary building blocks and organizing them as necessary.)Those building blocks are known as models.(models help the controller to retrieve all of the information it needs from the database.) So the request comes in the form of Response to the Client.The final product is known as the view.(Complete code i.e Template + Data).The view is the final page the user sees in their browser.

### Creating the APP

#### Here same case for naming, we can choose any name for our app, For example in case of project my project name is mysite, lets say here i am using the name of my APP is polls.
### To create an APP we have to write `python manage.py startapp polls`in our cmd window, Here startapp plays the same role as startproject plays in case of creating the name of our project
#### `python manage.py startapp polls`
 **The output will be like this :--**
 ![apps](Apps.png)

### Configuring our APP with Django Project In Settings.py File.

#### To include the APP in our project, we need to add a reference to its configuration class in the `INSTALLED_APPS` setting. For this we have to Edit the `mysite/settings.py` file and add that APP to the INSTALLED_APPS setting. It’ll look like this:
```
mysite/settings.py
INSTALLED_APPS = [
    'polls',
    'django.contrib.admin',
    'django.contrib.auth',
    'django.contrib.contenttypes',
    'django.contrib.sessions',
    'django.contrib.messages',
    'django.contrib.staticfiles',
]
```
Note:- Donot forget to place ' , ' comma After adding the app Name i.e. `polls.`



### DataBase Setup--->

#### By default, the django configuration uses SQLite. If you’re new to databases, or you’re just interested in trying Django, this is the easiest choice. SQLite is included in Python, so you won’t need to install anything else to support your database.
#### When starting your first real project, however, you may want to use a more scalable database like `PostgreSQL`, `MySql` to avoid database-switching headaches down the road.
#### [Installation Guide For Installing MySql For Windows ..Click Here..](https://github.com/avmain/Acadview-Docs/blob/master/docs/How%20to%20install%20MySQL%20in%20Windows.md)
#### [Installation Guide For Installing PostgreSQL For Windows ..Click Here..](https://drive.google.com/file/d/0B6G-YjcSmDxeWkdGUjBDTGwxRzg/view?ths=true)

To do this, we open the settings.py file in mysite directory.
Next, we navigate to the DATABASE dictionary, which looks like this:
![Databases](Database.png)
#### Now You have to **Change the following keys in the DATABASES** 'default' item to match your database connection settings:

* #####  **ENGINE** – Either `'django.db.backends.sqlite3'`,  `'django.db.backends.postgresql'`, `'django.db.backends.mysql'`, or ``'django.db.backends.oracle'`` Depending Upon Your Choice.
* #### **NAME** – The name of your database. If you’re using SQLite, the database will be a file on your computer; in that case, NAME should be the full absolute path, including filename, of that file. The default value, `os.path.join(BASE_DIR, 'db.sqlite3')`, will store the file in your project directory.
##### **Note:-** If you are not using SQLite as your database, additional settings such as USER, PASSWORD, and HOST must be added.


#### [MySQL-Django configuration for Windows...Check here..](https://docs.google.com/document/d/1tUnpcf_u40-XZdnjNjCPpkvV_8UvLkJ9QW8mcGwRvAY/edit)









#### Now Configure the Urls in File (Urls.py) For Your Logic in (Views.py) And Create the Data Model(models.py) And Map Urls to Views.

#### When a user makes a request for a page on your web app, Django controller takes over to look for the corresponding view via the url.py file, and then return the HTML response or a 404 not found error, if not found. In url.py, the most important thing is the "urlpatterns" tuple. It’s where you define the mapping between URLs and views.

#### **[To get more information regarding Urls in Django Visit here.....](https://www.tutorialspoint.com/django/django_url_mapping.htm)**

### <--- What is MVC/MVT Model Architecture in Django ---> ??  [Check this for more info....](https://djangobook.com/model-view-controller-design-pattern/)

#### Broadly, Django Follows  `MVC (Model View Controller) architecture` closely enough to be called an MVC framework. *Django has been referred to as an MTV framework because the controller is handled by the framework itself and most of the excitement happens in models, templates and views.* However, Django calls these pieces by different names. The four pieces to understand for Django are:--> *URL patterns, views, models, and templates.*. Each of these pieces has a separate role.

##### * The URL patterns take the path of a request and decide, which views should handle the request.The patterns for our project are defined in folder  `mysite/urls.py`. Give a request, the URL patterns pass control to the views.

##### * Views are the logic layer of the program, which are pythons functions that take a request and return an HTTP response.Our views are defined in folder `polls/views.py`.

#### * Each view can use the models,which we have defined in folder  `polls/models.py` to query the database as needed.Each view relies on a corresponding template(HTML+CSS) to help with the presentation layer of what the HTML will look like. Each template is a separate file that consists of HTML with some extra template syntax.

##### We haven't created any templates yet, but they will live in the `mysite/templates` folder.


## <---- Diffrence btw MVC and MVT ---->

### In **MVT**, a request to a URL is dispatched to a View. This View calls into the Model, performs manipulations and prepares data for output. The data is passed to a Template that is rendered an emitted as a response. ideally in web frameworks, the controller is hidden from view.

### Whereas in **MVC**, the user interacts with the GUI, the controller handles the request and notifies the model and the view queries the model to display the result to the user.
