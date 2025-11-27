# Quick Setup Guide

## Step-by-Step Setup

### 1. Install Dependencies

**Backend:**
```bash
cd backend
npm install
```

**Frontend:**
```bash
cd frontend
npm install
```

### 2. Configure Environment Variables

**Backend** - Create `backend/.env`:
```env
DATABASE_URL="mongodb://localhost:27017/taskmanager?directConnection=true"
JWT_SECRET="your-super-secret-jwt-key-change-this-in-production"
JWT_EXPIRES_IN="7d"
BCRYPT_SALT_ROUNDS="10"
```

**Frontend** - Create `frontend/.env`:
```env
VITE_API_URL=http://localhost:3001
```

### 3. Setup Database

```bash
cd backend
npm run prisma:generate
npm run db:push
```

### 4. Run the Application

**Terminal 1 - Backend:**
```bash
cd backend
npm run dev
```

**Terminal 2 - Frontend:**
```bash
cd frontend
npm run dev
```

### 5. Access the Application

- Frontend: http://localhost:5173
- Backend API: http://localhost:3001

## First Test

1. Open http://localhost:5173
2. Click "Register" and create an account
3. Login with your credentials
4. Create your first task!

## Common Issues

**MongoDB not running?**
- Install MongoDB locally or use Docker: `docker run -d -p 27017:27017 --name mongodb mongo:latest`
- Or use MongoDB Atlas (cloud) and update DATABASE_URL

**Port 3001 already in use?**
- Change port in `backend/package.json` scripts
- Update `VITE_API_URL` in frontend `.env` to match

**Prisma errors?**
- Run: `cd backend && npm run prisma:generate`

