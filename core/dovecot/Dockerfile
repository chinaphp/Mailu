FROM alpine:3.7

RUN echo "@testing http://nl.alpinelinux.org/alpine/edge/testing" >> /etc/apk/repositories \
 && apk add --no-cache \
     dovecot dovecot-sqlite dovecot-pigeonhole-plugin dovecot-pigeonhole-plugin-extdata \
     dovecot-fts-lucene rspamd-client@testing python py-jinja2 py-pip \
 && pip install --upgrade pip \
 && pip install tenacity

COPY conf /conf
COPY sieve /var/lib/dovecot
COPY start.py /start.py

EXPOSE 110/tcp 143/tcp 993/tcp 4190/tcp 2525/tcp
VOLUME ["/data", "/mail"]

CMD /start.py
