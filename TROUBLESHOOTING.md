# Troubleshooting Guide

## "Failed to fetch" Error

### Common Causes and Solutions

#### 1. Port Mismatch
**Problem:** Frontend and backend are running on different ports.

**Solution:**
- Check your `frontend/.env` file - it should have: `VITE_API_URL=http://localhost:3000`
- Make sure your backend is running on port 3000
- Restart both frontend and backend after changing ports

#### 2. Backend Not Running
**Problem:** The backend server is not started.

**Solution:**
```bash
cd backend
npm run dev
```
You should see: `Ready on http://localhost:3000`

#### 3. CORS Issues
**Problem:** Browser blocking requests due to CORS.

**Solution:** The middleware is already configured, but if issues persist:
- Check browser console for CORS errors
- Verify middleware.ts is properly set up

#### 4. Database Connection Issues
**Problem:** MongoDB connection failing.

**Solution:**
- Verify MongoDB is running (local or Atlas)
- Check `DATABASE_URL` in `backend/.env`
- Test connection: `npm run prisma:studio`

#### 5. Environment Variables Not Loaded
**Problem:** Frontend not reading `.env` file.

**Solution:**
- Make sure `.env` file is in `frontend/` directory (not `frontend/src/`)
- Restart the Vite dev server after creating/modifying `.env`
- Vite requires `VITE_` prefix for environment variables

## Quick Diagnostic Steps

1. **Check Backend is Running:**
   ```bash
   curl http://localhost:3000/api/auth/register
   ```
   Should return an error (method not allowed), not "connection refused"

2. **Check Frontend Environment:**
   - Open browser console (F12)
   - Check Network tab for failed requests
   - Verify the request URL matches your backend port

3. **Verify Ports:**
   - Backend: Should be on port 3000
   - Frontend: Should be on port 5173 (Vite default)
   - Frontend `.env`: Should point to `http://localhost:3000`

## Still Having Issues?

1. Clear browser cache and localStorage
2. Restart both servers
3. Check terminal for error messages
4. Verify all environment variables are set correctly

