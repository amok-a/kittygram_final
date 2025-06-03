FROM python:3.9

WORKDIR /app
RUN pip install gunicorn==20.1.0
COPY requirements.txt .

RUN pip install -r requirements.txt --no-cache-dir

COPY . .
RUN echo "Проверка структуры проекта:" && ls -la
RUN echo "Проверка содержимого kittygram_backend:" && ls -la kittygram_backend
RUN echo "Попытка импорта модуля:" && python -c "import kittygram_backend.wsgi"
RUN python manage.py makemigrations
RUN python manage.py migrate
CMD ["gunicorn", "--bind", "0.0.0.0:9000", "kittygram_backend.wsgi:application"]