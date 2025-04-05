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
├── a_core/                 # Django project settings
├── a_rtchat/               # Main chat app
│   ├── consumers.py        # WebSocket consumers
│   ├── models.py           # Database models
│   ├── views.py            # Views for chatroom logic
│   └── routing.py          # Channels routing
├── static/                 # Static assets (CSS, JS, etc.)
├── templates/              # HTML templates
├── manage.py               # Django management CLI
├── requirements.txt        # Python dependencies
└── README.md               # You're here!
\`\`\`

---

## 🔧 Setup Instructions

### 1. Clone the Repository

\`\`\`bash
git clone https://github.com/your-username/django-realtime-chat.git
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

*Add a screenshot or demo GIF of the chat interface here.*

---

## 📜 License

This project is licensed under the MIT License.

---

## 🤝 Contributing

Pull requests are welcome! For major changes, open an issue first to discuss what you'd like to change.

---

## 📫 Contact

**Your Name**  
Email: [your.email@example.com](mailto:your.email@example.com)  
GitHub: [github.com/your-username](https://github.com/your-username)
EOF
