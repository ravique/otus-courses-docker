FROM node:12.12-alpine as otus-frontend

WORKDIR ./opt/otus-frontend

RUN apk add --update npm && apk add git
RUN git clone https://github.com/ravique/otus-courses-react.git .
RUN npm i
RUN npm run-script build

FROM nginx:alpine as nginx-proxy

COPY . /etc/nginx/conf.d
COPY --from=otus-frontend /opt/otus-frontend/build/static/css ./opt/static/css
COPY --from=otus-frontend /opt/otus-frontend/build/static/js ./opt/static/js
COPY --from=otus-frontend /opt/otus-frontend/build ./opt/frontend

COPY --from=otus-backend /opt/otus-django/otus-courses-website/static ./opt/static



