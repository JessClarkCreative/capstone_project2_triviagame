# Trivia Master

A full-stack trivia game application that tests your knowledge across multiple categories.

🎮 [Play Now](https://trivia-frontend-1ods.onrender.com/)

## Project Details

This interactive trivia game features:
- 3 rounds of trivia (5 questions each)
- Real-time score tracking
- Global leaderboard
- Personal score history
- User authentication

### Database Schema

```mermaid
erDiagram
    User ||--o{ Score : has
    User {
        int id PK
        string email "unique"
        string username "unique"
        string password "hashed"
        datetime createdAt
        datetime updatedAt
    }
    Score {
        int id PK
        int score
        int userId FK
        datetime createdAt
        datetime updatedAt
    }
```

The database design features:
- Users can have multiple scores (one-to-many relationship)
- Email and username uniqueness enforcement
- Secure password hashing with bcrypt
- Automatic timestamp tracking for all records

## Tech Stack

- **Frontend**: React with Semantic UI
- **Backend**: Node.js/Express
- **Database**: PostgreSQL with Prisma ORM
- **Authentication**: JWT

## Local Setup

1. Clone the repository:
```bash
git clone https://github.com/JessClarkCreative/capstone_project2_triviagame
cd trivia-master
```

2. Set up the backend:
```bash
cd backend
npm install

# Create a .env file with:
DATABASE_URL="postgresql://postgres:postgres@localhost:5432/db_trivia"
JWT_SECRET="your-secret-key"

# Run migrations
npx prisma migrate dev

# Start the server
npm run dev
```

3. Set up the frontend:
```bash
cd ../frontend
npm install
npm run dev
```

4. Visit `http://localhost:5173` in your browser

## Project Structure
```
├── frontend/          # React application
│   ├── src/
│   │   ├── components/
│   │   └── App.jsx
│   └── README.md      # Frontend setup details
├── backend/           # Express server
│   ├── routes/
│   ├── prisma/
│   └── README.md      # Backend setup details
```

## Key Components

### Frontend
- `TriviaGame.jsx`: Core game logic and user interface
- `Leaderboard.jsx`: Displays global rankings and personal scores
- `App.jsx`: Main application layout and routing
- `Login.jsx`/`Signup.jsx`: User authentication forms

### Backend
- `authRoutes.js`: Authentication endpoints
- `scoreRoutes.js`: Score tracking and retrieval
- `leaderboardRoutes.js`: Global rankings
- `schema.prisma`: Database schema definition

## Testing

Run frontend tests:
```bash
cd frontend
npm test
```

## Troubleshooting

### Database Connection Issues
- Verify PostgreSQL is running
- Check DATABASE_URL in .env file
- Try `npx prisma migrate reset` if schema is out of sync

### Port Conflicts
- Backend default: port 5000
- Frontend default: port 5173
- Configure ports in respective .env files if needed

## Features to Test
1. User Registration/Login
2. Complete game flow (3 rounds)
3. Score saving
4. Leaderboard updates
5. Personal score history

## Contact

Need help or want to report an issue? 
Contact: [jessclarkcreative@gmail.com]