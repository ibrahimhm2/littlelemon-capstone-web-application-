# Little Lemon Web Application

## Capstone Project — Meta Back-End Developer

This repository contains the final project for the [Meta Back-End Developer Capstone Course](https://www.coursera.org/learn/back-end-developer-capstone/).

A robust web application built with **Django**, **Django REST Framework**, **Djoser** (for authentication), and **MySQL**.

---

## Quick Start

### Requirements

- Python 3.8+
- Django 4.x
- Django REST Framework
- Djoser
- MySQL
- All dependencies are listed in `requirements.txt`

### Installation

1. **Clone the repository**

   ```bash
   git clone https://github.com/ibrahimhm2/littlelemon-capstone-web-application-.git
   cd littlelemon-capstone-web-application-
   ```

2. **Create & activate a virtual environment**

   ```bash
   python -m venv venv
   source venv/bin/activate  # On Windows: venv\Scripts\activate
   ```

3. **Install the dependencies**

   ```bash
   pip install -r requirements.txt
   ```

4. **Configure MySQL Database**

   - Create a database (e.g., `littlelemon_db`)
   - Update `settings.py`:
     ```python
     DATABASES = {
         'default': {
             'ENGINE': 'django.db.backends.mysql',
             'NAME': 'littlelemon_db',
             'USER': 'your_mysql_user',
             'PASSWORD': 'your_mysql_password',
             'HOST': 'localhost',
             'PORT': '3306',
         }
     }
     ```

5. **Apply migrations & create superuser**

   ```bash
   python manage.py migrate
   python manage.py createsuperuser
   ```

6. **Run the development server**
   ```bash
   python manage.py runserver
   ```

---

## Static Page

Access a basic static restaurant page at:  
`http://localhost:8000/restaurant/`

---

## API Documentation

All endpoints use `/restaurant/api/` as the root.

### Menu Endpoints

- **`GET /menu/`**  
  View all menu items (authenticated users)
- **`POST /menu/`**  
  Create new menu item (admin only)

  - Fields: `title` (str), `price` (decimal), `featured` (boolean, optional)

- **`GET /menu/<int:pk>/`**  
  View single menu item (authenticated users)
- **`PUT /menu/<int:pk>/` / `DELETE /menu/<int:pk>/`**  
  Update/Delete menu item (admin only)

### Booking Endpoints

- **`GET /book/`**  
  View bookings matching your username

- **`POST /book/`**  
  Book a table (authenticated users)

  - Fields: `name` (str, must match username), `guest_number` (int, optional), `date` (YYYY-MM-DD), `comment` (text, optional)

- **`GET /book/<int:pk>/`**  
  View a booking (admin only)
- **`DELETE /book/<int:pk>/`**  
  Delete a booking (admin only)

---

## Authentication

- **Registration/Login**: Provided by Djoser (`/auth/` endpoints, see Djoser docs)
- Most endpoints require authentication (Token or Session)
- Example users for testing:

| Role     | Username  | Password   |
| -------- | --------- | ---------- |
| Admin    | admin     | 123        |
| Customer | customer1 | lemon@123! |
| Customer | customer2 | lemon@123! |

---

## Running Tests

```bash
python manage.py test
```
