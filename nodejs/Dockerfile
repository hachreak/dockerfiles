FROM debian:jessie

RUN apt-get update && \
    apt-get install -y curl && \
    curl -sL https://deb.nodesource.com/setup | bash - && \
    apt-get install -y nodejs build-essential && \
    apt-get clean -y && \
    apt-get autoclean -y && \
    apt-get autoremove -y && \
    npm -g install npm@latest && \
    npm install -g bower
