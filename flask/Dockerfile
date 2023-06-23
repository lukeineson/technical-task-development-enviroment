# Base Image
FROM python:3.12.0b3-slim-bookworm as base

# Set the working directory
WORKDIR /app

# Install dependencies
COPY requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt

# Copy application code
COPY . . 

#Expose the Flask application port
EXPOSE 5000

#Set the entrypoint command
CMD ["python", "app.py"]
