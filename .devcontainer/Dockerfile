FROM ubuntu:18.04

RUN apt-get update && apt-get install -y \
        python \
        python-pip \
        python-virtualenv \
        python-wheel \
        \
        python-psycopg2 \
        python-redis \
        python-requests \
        python-sqlalchemy \
        \
        curl jq redis

RUN mkdir /venvs

RUN virtualenv /venvs/demo

COPY demo/requirements-fluid.txt /venvs/demo.requirements.txt

RUN set -eu; \
    echo /usr/lib/python2.7/dist-packages >> /venvs/demo/lib/python2.7/site-packages/dist-packages.pth; \
    . /venvs/demo/bin/activate; \
    pip install -r /venvs/demo.requirements.txt; \
    pip freeze

# Not for use in a Dev Container, but very useful for a Python container in general,
# especially when logging to stdout/stderr
#
ENV PYTHONUNBUFFERED=1
