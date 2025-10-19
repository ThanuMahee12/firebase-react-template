# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a React + Vite template project intended as a starting point for Firebase-integrated React applications. Currently, it contains a minimal Vite + React setup with HMR (Hot Module Replacement) and ESLint configuration.

**Important**: Despite the name "firebase-react-template", Firebase integration is NOT yet implemented. This is a vanilla React + Vite template awaiting Firebase setup.

## Technology Stack

- **Build Tool**: Vite (using rolldown-vite 7.1.14 variant)
- **Framework**: React 19.1.1
- **Language**: JavaScript (JSX)
- **Linting**: ESLint 9 with React Hooks and React Refresh plugins

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
│   ├── main.jsx           # Application entry point
│   ├── App.jsx            # Root component
│   ├── index.css          # Global styles
│   ├── App.css            # App component styles
│   └── assets/            # Static assets (images, etc.)
├── public/                # Public static files served at root
├── index.html             # HTML entry point
├── vite.config.js         # Vite configuration
└── eslint.config.js       # ESLint configuration
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

## Future Firebase Integration

When adding Firebase to this template:
- Firebase SDK should be initialized in a dedicated config file (e.g., `src/firebase/config.js`)
- Consider using environment variables for Firebase config (create `.env` file, add to `.gitignore`)
- Authentication state management should likely be done via React Context
- Firestore/Database queries should be abstracted into service/hook files
