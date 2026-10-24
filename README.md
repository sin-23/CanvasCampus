# Canvas Campus

Canvas Campus is a Django-based learning management system with course-related functionality. The project uses Django and SQLite for local development.

## Requirements

- Windows with Python 3.13 installed
- Git (if cloning the repository)

**Use Python 3.13 for this project.** The project currently uses Django 5.1.2, and running it with Python 3.14 caused an error when opening the Django admin's Add Course page.

## Setup

Open PowerShell in the project directory—the folder containing `manage.py`.

### 1. Create and activate a virtual environment

```powershell
py -3.13 -m venv venv313
.\venv313\Scripts\Activate.ps1
python --version
```

Confirm that the version shown is Python 3.13.x.

If PowerShell blocks activation, run this command in the same terminal and then activate the environment again:

```powershell
Set-ExecutionPolicy -Scope Process -ExecutionPolicy RemoteSigned
.\venv313\Scripts\Activate.ps1
```

### 2. Install dependencies

```powershell
python -m pip install --upgrade pip
pip install -r requirements.txt
```

### 3. Apply database migrations

```powershell
python manage.py migrate
```

The local development configuration uses SQLite. Django creates or updates the `db.sqlite3` database file in the configured location.

### 4. Create an administrator account

```powershell
python manage.py createsuperuser
```

Follow the prompts to set the username, email address, and password. If you already have an administrator account, you can skip this step.

### 5. Check the project and start the server

```powershell
python manage.py check
python manage.py runserver
```

Open the site at:

- Main site: http://127.0.0.1:8000/
- Django admin: http://127.0.0.1:8000/admin/

To stop the development server, press `Ctrl+C` in the terminal.

## Starting the project again

Whenever you reopen the project, activate the existing Python 3.13 environment before running Django:

```powershell
.\venv313\Scripts\Activate.ps1
python manage.py runserver
```

You only need to create the virtual environment and install dependencies during initial setup, or when rebuilding the environment.

## Troubleshooting

- **Django admin returns an error involving `context.py`, `copy.py`, or `AttributeError`**: Confirm that the project is running in the Python 3.13 environment. Run `python --version` in the activated terminal.
- **`No module named ...`**: Activate `venv313` and run `pip install -r requirements.txt` again.
- **`No such file or directory: manage.py`**: Change to the project directory containing `manage.py`.
- **Database changes are not applied**: Run `python manage.py migrate`.
- **The site is not loading**: Make sure the development server is running and use the HTTP address `http://127.0.0.1:8000/`, not HTTPS.

## Notes

- Do not commit your virtual environment folder (`venv313`) or local database (`db.sqlite3`) to version control.
- Keep passwords, email credentials, secret keys, and other private configuration out of the repository.
- This setup is for local development; Django's development server is not intended for production deployment.
