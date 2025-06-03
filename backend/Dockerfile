FROM python:3.9
RUN apt-get update && apt-get install -y tree
WORKDIR /app
RUN pip install gunicorn==20.1.0
COPY requirements.txt .

RUN pip install -r requirements.txt --no-cache-dir

COPY . .
RUN python manage.py makemigrations
RUN python manage.py migrate
RUN apt-get remove -y tree && apt-get autoremove -y
CMD ["gunicorn", "--bind", "0.0.0.0:9000", "--workers", "3", "kittygram_backend.wsgi:application"]