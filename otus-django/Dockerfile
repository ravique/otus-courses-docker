FROM python:3.7 as otus-backend

WORKDIR /opt/otus-django/otus-courses-website

RUN git clone -b "feature/pytest-factory_boy" https://github.com/ravique/otus-courses-website.git .

COPY ./db.sqlite3 .
COPY ./uwsgi.ini .

RUN pip3 install uwsgi &&\
    pip3 install -r requirements.txt

RUN python manage.py collectstatic --noinput

EXPOSE 8000

ENTRYPOINT ["uwsgi", "--ini", "uwsgi.ini"]



