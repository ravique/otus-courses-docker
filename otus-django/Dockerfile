FROM python:3.7

WORKDIR /opt/otus-django/otus-courses-website

RUN git clone -b "feature/pytest-factory_boy" https://github.com/ravique/otus-courses-website.git .

COPY ./db.sqlite3 .
COPY ./uwsgi.ini .
RUN mkdir static && mkdir frontend
COPY ./otus-react/build ./frontend

RUN pip3 install uwsgi &&\
    pip3 install -r requirements.txt

COPY ./otus-react/build/static ./static
#CMD python manage.py collectstatic --noinput

EXPOSE 8000

CMD ["uwsgi", "--ini", "uwsgi.ini"]

