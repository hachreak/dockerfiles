FROM python:3

RUN apt-get update && \
    apt-get install -y lsb-release

# install node
RUN apt-get update && \
    apt-get install -y curl build-essential && \
    curl -sL https://deb.nodesource.com/setup_6.x | bash - && \
    apt-get install -y nodejs && \
    npm install -g bower node-sass clean-css requirejs uglify-js && \
    npm install -g clean-css@3.4.24 && \
    npm install -g node-sass@3.8.0

# install elasticsearch
RUN cd /tmp && \
  wget -qO - https://packages.elastic.co/GPG-KEY-elasticsearch | apt-key add - && \
  echo "deb http://packages.elastic.co/elasticsearch/2.x/debian stable main" | tee -a /etc/apt/sources.list.d/elasticsearch-2.x.list && \
  apt-get update && apt-get install -y elasticsearch default-jdk redis-server && \
  /usr/share/elasticsearch/bin/plugin install mapper-attachments -b

# install python libraries
RUN pip install --upgrade pip setuptools py && \
    pip install --upgrade twine wheel coveralls requirements-builder ipdb ipython httpie gunicorn

# install postgresql
RUN echo "deb http://apt.postgresql.org/pub/repos/apt/ $(lsb_release -cs)-pgdg main" > /etc/apt/sources.list.d/pgdg.list && \
    wget --quiet -O - https://www.postgresql.org/media/keys/ACCC4CF8.asc | apt-key add - && \
    apt-get update && apt-get install postgresql-9.6 -y
# RUN service postgresql start && \
#     su -c "echo \"CREATE DATABASE cds OWNER postgres;\" | psql" postgres && \
#     su -c "echo \"ALTER USER postgres PASSWORD '';\" | psql" postgres

# install rabbitmq
RUN apt-get update && \
    apt-get install -y rabbitmq-server

RUN apt-get update && \
    pip install --upgrade pip setuptools py && \
    pip install twine wheel coveralls requirements-builder flask-shell-ipython gunicorn httpie --upgrade

# RUN echo -ne "postgres\npostgres" | passwd postgres && \
#     su -c "echo \"CREATE DATABASE cds OWNER postgres;\" | psql" postgres && \
#     su -c "echo \"ALTER USER postgres PASSWORD 'postgres';\" | psql" postgres

RUN mkdir /src/code -p

VOLUME /src/code
WORKDIR /src/code
