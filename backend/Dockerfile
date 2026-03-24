FROM python:3.11-slim

RUN apt-get update \
    && apt-get install -y --no-install-recommends gcc g++ \
    && rm -rf /var/lib/apt/lists/*

WORKDIR /app

COPY requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt

COPY . .
RUN mkdir -p uploads/simulations

ENV FLASK_HOST=0.0.0.0
ENV FLASK_DEBUG=False

EXPOSE 8080

CMD ["sh", "-c", "FLASK_PORT=${PORT:-8080} python run.py"]
