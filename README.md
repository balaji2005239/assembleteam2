# Assemble - Developer Collaboration Platform

A modern platform for developers to collaborate on projects, find teammates for hackathons, and build amazing things together.

## Features

- **Project Collaboration**: Create and discover projects, apply to join teams
- **Hackathon Teams**: Find teammates for hackathons and competitions
- **Real-time Chat**: Communicate with other developers
- **Skills & Roles**: Match based on technical skills and project roles
- **Portfolio**: Showcase your work and projects
- **Notifications**: Stay updated with project activities

## Tech Stack

### Frontend
- React 18 with TypeScript
- Tailwind CSS for styling
- React Router for navigation
- Axios for API calls
- Socket.IO for real-time features
- Lucide React for icons

### Backend
- Flask (Python)
- PostgreSQL database
- SQLAlchemy ORM
- Flask-JWT-Extended for authentication
- Flask-SocketIO for real-time features
- Flask-CORS for cross-origin requests

## Setup Instructions

### Prerequisites
- Node.js 18+ and npm
- Python 3.10+
- PostgreSQL 12+

### Database Setup

1. Install PostgreSQL and create a database:
```sql
CREATE DATABASE assemble;
CREATE USER assemble_user WITH PASSWORD 'your_password';
GRANT ALL PRIVILEGES ON DATABASE assemble TO assemble_user;
```

2. Create a `.env` file in the `backend` directory:
```env
DATABASE_URL=postgresql://assemble_user:your_password@localhost:5432/assemble
JWT_SECRET_KEY=your-secret-key-change-in-production
FLASK_ENV=development
```

### Backend Setup

1. Navigate to the backend directory:
```bash
cd backend
```

2. Create a virtual environment:
```bash
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate
```

3. Install dependencies:
```bash
pip install -r requirements.txt
```

4. Initialize the database:
```bash
python database.py
```

5. Run the Flask application:
```bash
python app.py
```

The backend will be available at `http://localhost:5000`

### Frontend Setup

1. Install dependencies:
```bash
npm install
```

2. Start the development server:
```bash
npm run dev
```

The frontend will be available at `http://localhost:5173`

## Environment Variables

### Backend (.env)
- `DATABASE_URL`: PostgreSQL connection string
- `JWT_SECRET_KEY`: Secret key for JWT tokens
- `FLASK_ENV`: Environment (development/production)

### Optional OAuth (if implementing)
- `GITHUB_CLIENT_ID`: GitHub OAuth client ID
- `GITHUB_CLIENT_SECRET`: GitHub OAuth client secret
- `GOOGLE_CLIENT_ID`: Google OAuth client ID
- `GOOGLE_CLIENT_SECRET`: Google OAuth client secret

## API Endpoints

### Authentication
- `POST /api/auth/register` - User registration
- `POST /api/auth/login` - User login
- `GET /api/auth/me` - Get current user profile
- `PUT /api/auth/me` - Update user profile

### Projects
- `GET /api/projects` - List projects with filtering
- `POST /api/projects` - Create new project
- `GET /api/projects/{id}` - Get project details
- `POST /api/projects/{id}/applications` - Apply to project

### Hackathons
- `GET /api/hackathons` - List hackathon team searches
- `POST /api/hackathons` - Create team search
- `POST /api/hackathons/{id}/applications` - Apply to join team

### Chat
- `GET /api/chat/conversations` - Get user conversations
- `GET /api/chat/messages/{user_id}` - Get messages with user
- `POST /api/chat/messages` - Send message

### Notifications
- `GET /api/notifications` - Get user notifications
- `PUT /api/notifications/{id}/read` - Mark notification as read

## Database Schema

The application uses PostgreSQL with the following main tables:
- `users` - User profiles and authentication
- `projects` - Project information
- `hackathon_posts` - Hackathon team searches
- `project_applications` - Project join applications
- `hackathon_applications` - Team join applications
- `messages` - Chat messages
- `notifications` - User notifications
- `skills` - Available skills/technologies
- `roles` - Available project roles

## Deployment

### Frontend (Netlify)
The frontend can be deployed to Netlify:
```bash
npm run build
```
Deploy the `dist` folder to Netlify.

### Backend (Production)
For production deployment:

1. Set up PostgreSQL database
2. Configure environment variables
3. Install dependencies: `pip install -r requirements.txt`
4. Initialize database: `python database.py`
5. Run with a production WSGI server like Gunicorn:
```bash
gunicorn -w 4 -b 0.0.0.0:5000 app:app
```

## Contributing

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Add tests if applicable
5. Submit a pull request

## License

This project is licensed under the MIT License.