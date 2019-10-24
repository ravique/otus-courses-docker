FROM python:3.7 as otus-backend

WORKDIR /opt/otus-django/otus-courses-website

RUN apt-get update && \
    apt-get install --assume-yes libpq-dev postgresql postgresql-contrib && \
    git clone -b "feature/multi-db" https://github.com/ravique/otus-courses-website.git .

COPY ./uwsgi.ini .

RUN pip3 install uwsgi &&\
    pip3 install -r requirements.txt

RUN python manage.py collectstatic --noinput

EXPOSE 8000

ENTRYPOINT ["uwsgi", "--ini", "uwsgi.ini"]



