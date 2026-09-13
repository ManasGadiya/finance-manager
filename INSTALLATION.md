# Installation Guide

## Prerequisites

Before you begin, ensure you have the following installed:
- Node.js (v14 or higher)
- npm or yarn
- MongoDB (local or cloud instance)
- Git

## Step-by-Step Setup

### 1. Clone the Repository

```bash
git clone https://github.com/ManasGadiya/finance-manager.git
cd finance-manager
```

### 2. Backend Setup

#### 2.1 Navigate to Backend Directory
```bash
cd backend
```

#### 2.2 Install Dependencies
```bash
npm install
```

#### 2.3 Create Environment File
Create a `.env` file in the `backend` directory:
```bash
cp .env.example .env
```

#### 2.4 Update Environment Variables
Edit the `.env` file and add your MongoDB connection string and JWT secret:
```
MONGODB_URI=mongodb+srv://your_username:your_password@your_cluster.mongodb.net/finance-manager
JWT_SECRET=your_super_secret_key_here
PORT=5000
NODE_ENV=development
```

#### 2.5 Start the Backend Server
```bash
npm start
```

For development with auto-reload:
```bash
npm run dev
```

The backend server should start on `http://localhost:5000`

### 3. Frontend Setup

#### 3.1 Navigate to Frontend Directory (from the root)
```bash
cd frontend
```

#### 3.2 Install Dependencies
```bash
npm install
```

#### 3.3 Start the Frontend Development Server
```bash
npm start
```

The frontend will open automatically on `http://localhost:3000`

## MongoDB Setup

### Option 1: Using MongoDB Atlas (Cloud)
1. Go to [MongoDB Atlas](https://www.mongodb.com/cloud/atlas)
2. Create an account and sign in
3. Create a new cluster
4. Create a database user and get the connection string
5. Whitelist your IP address
6. Copy the connection string and paste it in your `.env` file

### Option 2: Using Local MongoDB
1. Install MongoDB locally
2. Start MongoDB service
3. Use `mongodb://localhost:27017/finance-manager` as your connection string

## Testing the API

You can test the API endpoints using Postman or any API client:

### 1. Register a New User
```
POST http://localhost:5000/api/auth/register
Content-Type: application/json

{
  "name": "John Doe",
  "email": "john@example.com",
  "password": "password123"
}
```

### 2. Login
```
POST http://localhost:5000/api/auth/login
Content-Type: application/json

{
  "email": "john@example.com",
  "password": "password123"
}
```

### 3. Add an Expense
```
POST http://localhost:5000/api/expenses
Authorization: Bearer YOUR_JWT_TOKEN
Content-Type: application/json

{
  "description": "Groceries",
  "amount": 50.99,
  "category": "Food",
  "notes": "Weekly grocery shopping"
}
```

## Troubleshooting

### Backend Issues
- **MongoDB Connection Error**: Check your MONGODB_URI in .env
- **Port Already in Use**: Change PORT in .env or kill the process using the port
- **Dependencies Not Installing**: Try deleting node_modules and running npm install again

### Frontend Issues
- **Port 3000 Already in Use**: The CLI will prompt to use a different port
- **API Connection Error**: Make sure the backend server is running on localhost:5000

### General Issues
- Check that both backend and frontend servers are running
- Verify MongoDB is connected
- Clear browser cache if experiencing issues
- Check browser console for errors

## Next Steps

1. Add more features (budget, reports, etc.)
2. Implement data validation
3. Add unit and integration tests
4. Deploy to production (Heroku for backend, Vercel for frontend)
5. Add authentication refresh token logic
6. Implement email notifications

## Support

For issues or questions, please open an issue on GitHub or contact the project maintainer.
