# analytics/Dockerfile
FROM python:3.10-slim

# Prevent Python from writing pyc files and enable unbuffered logs
ENV PYTHONDONTWRITEBYTECODE=1
ENV PYTHONUNBUFFERED=1

WORKDIR /app

# Install dependencies
COPY requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt

# Copy application code
COPY . .

# The Udacity analytics service commonly listens on 5153
EXPOSE 5153

# Run the app
CMD ["python", "app.py"]
