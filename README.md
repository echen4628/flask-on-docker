This repo contains code for containerizing a Flask application with Postgres for development. It also contains production-ready setup with Gunicorn and Nginx. The website could be launched locally and allows users to upload media files and display static files. See below for the resulting website and instructions on how to use this setup.

<img src="demo.gif" width="80%" />

Create and add your login to `.env.prod`. It should have the following fields
```
FLASK_APP=
FLASK_DEBUG=
DATABASE_URL=
SQL_HST=
SQL_PORT=
DATABASE=
```
Also create `.env.prod.db`. It should have the following fields
```
POSTGRES_USER=
POSTGRES_PASSWORD=
POSTGRES_DB=
```

For Launching Web Page (Development):
```
docker-compose up -d --build
```
The site should be up on http://localhost:1340/

You can access postgres using
```
$ docker-compose exec web python manage.py create_db
$ docker-compose exec db psql --username=hello_flask
```

For Launching Web Page (Production):
```
$ docker-compose -f docker-compose.prod.yml down -v
$ docker-compose -f docker-compose.prod.yml up -d --build
$ docker-compose -f docker-compose.prod.yml exec web python manage.py create_db
```
The site should be up on http://localhost:1339/

You can check the logs via `docker-compose logs -f`

