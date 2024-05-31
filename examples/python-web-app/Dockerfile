FROM python:3.12-slim

# Set the working directory
WORKDIR /app

# Install system dependencies
RUN apt-get update && \
    apt-get install -y python3 python3-venv && \
    apt-get clean

# Create and activate the virtual environment
RUN python3 -m venv /opt/venv

# Copy the application code
COPY requirements.txt /app
COPY devops /app

# Install the required packages within the virtual environment
RUN /opt/venv/bin/pip install -r requirements.txt

# Ensure manage.py is in the correct location
RUN ls -la /app/manage.py

# Set the virtual environment as the default Python
ENV PATH="/opt/venv/bin:$PATH"

# Run the application
CMD ["python", "manage.py", "runserver", "0.0.0.0:8000"]

