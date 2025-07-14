# TaskFlow API

TaskFlow is a simple task management API built with Django and Django Rest Framework. It allows users to register, log in, and manage their tasks through a RESTful API.

## Features

*   **User Authentication:** Register and log in to receive an authentication token.
*   **Task Management:** Create, read, update, and delete your own tasks.
*   **API Endpoints:**
    *   `POST /api/register/`: Register a new user.
    *   `POST /api/api-token-auth/`: Log in and receive an authentication token.
    *   `GET /api/tasks/`: List all of your tasks.
    *   `POST /api/tasks/`: Create a new task.
    *   `GET /api/tasks/<id>/`: Retrieve a specific task.
    *   `PUT /api/tasks/<id>/`: Update a specific task.
    *   `DELETE /api/tasks/<id>/`: Delete a specific task.

## Technology Stack

*   **Backend:** Python, Django, Django Rest Framework
*   **Database:** PostgreSQL
*   **Authentication:** Token-based authentication
*   **Deployment:** Docker

## Getting Started

### Prerequisites

*   Docker
*   Docker Compose

### Installation

1.  Clone the repository:

    ```bash
    git clone https://github.com/Niyaz-H/taskflow.git
    ```

2.  Navigate to the project directory:

    ```bash
    cd taskflow
    ```

3.  Build and run the Docker containers:

    ```bash
    docker-compose up --build -d
    ```

4.  Apply the database migrations:

    ```bash
    docker-compose exec web python manage.py migrate
    ```

5.  Create a superuser:

    ```bash
    docker-compose exec web python manage.py create_superuser
    ```

### Usage

The API will be available at `http://localhost:8000`. You can use a tool like [Postman](https://www.postman.com/) or `curl` to interact with the API.

**1. Register a new user:**

```bash
curl -X POST http://localhost:8000/api/register/ -H "Content-Type: application/json" -d '{"username": "yourusername", "password": "yourpassword"}'
```

**2. Log in and get a token:**

```bash
curl -X POST http://localhost:8000/api/api-token-auth/ -H "Content-Type: application/json" -d '{"username": "yourusername", "password": "yourpassword"}'
```

**3. Create a new task:**

```bash
curl -X POST http://localhost:8000/api/tasks/ -H "Authorization: Token YOUR_TOKEN" -H "Content-Type: application/json" -d '{"title": "My first task", "description": "This is a description of my first task."}'
```

**4. List all tasks:**

```bash
curl -X GET http://localhost:8000/api/tasks/ -H "Authorization: Token YOUR_TOKEN"