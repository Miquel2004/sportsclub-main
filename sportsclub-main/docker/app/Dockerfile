# docker/app/Dockerfile
FROM python:3.13-slim-trixie
EXPOSE 8080

# Set environment variables
ENV PYTHONDONTWRITEBYTECODE=1
ENV PYTHONUNBUFFERED=1

# Set work directory
WORKDIR /app

# Install system dependencies
RUN apt-get update && apt-get install -y \
    curl \
    && rm -rf /var/lib/apt/lists/*

# Install Python dependencies
COPY requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt
RUN pip install --no-cache-dir uvicorn

# Copy project
COPY sportsclub/ .

# Collect static files (needed when serving through a reverse proxy)
RUN python manage.py collectstatic --noinput

# --- TAREA 1: SEGURETAT ---
# Creem l'usuari sense privilegis
RUN useradd -m appuser

# Canviem el propietari de la carpeta /app a l'usuari nou
# Com que a la línia 10 has posat WORKDIR /app, fem servir /app aquí
RUN chown -R appuser:appuser /app

# Indiquem que s'executi com a appuser i no com a root
USER appuser


# Run uvicorn
CMD ["uvicorn", "sportsclub.asgi:application", "--host", "0.0.0.0", "--port", "8080"]
