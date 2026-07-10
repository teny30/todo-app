# Goal Description

The goal is to build two distinct applications within the project directory:
1. A **cryptographically secure random password generator** built using Django.
2. A **full CRUD To-Do List application** built using Flask, featuring RESTful GET/POST endpoints and session management.

Both applications will feature modern, vibrant, and premium user interfaces adhering to best web design practices.

## User Review Required

> [!IMPORTANT]  
> The project involves two different web frameworks (Django and Flask). I plan to structure the repository as a monorepo containing both applications in separate subdirectories (`password_generator_django/` and `todo_app_flask/`).
> Please confirm if this structure is acceptable, or if you prefer a different setup (e.g., integrating them into a single web server using WSGI middleware, although keeping them separate is usually cleaner for distinct frameworks).

## Open Questions

> [!WARNING]  
> 1. **To-Do List Database**: I will use SQLite via Flask-SQLAlchemy for the To-Do list to keep it lightweight and self-contained. Is this acceptable?
> 2. **Session Management**: I plan to use Flask's built-in signed cookie-based sessions to manage user states (e.g., login/registration) for the To-Do app. Is this what you envisioned?
> 3. **Design Framework**: I will use Vanilla CSS with a highly polished custom design system (glassmorphism, vibrant colors, animations) as per the guidelines. Should I avoid Bootstrap/Tailwind entirely for this?

## Proposed Changes

---

### Django Password Generator

This component will be housed in `password_generator_django/`.

#### [NEW] `password_generator_django/manage.py`
Standard Django entry point.

#### [NEW] `password_generator_django/password_project/settings.py`, `urls.py`, etc.
Django project configuration.

#### [NEW] `password_generator_django/generator/views.py`
Will contain the logic using Python's `secrets` module to generate cryptographically secure passwords based on user-defined criteria (length, symbols, numbers, etc.).

#### [NEW] `password_generator_django/generator/templates/generator/index.html`
A premium, modern interface for the password generator featuring micro-animations and a sleek dark mode or vibrant color palette.

---

### Flask To-Do List App

This component will be housed in `todo_app_flask/`.

#### [NEW] `todo_app_flask/app.py`
The main Flask application file defining the setup, SQLAlchemy database models (User and Task), and the RESTful routes (`GET /`, `POST /add`, `POST /update/<id>`, `POST /delete/<id>`).

#### [NEW] `todo_app_flask/templates/base.html`, `index.html`, `login.html`, `register.html`
Premium UI templates for the To-Do app.

#### [NEW] `todo_app_flask/static/style.css`
Custom CSS for the Flask application to deliver a "wow" factor with glassmorphism and modern typography.

#### [NEW] `requirements.txt`
Root level file specifying the dependencies (`Django`, `Flask`, `Flask-SQLAlchemy`, `Werkzeug`).

## Verification Plan

### Automated Tests
- Run `python manage.py test` (if unit tests are added for the password generator).
- Validate the cryptographic security by inspecting the implementation (ensuring `secrets.choice` is used instead of `random.choice`).

### Manual Verification
- Start the Django server and manually verify that passwords are generated correctly with the selected options.
- Start the Flask server, register a user, log in (testing session management), and perform full CRUD operations (Create, Read, Update, Delete) on tasks.
- Visually inspect both applications to ensure the design is premium, responsive, and includes dynamic animations.
