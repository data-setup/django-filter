# Django Filter Project with Postgres, Gunicorn, and Nginx

## Features

- Built with Django 5.0 & Python 3.12
- Easy installation via [Pip](https://pypi.org/project/pip/) or [Docker](https://www.docker.com/)
- User authentication functionalities including log in/out, sign up, and password reset, powered by [django-allauth](https://github.com/pennersr/django-allauth)
- Efficient serving of static files using [Whitenoise](http://whitenoise.evans.io/en/stable/index.html)
- Styling with the latest version of [Bootstrap (v5)](https://getbootstrap.com/)
- DRY forms with [django-crispy-forms](https://github.com/django-crispy-forms/django-crispy-forms)
- Custom error pages for 404, 500, and 403 errors

# Installation

```bash
python3 -m venv venv
$ source venv/bin/activate
(venv) $ pip install -r requirements.txt
(venv) $ python manage.py createsuperuser
(venv) $ python manage.py runserver
```

Access the site at http://127.0.0.1:8000

# Docker

To use Docker with PostgreSQL as the database, update the DATABASES section of django_project/settings.py as follows:

```bash
# django_project/settings.py
DATABASES = {
    "default": {
        "ENGINE": "django.db.backends.postgresql",
        "NAME": "postgres",
        "USER": "postgres",
        "PASSWORD": "postgres",
        "HOST": "db",  # set in docker-compose.yml
        "PORT": 5432,  # default postgres port
    }
}
```

Then build the Docker image, run the container, and execute standard commands within Docker:

```bash
$ docker-compose up -d --build
$ docker-compose exec web python manage.py migrate
$ docker-compose exec web python manage.py createsuperuser
```

Access the site at http://127.0.0.1:8000

### Options: Create products.json
To populate your database with sample data from a JSON file, run:

```bash
python manage.py loaddata products.json
```

This README.md provides clearer instructions
