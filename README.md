# [microservice] service

This microservice provides a simple API for [microservice].

## Setup

1. Clone the repository:

   ```
   git clone https://github.com/SoloAWS/[microservice]-service.git
   cd [microservice]-service
   ```

2. Create and activate a virtual environment:

   ```
   python -m venv venv
   source venv/bin/activate  # On Windows, use `venv\Scripts\activate`
   ```

3. Install the required packages:
   ```
   pip install -r requirements.txt
   ```

## Running the Service

To run the service locally:

```
uvicorn app.main:app --reload --port 8006
```

The service will be available at `http://localhost:8006`.

## API Endpoints

- `GET /incident-query/health`: Health check endpoint

## Docker

To build and run the Docker container:

```
docker build -t [microservice]-service .
docker run -p 8006:8006 [microservice]-service
```

Make sure to expose port 8006 in your Dockerfile:

```dockerfile
EXPOSE 8006
CMD ["uvicorn", "app.main:app", "--host", "0.0.0.0", "--port", "8006"]
```

## Alembic
This project uses **Alembic** for handling database migrations with **SQLAlchemy** in a **FastAPI** project. The configuration allows for seamless switching between **PostgreSQL** and **SQLite** databases based on environment variables.

### Common Commands
- Create a new migration:
``` bash
alembic revision --autogenerate -m "Message"
```

- Apply all migrations:

``` bash

alembic upgrade head
```
- Downgrade to the previous migration:

``` bash
alembic downgrade -1
```

- Show the current migration status:
``` bash
alembic current
```