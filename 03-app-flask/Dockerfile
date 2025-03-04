# With ubuntu image
# FROM ubuntu:22.04
# RUN apt update && apt-get install -y python3 python3-venv

# With python image
# FROM python:3.10
# 
# WORKDIR /app
# 
# RUN python3 -m venv .venv
# 
# ENV VIRTUAL_ENV=/app/.venv
# ENV PATH="$VIRTUAL_ENV/bin:$PATH"
# ENV FLASK_APP=src.app
# 
# COPY requirements.txt ./
# RUN pip install -r requirements.txt
# 
# COPY . .
# 
# EXPOSE 5000
# 
# CMD flask run --host 0.0.0.0

# With pipenv
FROM python:3.10

RUN pip install pipenv

ENV PIPENV_VENV_IN_PROJECT=1
ENV FLASK_APP=src.app

WORKDIR /app
COPY Pipfile* ./
RUN pipenv install

COPY . .

EXPOSE 5000

CMD pipenv run flask run --host 0.0.0.0
