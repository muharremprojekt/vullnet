# Use the official Python slim image
FROM python:3.12-slim

# Prevent Python from writing .pyc files and enable unbuffered output
ENV PYTHONDONTWRITEBYTECODE=1 \
    PYTHONUNBUFFERED=1

# Set working directory inside the container
WORKDIR /app

# Copy requirements and install dependencies
COPY requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt

# Copy the rest of the code
COPY . .

# Expose the port Render provides via $PORT
EXPOSE $PORT

# Start the Django app using Gunicorn
CMD ["gunicorn", "vullnet_client.wsgi:application", "--bind", "0.0.0.0:$PORT", "--workers", "3"]
