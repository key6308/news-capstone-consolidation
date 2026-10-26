# Django News Application — Capstone Consolidation

This Django project includes role-based accounts, article submission and approval,
newsletters, subscriptions, email notifications, a token-authenticated REST API,
automated tests, Sphinx documentation, and Docker support.

## 1. Get the project

Clone your public GitHub repository, then enter its folder:

```powershell
git clone https://github.com/YOUR_GITHUB_USERNAME/YOUR_REPOSITORY_NAME.git
cd YOUR_REPOSITORY_NAME
```

Replace the example username and repository name with the real values.

## 2. Run locally (Windows PowerShell)

Install Python 3.12, then from the project root run:

```powershell
python -m venv venv
.\venv\Scripts\Activate.ps1
python -m pip install -r requirements.txt
```

Create a MySQL/MariaDB database named `news_capstone` and a database user with
permissions on it. Set the variables in `.env.example` in your local environment
using your own database credentials. Do not commit a real `.env` file or secrets.

Run migrations (this creates the Django tables inside the database), tests, and
the development server:

```powershell
python manage.py check
python manage.py migrate
python manage.py test
python manage.py runserver
```

Open `http://127.0.0.1:8000/`.

## 3. Run with Docker

The Docker setup is independent of the local Python virtual environment and
includes a MariaDB database. Install Docker Desktop (Windows/macOS) or Docker
Engine plus Docker Compose (Linux). From the project root, run:

```powershell
docker compose up --build
```

The database is created automatically by the Compose configuration. Django
runs migrations when the web container starts. Open `http://127.0.0.1:8000/`.
Stop with `Ctrl+C`, then run `docker compose down`. To also delete the local
database volume and its data, run `docker compose down -v`.

The default Compose passwords are for local learning only. Set `DB_PASSWORD`,
`DB_ROOT_PASSWORD`, and `DJANGO_SECRET_KEY` to your own values before using
this outside your own machine. Never publish production secrets.

## Sphinx documentation

Install requirements in your active virtual environment, then run:

```powershell
python -m sphinx -b html docs docs/_build/html
```

Open `docs/_build/html/index.html`. The generated documentation is organized
into separate pages in the `docs/` folder and uses the Read the Docs theme.

## API token

Request a token at `http://127.0.0.1:8000/api/token/` and send it in the header
`Authorization: Token YOUR_TOKEN`. Use your own token and do not publish it.

## Demo data

Run `python manage.py seed_demo` to create local demo accounts and sample content.
The command prints the shared demo password. These credentials are only for
local testing and must never be used in a public or production deployment.

## GitHub submission

The task folder must contain `capstone.txt` with the URL of your actual public
GitHub repository. Make sure the URL works in a private/incognito browser window.
