# 🌶️ Lutenitsa Appraiser 🍅

A web app for rating and discussing lutenitsa brands. Authenticated users can register, log in, submit appraisals, and comment on reviews.

## ✨ Features
- 🔐 User authentication with Supabase
- ✍️ Create appraisals with brand, rating, and notes
- 💬 Add comments to existing appraisals
- 📱 Responsive UI built with Angular Material
- ⚡ State management with Angular signals and RxJS
- 🧠 Error handling through a centralized service

## 🚀 Quick Start
1. Install dependencies:
   ```bash
   npm install
   ```
2. Configure Supabase credentials in `src/environments/environment.ts`.
3. Run the app:
   ```bash
   ng serve
   ```
4. Open the browser at `http://localhost:4200`.

## 🧩 App Architecture
- `src/app/components/` — UI components and page views
- `src/app/core/services/` — services for auth, data, error handling, and Supabase client
- `src/app/models/` — typings for appraise, comment, extended appraise, and user objects
- `src/app/utils/` — reusable form helpers
- `src/environments/` — environment-specific configuration

## 🔐 Authentication Flow
- Users sign up or log in using Supabase Auth.
- Successful login stores the current user in local state and localStorage.
- Authenticated actions such as creating appraisals and comments use the active Supabase session.

## 🗄️ Database Schema
### `appraises`
- `id`
- `brand_name`
- `rating`
- `appraise`
- `user_id`
- `created_at`

### `comments`
- `id`
- `appraise_id`
- `user_id`
- `comment_text`
- `created_at`

### `profiles`
- `id`
- `email`

## 🛠️ Tech Stack
### Frontend
- Angular 20
- TypeScript
- Angular Material
- RxJS

### Backend
- Supabase (PostgreSQL)
- Row-Level Security
- JWT Authentication
- Realtime API

## ⚙️ Key Services
- `AuthService` — handles login, registration, logout, and user session state
- `AppraiseService` — loads appraisals, comments, and performs CRUD operations
- `SupabaseService` — initializes and provides the Supabase client
- `ErrorService` — centralizes error reporting

## ✅ Notes
- Ensure SUPABASE_URL and SUPABASE_ANON_KEY are set correctly for Supabase access.
- The app relies on Supabase auth session state, so expired or missing sessions will prevent authenticated calls.
- If `getUserId()` returns `null`, verify that the user is logged in and that Supabase has an active session.

## 📚 Recommended Improvements
- Add pagination or search filters for appraisals
- Support user profile editing
- Add real-time updates for comments
- Improve form validation and user feedback
