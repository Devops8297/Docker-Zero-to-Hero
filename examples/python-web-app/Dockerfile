FROM ubuntu

WORKDIR /app

# Copy files first to improve build caching
COPY requirements.txt /app
COPY devops /app

# Install required packages
RUN apt-get update && \
    apt-get install -y python3 python3-pip python3-venv build-essential python3-dev && \
    python3 -m venv /app/venv && \
    /app/venv/bin/pip install --upgrade pip && \
    /app/venv/bin/pip install -r requirements.txt

# Set the virtual environment path for all subsequent commands
ENV PATH="/app/venv/bin:$PATH"

ENTRYPOINT ["python3"]
CMD ["manage.py", "runserver", "0.0.0.0:8000"]
