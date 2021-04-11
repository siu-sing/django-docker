# Django with Postgres, Docker, Gunicorn and Nginx

Based on [this guide](https://testdriven.io/blog/dockerizing-django-with-postgres-gunicorn-and-nginx/)


## Usage

Replace `dev` with `prd` for production environment.

- Compose up
    ```sh
    docker-compose -f docker-compose.dev.yml up -d --build
    ```
    
- Migrate and load static files（for prd only)
    ```sh
    docker-compose -f docker-compose.prd.yml exec web python manage.py migrate --noinput && \
    docker-compose -f docker-compose.prd.yml exec web python manage.py collectstatic --no-input --clear
    ```

- Compose down
    ```sh
    docker-compose -f docker-compose.dev.yml down
    ```