FROM python:3.12-slim

ENV TZ=Asia/Tokyo

ARG project_dir=/app/
COPY ./app $project_dir
COPY ./requirements.txt $project_dir
WORKDIR $project_dir

RUN apt-get update -y \
    && apt-get install -y curl \
    # install following libraries to connect to MySQL
    && apt-get install -y default-libmysqlclient-dev pkg-config build-essential \
    # To Connect to Postgresql
    && apt-get install -y postgresql-client libpq-dev build-essential \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/* \
    && pip install --upgrade pip \
    && pip install --no-cache-dir -r requirements.txt

EXPOSE 8000

ENTRYPOINT ["uvicorn", "app:app", "--host", "0.0.0.0"]