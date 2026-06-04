FROM python:3.11-slim

ENV PYTHONDONTWRITEBYTECODE=1 \
    PYTHONUNBUFFERED=1

WORKDIR /app

COPY requirements.txt /app/requirements.txt
RUN pip install --no-cache-dir -r /app/requirements.txt

COPY . /app

EXPOSE 5004 5005

CMD ["sh", "-c", "gunicorn --chdir /app/rabbit_ig_results/flask --bind 0.0.0.0:5004 app:app & gunicorn --chdir /app/rabbit_tr_results/flask --bind 0.0.0.0:5005 app:app & wait"]