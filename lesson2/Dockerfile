FROM python:alpine3.14

ENV USER_UID 1000
ENV APP_DIR /var/dir

WORKDIR ${APP_DIR}

COPY . ${APP_DIR}

RUN set -eux;  \
    addgroup -g "$USER_UID" developer &&  \
    adduser -D -h ${APP_DIR} -s /bin/sh -u "$USER_UID" -G developer developer && \
    pip install --no-cache-dir -r requirements.txt && \
    rm -f requirements.txt && \
    chown -R developer:developer .

EXPOSE 8080

USER developer

ENTRYPOINT [ "python", "app.py" ]