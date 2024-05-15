FROM python:3.10-slim-buster
# Install python packages
COPY requirements.txt /tmp
RUN apt-get update \
    && apt-get install -y gcc libpq-dev \
    && pip install -r /tmp/requirements.txt
