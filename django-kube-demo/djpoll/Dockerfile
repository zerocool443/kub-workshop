FROM python:2.7-onbuild

ENV PYTHONUNBUFFERED 1

RUN apt-get -q update && apt-get install -y -q \
    sqlite3 --no-install-recommends \
    && apt-get clean && rm -rf /var/lib/apt/lists/*

ENV LANG C.UTF-8

RUN mkdir -p /app

WORKDIR /app

ADD requirements.txt /app/requirements.txt
RUN pip install --no-cache-dir -r /app/requirements.txt

ADD . /app

CMD gunicorn -b :8000 mysite.wsgi
