FROM python:2

RUN cd /tmp && \
  wget -qO - https://packages.elastic.co/GPG-KEY-elasticsearch | apt-key add - && \
  echo "deb http://packages.elastic.co/elasticsearch/2.x/debian stable main" | tee -a /etc/apt/sources.list.d/elasticsearch-2.x.list && \
  apt-get update && apt-get install -y elasticsearch default-jdk redis-server

ONBUILD RUN service elasticsearch restart
ONBUILD RUN service redis-server restart

RUN pip install ipdb ipython pudb && mkdir /src/code -p

VOLUME /src/code
WORKDIR /src/code
