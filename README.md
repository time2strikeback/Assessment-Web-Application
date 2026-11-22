# Student Grades: Django Assessment App

A small Django web app for recording student grades by subject. Each record gets an
automatic **PASS** or **FAIL** remark, and the list can be filtered.

## Features

- Add, edit and delete student grade records.
- Grades of **75 or more** are marked `PASS`; anything lower is `FAIL`. Remarks are
  set automatically on save and can't be edited by hand.
- Filter the student list with [django-filter](https://django-filter.readthedocs.io/).
- Manage subjects through the Django admin.

## Data model

| Model | Fields |
|---|---|
| `Subject` | `subject_key` (PK), `subject_name` |
| `Student` | `student_key` (PK), `student_name`, `subject` → Subject, `grade`, `remarks` |

## Routes

| URL | View |
|---|---|
| `/` | Student list with filters |
| `/new/` | Add a record |
| `/edit/<id>/` | Edit a record |
| `/delete/<id>/` | Delete a record |

## Run locally

Requires Python 3.12+.

```
pip install -r requirements.txt
cd student_grades
python manage.py migrate
python manage.py createsuperuser
```

Turn on debug mode for local development, then start the server.

PowerShell:

```
$env:DJANGO_DEBUG = "1"
python manage.py runserver
```

macOS / Linux:

```
DJANGO_DEBUG=1 python manage.py runserver
```

Then open http://127.0.0.1:8000/.

## Configuration

| Variable | Default | Purpose |
|---|---|---|
| `DJANGO_SECRET_KEY` | an insecure development key | Set a real secret for any deployment |
| `DJANGO_DEBUG` | `0` (off) | Set to `1` for local development |
| `DJANGO_ALLOWED_HOSTS` | `localhost,127.0.0.1` | Comma-separated host names |

The SQLite database is created locally by `migrate` and isn't committed.

## Tech

Python · Django 5.1 · django-filter · SQLite
