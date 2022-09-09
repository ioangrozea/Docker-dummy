# syntax = docker/dockerfile:experimental
FROM python:3.9-slim-bullseye

RUN apt-get update -qy && apt-get install -qy \
    build-essential tini libsasl2-dev libssl-dev default-libmysqlclient-dev gnutls-bin

RUN pip install poetry==1.1.15
COPY pyproject.toml .
COPY poetry.lock .
RUN poetry config virtualenvs.create false
RUN --mount=type=cache,mode=0777,target=/root/.cache/pypoetry poetry install