# 💬 Real-Time Django Chat App

A fully functional **real-time chat application** built with **Django**, **Django Channels**, **TailwindCSS**, and **Alpine.js**. This app supports multiple chatrooms, user authentication, and live messaging with WebSockets.

---

## 🚀 Features

- 🔒 User Authentication (Login/Signup/Logout)
- 💬 Real-time messaging with WebSockets (Django Channels)
- 👥 Create or join chatrooms
- 🚪 Leave chatroom functionality
- 🧼 Clean UI with TailwindCSS
- ⚡ Alpine.js modal for confirmation dialogs
- 🗂️ Fully structured Django app ready for deployment

---

## 📁 Project Structure

\`\`\`
├── a_core/                 # Django project settings and configuration
│   └── __init__.py         # Core app init file (other standard files assumed: settings.py, urls.py, asgi.py, etc.)
├── a_home/                 # Home or landing page app
│   └── (views, urls, models, etc.)  # Files for handling homepage logic
├── a_rtchat/               # Real-time chat application
│   ├── consumers.py        # WebSocket consumers for chat
│   ├── models.py           # Chat-related database models
│   ├── views.py            # Views for handling chat logic
│   └── routing.py          # WebSocket routing for channels
├── a_users/                # User authentication and profile handling
│   └── (models, views, urls, etc.)  # User login, registration, and profile logic
├── media/avatars/          # Uploaded user avatar images
├── static/                 # Static files (CSS, JavaScript, images)
├── templates/              # HTML template files
├── db.sqlite3              # SQLite database file
├── manage.py               # Django’s command-line utility
├── requirements.txt        # List of Python dependencies
├── .gitignore              # Git ignore rules
└── README.md               # Project overview and documentation

\`\`\`

---

## 🔧 Setup Instructions

### 1. Clone the Repository

\`\`\`bash
https://github.com/SujalSongire/Chat_application.git
cd django-realtime-chat
\`\`\`

### 2. Create and Activate Virtual Environment

\`\`\`bash
python -m venv .venv
# On Windows
.venv\Scripts\activate
# On Mac/Linux
source .venv/bin/activate
\`\`\`

### 3. Install Dependencies

\`\`\`bash
pip install -r requirements.txt
\`\`\`

### 4. Run Migrations

\`\`\`bash
python manage.py migrate
\`\`\`

### 5. Create a Superuser (Optional)

\`\`\`bash
python manage.py createsuperuser
\`\`\`

### 6. Run the Development Server

\`\`\`bash
python manage.py runserver
\`\`\`

Now open your browser and go to: \`http://127.0.0.1:8000/\`

---

## 🌐 WebSocket Configuration

Make sure you’re using Django Channels with proper ASGI configuration.

### \`asgi.py\` (in \`a_core/\`)

\`\`\`python
import os
from channels.routing import ProtocolTypeRouter, URLRouter
from django.core.asgi import get_asgi_application
from channels.auth import AuthMiddlewareStack
import a_rtchat.routing

os.environ.setdefault('DJANGO_SETTINGS_MODULE', 'a_core.settings')

application = ProtocolTypeRouter({
    "http": get_asgi_application(),
    "websocket": AuthMiddlewareStack(
        URLRouter(
            a_rtchat.routing.websocket_urlpatterns
        )
    ),
})
\`\`\`

---

## 📦 Requirements

\`\`\`txt
Django>=4.0
channels>=4.0
asgiref>=3.6
\`\`\`

Generate with:

\`\`\`bash
pip freeze > requirements.txt
\`\`\`

---

## 🧪 Testing

\`\`\`bash
python manage.py test
\`\`\`

---

## 📸 UI Snapshot

![Screenshot 2025-06-07 102918](https://github.com/user-attachments/assets/d240a34f-69ea-49be-a5a2-e7fe082055d9)


---

## 📜 License

This project is licensed under the MIT License.

---
