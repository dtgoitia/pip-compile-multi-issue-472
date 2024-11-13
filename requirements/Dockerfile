FROM python:3.10-slim

ENV PYTHONUNBUFFERED 1
ENV PYTHONDONTWRITEBYTECODE 1

WORKDIR /app

RUN adduser rootlessuser

RUN pip install --upgrade pip        && \
    pip install pip-compile-multi    && \
    apt-get update                   && \
    apt-get install -y                  \
        default-libmysqlclient-dev      \
        gcc                             \
        libkrb5-dev                     \
        libpq-dev                       \
        pkg-config

#########################################################################
#
#   REQUIRED SYSTEM-LEVEL DEPENDENCIES
#
#########################################################################
#
# List of apt packages installed so that a given command is available for
# Python packages:
#
# | Python package | command      | apt package                |
# |----------------|--------------|----------------------------|
# | gssapi         | krb5-config  | libkrb5-dev, gcc           |
# | mysqlclient    | pkg-config   | pkg-config                 |
# | pymssql        | mysql_config | default-libmysqlclient-dev |
# | psycopg2       | pg_config    | libpq-dev                  |
#

USER rootlessuser
