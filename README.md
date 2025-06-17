# Taskmaster API

Taskmaster is a powerful and extensible task management API server built with **FastAPI** and **PostgreSQL**, adhering to RESTful principles. It empowers users to organize tasks efficiently through features like categorization, priority setting, and reminders, all secured with JWT-based authentication. The API is fully documented with OpenAPI and designed for scalability and ease of integration.

## Features

### User Management

- User registration and login with JWT-based authentication.
- Secure password storage using bcrypt.
- Profile management (update name, email, password).
- Role-based access control (e.g., Admin, User).

### Task Management

- Full CRUD operations for tasks.
- Assign due dates and set priorities (Low, Medium, High, Urgent).
- Mark tasks as complete or pending.
- Advanced filtering by priority, due date, or status.

### Categorization

- Create and manage custom categories (e.g., Work, Personal).
- Assign tasks to categories.
- Filter tasks by category.

### Reminder System

- Set one-time reminders for tasks.
- List, update, and delete reminders.
- Asynchronous reminder processing with Celery and Redis.

### API Infrastructure

- RESTful API with standardized HTTP status codes.
- Token-based access control for secure endpoints.
- OpenAPI documentation (accessible at `/docs`).
- Input validation with Pydantic models.
- Rate limiting to prevent abuse.
- Standardized error handling with custom responses.

### Database Management

- PostgreSQL with relational tables for users, tasks, categories, and reminders.
- Database migrations managed with Alembic.

## Tech Stack

| Layer            | Technology                     |
|------------------|--------------------------------|
| Backend          | FastAPI                        |
| Database         | PostgreSQL                     |
| Authentication   | JSON Web Tokens (python-jose)  |
| ORM              | SQLAlchemy                     |
| Migrations       | Alembic                        |
| Task Queue       | Celery with Redis (optional)   |
| API Docs         | FastAPI OpenAPI (built-in)     |
| Validation       | Pydantic                       |
| Rate Limiting    | slowapi (optional)             |

## Getting Started

### Prerequisites

- Python 3.8+
- PostgreSQL
- Redis (optional, for Celery)
- Git

### Installation

1. Clone the repository:
   ```bash
   git clone https://github.com/iraqooh/taskmaster_api.git
   cd taskmaster_api
   ```
   
2. Create a virtual environment and install dependencies:
   ```bash
   python -m venv venv
   source venv/bin/activate  # On Windows: venv\Scripts\activate
   pip install -r requirements.txt
   ```
   
3. Set up environment variables:
   - Create a `.env` file based on `.env.example`.
   - Configure database URL, JWT secret, and other settings.

4. Initialize the PostgreSQL database:
   ```bash
   alembic upgrade head
   ```

5. Run the FastAPI server:
   ```bash
   uvicorn app.main:app --host 0.0.0.0 --port 8000
   ```

6. Access the API documentation at `http://localhost:8000/docs`.

## API Documentation

Explore the API using the interactive OpenAPI docs at `/docs` or `/redoc` when the server is running. All endpoints are clearly documented with request/response schemas.

## Security

- JWT-based authentication ensures secure access to protected endpoints.
- Passwords are hashed using bcrypt.
- Rate limiting is implemented to prevent abuse (configurable with `slowapi`).

## Contributing

Contributions are welcome! Please follow these steps:
1. Fork the repository.
2. Create a feature branch (`git checkout -b feature/your-feature`).
3. Commit your changes (`git commit -m "Add your feature"`).
4. Push to the branch (`git push origin feature/your-feature`).
5. Open a pull request.

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

## Contact
For questions or feedback, open an issue or reach out to the maintainer at [iraqooh@gmail.com].
