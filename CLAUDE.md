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
│   ├── components/           # Reusable React components
│   ├── pages/                # Page components for routing
│   ├── layouts/              # Layout wrapper components
│   ├── routes/               # Route configuration and protected routes
│   ├── slices/               # Redux Toolkit slices
│   ├── features/             # Redux features (alternative to slices)
│   ├── store/                # Redux store configuration
│   ├── firebase/             # Firebase config and services
│   ├── hooks/                # Custom React hooks
│   ├── utils/                # Helper functions and utilities
│   └── assets/               # Static assets (images, icons, fonts)
├── public/                   # Public static files served at root
├── index.html                # HTML entry point
├── vite.config.js            # Vite configuration
├── eslint.config.js          # ESLint configuration
└── CLAUDE.md                 # AI assistant guidance
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
- Redux slices in `src/slices/` directory (e.g., `authSlice.js`, `userSlice.js`, `themeSlice.js`)
- Alternative: Use `src/features/` for feature-based organization
- Use Redux Toolkit's `createSlice` and `createAsyncThunk` for async Firebase operations
- Combine Redux with Firebase for centralized state management

### Routing Structure
- Route configuration in `src/routes/index.jsx`
- Protected/Public route wrappers in `src/routes/` (e.g., `ProtectedRoute.jsx`)
- Page components in `src/pages/` (e.g., `Home.jsx`, `Login.jsx`, `Dashboard.jsx`)
- Use `createBrowserRouter` from react-router-dom for route configuration
- Use `useNavigate` and `useParams` hooks for navigation

### Layout Structure
- Layout components in `src/layouts/` (e.g., `MainLayout.jsx`, `AuthLayout.jsx`, `DashboardLayout.jsx`)
- Wrap page components with appropriate layouts
- Include common elements like headers, footers, sidebars in layouts

### Component Guidelines
- Shared/reusable components in `src/components/` (e.g., `Button.jsx`, `Modal.jsx`, `Navbar.jsx`)
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
  VITE_FIREBASE_STORAGE_BUCKET=...
  VITE_FIREBASE_MESSAGING_SENDER_ID=...
  VITE_FIREBASE_APP_ID=...
  ```

## Firebase Integration

### Configuration Files
- `firebase.json` - Firebase Hosting and services configuration
- `firestore.rules` - Firestore security rules (deployed with `firebase deploy --only firestore`)
- `firestore.indexes.json` - Firestore indexes configuration
- `storage.rules` - Storage security rules (deployed with `firebase deploy --only storage`)
- `.firebaserc` - Firebase project ID configuration
- `src/firebase/config.js` - Firebase SDK initialization

### Firebase Services Available
- **Authentication** - Email/Password, Google Sign-in, Password Reset
- **Firestore Database** - NoSQL cloud database with real-time updates
- **Storage** - File uploads and downloads
- **Hosting** - Static file hosting with CDN

### Security Rules Pattern
```javascript
// Firestore example
match /users/{userId} {
  allow read: if request.auth != null;
  allow write: if request.auth.uid == userId;
}

// Storage example
match /users/{userId}/{allPaths=**} {
  allow read, write: if request.auth.uid == userId;
}
```

## Deployment

### Manual Deployment
```bash
npm run build              # Build for production
firebase deploy           # Deploy everything
firebase deploy --only hosting   # Deploy hosting only
```

### CI/CD with GitHub Actions
- See [GitHub Actions Wiki](https://github.com/ThanuMahee12/firebase-react-template/wiki/GitHub-Actions)
- Configure secrets in repository settings
- Automatic deployment on push to main branch

## Documentation

### Wiki Resources
Complete documentation available at: https://github.com/ThanuMahee12/firebase-react-template/wiki

Essential pages:
- **Setup Guide** - Complete installation and configuration
- **Firebase Configuration** - Set up Firebase services
- **API Reference** - Complete API documentation
- **Deployment Guide** - Deploy to Firebase Hosting
- **GitHub Actions** - Automated CI/CD setup
- **Email Templates** - Customize Firebase auth emails
- **Firebase Limitations** - Free tier quotas and optimization

### Development Workflow
1. Read [Setup Guide](https://github.com/ThanuMahee12/firebase-react-template/wiki/Setup-Guide)
2. Configure Firebase credentials in `.env`
3. Update `.firebaserc` with your project ID
4. Start development: `npm run dev`
5. Deploy when ready: `firebase deploy`

## Common Tasks

### Adding a New Page
1. Create component in `src/pages/` (e.g., `About.jsx`)
2. Add route in `src/routes/index.jsx`
3. Optionally wrap with layout component

### Adding Redux State
1. Create slice in `src/slices/` (e.g., `userSlice.js`)
2. Add reducer to `src/store/store.js`
3. Use in components with `useSelector` and `useDispatch`

### Adding Firebase Service
1. Create service file in `src/firebase/` (e.g., `auth.js`)
2. Import Firebase modules
3. Export service functions
4. Use in components or Redux thunks

### Working with Firestore
```javascript
import { collection, addDoc, getDocs } from 'firebase/firestore'
import { db } from './firebase/config'

// Add document
await addDoc(collection(db, 'items'), { name: 'Item' })

// Get documents
const snapshot = await getDocs(collection(db, 'items'))
```

### Working with Authentication
```javascript
import { signInWithEmailAndPassword } from 'firebase/auth'
import { auth } from './firebase/config'

// Sign in
await signInWithEmailAndPassword(auth, email, password)
```

## Best Practices

### Code Organization
- One component per file
- Keep components small (< 200 lines)
- Use custom hooks for reusable logic
- Organize imports: React → Third-party → Local

### State Management
- Use Redux for global state (user, theme, etc.)
- Use local state for component-specific data
- Use React Context sparingly

### Firebase Best Practices
- Always use environment variables
- Implement proper security rules
- Handle errors gracefully
- Use Firestore queries efficiently
- Monitor usage in Firebase Console

### Performance
- Use React.memo for expensive components
- Implement code splitting with React.lazy
- Optimize images before uploading to Storage
- Use Firestore pagination for large datasets

## Troubleshooting

### Common Issues

**Build fails with "env variable not found"**
- Ensure all `VITE_FIREBASE_*` variables are in `.env`
- Restart dev server after changing `.env`

**Firebase permission denied**
- Check `firestore.rules` and `storage.rules`
- Verify user is authenticated
- Deploy rules: `firebase deploy --only firestore,storage`

**Deployment fails**
- Run `firebase login` to re-authenticate
- Verify `.firebaserc` has correct project ID
- Ensure `npm run build` succeeds locally

## Resources

- [Repository README](README.md) - Quick start guide
- [Wiki Documentation](https://github.com/ThanuMahee12/firebase-react-template/wiki) - Complete docs
- [Contributing Guide](CONTRIBUTING.md) - How to contribute
- [Firebase Docs](https://firebase.google.com/docs) - Official Firebase documentation
- [React Docs](https://react.dev) - Official React documentation
- [Redux Toolkit Docs](https://redux-toolkit.js.org) - Redux state management
- [Vite Docs](https://vitejs.dev) - Build tool documentation

## Template Maintenance

### Updating Dependencies
```bash
npm update           # Update to latest minor/patch versions
npm outdated         # Check for newer versions
```

### Firebase CLI
```bash
firebase --version   # Check Firebase CLI version
npm install -g firebase-tools  # Update Firebase CLI
```

## Support

- 🐛 [Report Issues](https://github.com/ThanuMahee12/firebase-react-template/issues)
- 💬 [Discussions](https://github.com/ThanuMahee12/firebase-react-template/discussions)
- 📖 [Wiki](https://github.com/ThanuMahee12/firebase-react-template/wiki)

---

**This template is production-ready and actively maintained. Happy coding! 🚀**
