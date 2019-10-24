# Multi-container docker configuration for otus-courses demo

Without data seed!

## Install

```
docker-compose up
```

## Run

```commandline
docker exec -it otus-courses-docker_courses_backend_1 python manage.py migrate
```

## If you want to configure Grafana

There are issues with Grafana seed config in Docker and adding sqlite.db into repo isn't a good idea, so:
 
- 0.0.0.0:3000
- login: admin
- password: koala

### Data source

- InfluxDB
- Url: http://influxdb:8086
- Database: otus
- Measurement: `django_response_time`
 
## Authors

* **Andrei Etmanov** - *Student of OTUS :)*