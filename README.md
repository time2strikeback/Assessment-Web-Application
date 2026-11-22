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
pip install "django>=5.1" django-filter
cd student_grades
python manage.py migrate
python manage.py createsuperuser
python manage.py runserver
```

Then open http://127.0.0.1:8000/.

## Tech

Python · Django 5.1 · django-filter · SQLite
