FROM ubuntu:20.04

#RUN useradd -ms /bin/bash redis
#USER redis

COPY ./bin/* /usr/local/bin/
COPY docker-entrypoint.sh /usr/local/bin/
RUN echo $PATH
ENV PATH="$PATH:/usr/local/bin"
RUN echo $PATH
EXPOSE 6379
RUN bash -c "groupadd -r -g 999 redis && useradd -r -g redis -u 999 redis"
RUN bash -c "mkdir /data && chown redis:redis /data"
RUN bash -c "apt-get update && apt-get install gosu"
VOLUME /data
WORKDIR /data

ENTRYPOINT ["/usr/local/bin/docker-entrypoint.sh"]

CMD ["redis-server"]