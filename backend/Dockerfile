FROM python:3.12-slim

WORKDIR /app

RUN python -m pip install --upgrade pip

# Установка необходимых пакетов, отсутствующих в slim.
RUN apt-get update && \
    apt-get install -y gcc python3-dev libpq-dev && \
    apt-get install -y libpq-dev && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/*

COPY requirements.txt .

RUN pip install -r requirements.txt --no-cache-dir

COPY . .

CMD ["gunicorn", "--bind", "0.0.0.0:8000", "backend.wsgi"]