# Vault Times – Django News Platform

Vault Times is a role-based news publishing platform built with Django and Django REST Framework.
It supports multiple user roles, article workflows, subscriptions, newsletters, and API access.

---

## Features

* **Role-based system**

  * Reader: subscribes to publishers/journalists and views content
  * Journalist: creates and manages articles/newsletters
  * Editor: reviews and approves articles
  * Publisher: manages organization and staff

* **Article workflow**

  * Journalists submit articles
  * Editors approve articles before publication

* **Subscriptions**

  * Readers can follow publishers and journalists
  * Personalized article feed

* **Newsletter system**

  * Create and manage newsletters
  * Include multiple articles

* **Email notifications**

  * When an article is approved, subscribers are notified
  * Emails are printed to the console (development mode)

* **REST API**

  * JWT authentication
  * Article and newsletter endpoints
  * Subscription-based filtering

---

## Tech Stack

* Django
* Django REST Framework
* MariaDB / MySQL
* SimpleJWT (authentication)

---

## Installation & Setup

### 1. Clone the Repository

```bash
git clone https://github.com/your-username/vault-times.git
cd news_project
```

---

### 2. Create Virtual Environment

```bash
python -m venv venv
```

#### Activate it:

**Windows:**

```bash
venv\Scripts\activate
```

**Mac/Linux:**

```bash
source venv/bin/activate
```

---

### 3. Install Dependencies

```bash
pip install -r requirements.txt
```

---

## Database Setup (MariaDB / MySQL)

This project uses **MariaDB/MySQL**.

---

### 1. Install MariaDB

Download from:
https://mariadb.org/download/

---

### 2. Create Database

```bash
mysql -u root -p
```

Then run:

```sql
CREATE DATABASE newsapp_db;
```

---

### 3. Install MySQL Driver

```bash
pip install mysqlclient
```

---

### 4. Configure Database

Open:

```
news_project/settings.py
```

Ensure your database config looks like:

```python
DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.mysql',
        'NAME': 'newsapp_db',
        'USER': 'root',
        'PASSWORD': 'zg090521',
        'HOST': 'localhost',
        'PORT': '3306',
    }
}
```

---

### 5. Apply Migrations

```bash
python manage.py migrate
```

---

## Running the Server

```bash
python manage.py runserver
```

Visit:

```
http://127.0.0.1:8000/
```

---

## Authentication (API)

The API uses **JWT authentication**.

### Obtain Token:

```
POST /api/token/
```

### Refresh Token:

```
POST /api/token/refresh/
```

---

## API Endpoints

| Endpoint                    | Description                |
| --------------------------- | -------------------------- |
| `/api/articles/`            | List or create articles    |
| `/api/articles/<id>/`       | Retrieve/update/delete     |
| `/api/articles/subscribed/` | Subscribed content         |
| `/api/newsletters/`         | List or create newsletters |
| `/api/approved/`            | Approval webhook endpoint  |

---

## Email Functionality

When an article is approved:

* Emails are sent to subscribed users
* In development, emails are printed to the console

Example output appears in the terminal when running the server.

---

## User Roles

| Role       | Permissions                 |
| ---------- | --------------------------- |
| Reader     | View subscribed content     |
| Journalist | Create/edit own articles    |
| Editor     | Approve and manage articles |
| Publisher  | Manage organization         |

---

## Running Tests

```bash
python manage.py test
```

---

## Project Structure

```
├── news_project/
│   ├── api/
│   ├── news_project/
│   ├── templates/
│   ├── static/
│   ├── manage.py
│   ├── requirements.txt
│
├── README.md
```

---

## ⚠️ Notes

* Ensure MariaDB is running before starting the server

---

## Summary

This project demonstrates:

* Full-stack Django development
* Role-based access control
* REST API design
* Database integration (MariaDB)
* Event-driven features (email + approval system)

---

## Author

giavassallo
