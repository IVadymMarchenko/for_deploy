FROM python:3.11-slim

RUN apt-get update && apt-get install -y \
    build-essential \
    && rm -rf /var/lib/apt/lists/*

# Переходим в подкаталог, где лежат manage.py и requirements.txt
WORKDIR /app

COPY app_base/requirements.txt .

RUN pip install --no-cache-dir -r requirements.txt

# Копируем весь app_base в контейнер
COPY app_base/ /app/

EXPOSE 8000

CMD ["sh", "-c", "python manage.py migrate && python manage.py runserver 0.0.0.0:8000"]
