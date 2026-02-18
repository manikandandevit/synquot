# SynQuot Project Setup Guide

## Problem: Project won't open/run after git clone

### Issues Fixed:
1. ✅ Fixed `.gitignore` merge conflict in frontend
2. ✅ Fixed frontend directory path in Django settings

### Issues to Fix Manually:

## 1. Create Frontend Environment File

The frontend needs a `.env.localenv` file that is not in git (for security).

**Create this file:** `synquote-frontend/.env.localenv`

**Content:**
```
VITE_ADMIN_BASE_URL=http://localhost:8000/api
```

## 2. How to Run the Project

### Backend (Django):
```powershell
cd synquote-backend\backend
python manage.py runserver
```
Backend will run on: http://localhost:8000

### Frontend (React/Vite):
```powershell
cd synquote-frontend
npm run local
```
Frontend will run on: http://localhost:5173

## 3. First Time Setup

### Install Python Dependencies:
```powershell
cd synquote-backend\backend
pip install -r requirements.txt
```

### Install Node Dependencies:
```powershell
cd synquote-frontend
npm install
```

### Run Database Migrations:
```powershell
cd synquote-backend\backend
python manage.py migrate
```

## Why it doesn't work after git clone:

1. **`.env` files are gitignored** - They contain sensitive config and are not in the repository
2. **`node_modules` is gitignored** - Need to run `npm install`
3. **Python packages** - Need to install from `requirements.txt`
4. **Database** - Need to run migrations

## Quick Fix:

Just create the `.env.localenv` file in `synquote-frontend` folder with:
```
VITE_ADMIN_BASE_URL=http://localhost:8000/api
```

Then run:
- Backend: `python manage.py runserver` (from backend folder)
- Frontend: `npm run local` (from frontend folder)

