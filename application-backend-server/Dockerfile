FROM python:3.11-alpine

WORKDIR /app

COPY requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt

COPY app.py .
COPY students.json .
COPY blogs.json .
COPY templates ./templates

ENV PYTHONUNBUFFERED=1

EXPOSE 8081

CMD ["python", "app.py"]