# Backend Setup and Launch Guide

This guide will walk you through setting up the backend of the FastAPI + React template from scratch, including database setup, schema creation, initial data population, and launching the backend server.

---

## 1. Add PostgreSQL to your PATH (Mac specific)

If you are on a Mac and have installed PostgreSQL using Postgres.app, add the PostgreSQL binaries to your system PATH to make the `psql` command available in your terminal:

```bash
export PATH=/Applications/Postgres.app/Contents/Versions/latest/bin:$PATH
```

This allows you to use the `psql` command to interact with your PostgreSQL database.

---

## 2. Create the Database

Use the `psql` command-line tool to create the database for the application. Run:

```bash
psql
```

This will open the PostgreSQL interactive terminal where you can create your database.

```sql
CREATE DATABASE app;
```

---

## 3. Activate the Python Virtual Environment

Activate the virtual environment where your backend dependencies are installed:

```bash
cd backend
uv sync
source .venv/bin/activate
```

---


## 5. Install the frontend
```bash
nvm install
nvm use
npm install
```

## 4. Generate API Client from OpenAPI Spec

Run the script to generate the API client code from the OpenAPI specification. This helps keep the frontend and backend API contracts in sync:

```bash
cd ../
bash scripts/generate-client.sh
```

---

## 5. Create Database Schema with Alembic

Apply the latest database migrations to create the schema:

```bash
alembic upgrade head
```

---

## 6. Populate Initial Data

Run the script to add initial data to the database, such as creating an admin superuser:

```bash
python app/initial_data.py
```

---

## 7. Check Database Connection

Before launching the backend, run a pre-start script to verify that the database is awake and accessible:

```bash
python app/backend_pre_start.py
```

---

## 8. Launch the Backend Server

Finally, start the FastAPI backend server in development mode:

```bash
fastapi dev app/main.py
```

This will launch the backend server and make it ready to serve API requests.

---

## 9. Launch the Frontend Server
```bash
npm run dev
```

---
## 10. Check the database
```
SELECT * FROM "user";
```
Should see the admin user there.
