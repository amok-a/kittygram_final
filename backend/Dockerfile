FROM python:3.9

WORKDIR /app
RUN pip install gunicorn==20.1.0
COPY requirements.txt .


COPY . .
RUN pip install -r requirements.txt --no-cache-dir

RUN python manage.py collectstatic --noinput

CMD ["gunicorn", "--bind", "0.0.0.0:9000", "kittygram_backend.wsgi:application"]