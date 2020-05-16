# Django3_blog_application

This is a basic blog app.

Navigate to the project root directory and create an isolated environment with the following command:
`python3 -m venv my_env`

This will create a `my_env/` directory, including your Python environment. Any Python libraries you install while your virtual environment is active will go into the `my_env/lib/python3.8/site-packages` directory.

Run the following command to activate your virtual environment:
`source my_env/bin/activate`

Run the following command at the shell prompt to install the dependencies with pip:
`pip install -r requirements.txt`

If you are using Linux, install PostgreSQL with the following command:
`sudo apt-get install postgresql postgresql-contrib`

If you are using macOS or Windows, download PostgreSQL from https://www.postgresql.org/download/ and install it.

You also need to install the psycopg2 PostgreSQL adapter for Python. Run the following command in the shell to install it:
`pip install psycopg2-binary==2.8.4`

Create a user for your PostgreSQL database. Open the shell and run the following commands:
```
su postgres
createuser -dP blog
```
You will be prompted for a password for the new user. Enter the desired password and then create the blog database and give ownership to the blog user you just created with the following command:
`createdb -E utf8 -U blog blog`

Then, edit the `settings.py` file of your project and modify the DATABASES setting to make it look as follows:
```
DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.postgresql',
        'NAME': 'blog',
        'USER': 'blog',
        'PASSWORD': '*****',
    }
}
```
Replace the preceding data with the database name and credentials for the user you created. The new database is empty. Run the following command to apply all database migrations:
`python manage.py migrate`

Finally, create a superuser with the following command:
`python manage.py createsuperuser`

You can now run the development server and access the administration site at http://127.0.0.1:8000/admin/ with the new superuser.
`python manage.py runserver`

You should see something like this:
```
Watching for file changes with StatReloader
Performing system checks...
System check identified no issues (0 silenced).
January 01, 2020 - 10:00:00
Django version 3.0, using settings 'mysite.settings'
Starting development server at http://127.0.0.1:8000/
Quit the server with CONTROL-C.
```
Now open `http://127.0.0.1:8000/blog` in your browser. You should see a blog app.

![Screenshot 2020-05-16 at 8 53 41 PM](https://user-images.githubusercontent.com/49444980/82123938-b9ca2c80-97b9-11ea-8684-94133f1b5fbf.png)
![Screenshot 2020-05-16 at 8 53 56 PM](https://user-images.githubusercontent.com/49444980/82123978-f007ac00-97b9-11ea-9a88-3d3cb21921f8.png)
![Screenshot 2020-05-16 at 8 54 04 PM](https://user-images.githubusercontent.com/49444980/82123986-fc8c0480-97b9-11ea-9561-05121f9762d4.png)
![Screenshot 2020-05-16 at 8 54 13 PM](https://user-images.githubusercontent.com/49444980/82124004-0d3c7a80-97ba-11ea-84aa-b5b7c8adac27.png)
![Screenshot 2020-05-16 at 8 54 34 PM](https://user-images.githubusercontent.com/49444980/82124011-188fa600-97ba-11ea-8212-46018bf7cea4.png)
![Screenshot 2020-05-16 at 8 54 46 PM](https://user-images.githubusercontent.com/49444980/82124026-26ddc200-97ba-11ea-930c-c3bea6b69366.png)
![Screenshot 2020-05-16 at 8 54 54 PM](https://user-images.githubusercontent.com/49444980/82124045-38bf6500-97ba-11ea-8a43-78db6bfdd572.png)
