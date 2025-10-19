# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

A production-ready React + Vite template for building Firebase-integrated applications. This template includes essential packages and structure for full-stack Firebase development with modern React patterns.

## Technology Stack

- **Build Tool**: Vite (using rolldown-vite 7.1.14 variant)
- **Framework**: React 19.1.1
- **Language**: JavaScript (JSX)
- **Linting**: ESLint 9 with React Hooks and React Refresh plugins
- **State Management**: Redux Toolkit (@reduxjs/toolkit 2.9.1) + React-Redux 9.2.0
- **Routing**: React Router DOM 7.9.4
- **Backend**: Firebase 12.4.0 (Auth, Firestore, Storage, etc.)
- **Icons**: React Icons 5.5.0

## Development Commands

```bash
# Start development server with HMR
npm run dev
# or
yarn dev

# Build for production
npm run build
# or
yarn build

# Preview production build locally
npm run preview
# or
yarn preview

# Run linter
npm run lint
# or
yarn lint
```

## Project Structure

```
firebase-react-template/
├── src/
│   ├── main.jsx              # Application entry point
│   ├── App.jsx               # Root component
│   ├── styles/               # CSS styles
│   │   ├── index.css         # Global styles
│   │   └── App.css           # App component styles
│   ├── components/           # Reusable React components (to be created)
│   ├── pages/                # Page components for routing (to be created)
│   ├── features/             # Redux slices and feature logic (to be created)
│   ├── firebase/             # Firebase config and services (to be created)
│   ├── hooks/                # Custom React hooks (to be created)
│   ├── utils/                # Helper functions (to be created)
│   └── assets/               # Static assets (images, icons, etc.)
├── public/                   # Public static files served at root
├── index.html                # HTML entry point
├── vite.config.js            # Vite configuration
└── eslint.config.js          # ESLint configuration
```

## Architecture Notes

### Entry Point Flow
1. `index.html` loads `/src/main.jsx` as a module
2. `main.jsx` renders the `<App />` component into `#root` div with StrictMode
3. App component is the top-level React component

### Vite Configuration
- Uses `@vitejs/plugin-react` with Babel for Fast Refresh (switches to oxc when using rolldown-vite)
- Note: This project uses `rolldown-vite@7.1.14` instead of standard Vite (see package.json resolutions)

### ESLint Configuration
- Uses ESLint 9 flat config format (not legacy .eslintrc)
- Configured for React Hooks best practices
- React Refresh integration for Vite HMR
- Custom rule: `no-unused-vars` ignores uppercase/underscore prefixed variables
- Ignores `dist` directory

## Recommended Project Organization

### Firebase Setup
- Create `src/firebase/config.js` for Firebase initialization
- Use environment variables for Firebase credentials (`.env` file with `VITE_` prefix)
- Create service files in `src/firebase/` for different Firebase features:
  - `auth.js` - Authentication methods
  - `firestore.js` - Firestore database operations
  - `storage.js` - Firebase Storage operations

### Redux State Management
- Store configuration in `src/store/store.js`
- Feature slices in `src/features/` directory (e.g., `authSlice.js`, `userSlice.js`)
- Use Redux Toolkit's `createSlice` and `createAsyncThunk` for async Firebase operations
- Combine Redux with Firebase for centralized state management

### Routing Structure
- Define routes in `App.jsx` using React Router
- Page components in `src/pages/` (e.g., `Home.jsx`, `Login.jsx`, `Dashboard.jsx`)
- Protected routes for authenticated pages
- Use `useNavigate` and `useParams` hooks from react-router-dom

### Component Guidelines
- Shared/reusable components in `src/components/`
- Page-specific components can live in `src/pages/[pageName]/components/`
- Use React Icons for consistent iconography
- Keep components small and focused

### Environment Variables
- Vite requires `VITE_` prefix for environment variables
- Create `.env` file (add to `.gitignore`)
- Example Firebase env variables:
  ```
  VITE_FIREBASE_API_KEY=...
  VITE_FIREBASE_AUTH_DOMAIN=...
  VITE_FIREBASE_PROJECT_ID=...
  ```
