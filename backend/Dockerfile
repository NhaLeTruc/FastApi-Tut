FROM python:3.8-slim-buster

WORKDIR /backend

ENV PYTHONDONTWRITEBYTECODE 1
ENV PYTHONBUFFERED 1

# install system dependencies
RUN apt-get update \
  && apt-get -y install netcat gcc postgresql \
  && apt-get clean

# install python dependencies
RUN pip install --upgrade pip
COPY ./requirements.txt /backend/requirements.txt
RUN pip install -r requirements.txt
RUN apt-get -y install libpq-dev python-dev
RUN pip install psycopg2

COPY . /backend

CMD ["uvicorn", "--host", "0.0.0.0", "--port", "8000", "app.api.server:app"]
