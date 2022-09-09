# syntax = docker/dockerfile:experimental
FROM apache/airflow:2.3.3-python3.9
USER root
RUN apt-get update -qy && apt-get install -qy \
    build-essential tini libsasl2-dev libssl-dev default-libmysqlclient-dev gnutls-bin

USER airflow
RUN pip install poetry==1.1.15
COPY pyproject.toml .
COPY poetry.lock .
RUN poetry config virtualenvs.create false
RUN poetry config cache-dir /opt/airflow/.cache/pypoetry
RUN --mount=type=cache,uid=50000,mode=0777,target=/opt/airflow/.cache/pypoetry poetry install