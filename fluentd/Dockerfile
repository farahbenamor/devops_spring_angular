# fluentd/Dockerfile
FROM fluent/fluentd:v1.11-debian

# Use root account to use apk
USER root

# below RUN includes plugin as examples elasticsearch is not required
# you may customize including plugins as you wish
#RUN apk add --no-cache --update --virtual .build-deps \
#        sudo build-base ruby-dev \
# && sudo gem install fluent-plugin-elasticsearch \
# && sudo gem sources --clear-all \
# && apk del .build-deps \
# && rm -rf /tmp/* /var/tmp/* /usr/lib/ruby/gems/*/cache/*.gem

RUN ["gem", "install", "elasticsearch", "--no-document", "--version", "7.13.3"]
RUN ["gem", "install", "fluent-plugin-elasticsearch", "--no-document", "--version", "5.0.5"]
USER fluent
