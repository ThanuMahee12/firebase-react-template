# 🔥 Firebase React Template

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](https://opensource.org/licenses/MIT)
[![React](https://img.shields.io/badge/React-19.1.1-blue)](https://react.dev)
[![Firebase](https://img.shields.io/badge/Firebase-12.4.0-orange)](https://firebase.google.com)
[![Vite](https://img.shields.io/badge/Vite-7.1.14-purple)](https://vitejs.dev)

A **production-ready** React + Vite template with Firebase integration, Redux state management, and automated deployment. Perfect for building modern web applications quickly.

## ✨ Features

- ⚡️ **Vite** - Lightning-fast build tool with HMR
- ⚛️ **React 19** - Latest React with modern hooks
- 🔥 **Firebase Ready** - Pre-configured for Auth, Firestore, Storage, and Hosting
- 🎨 **Redux Toolkit** - Simplified state management
- 🧭 **React Router** - Client-side routing
- 🎯 **React Icons** - Popular icon library
- 📝 **ESLint** - Code quality and consistency
- 🔒 **Security Rules** - Pre-configured Firestore and Storage rules
- 🚀 **GitHub Actions** - Automated CI/CD deployment
- 📚 **Comprehensive Docs** - Complete wiki documentation

## 📋 Prerequisites

- Node.js 18+ and npm/yarn
- Firebase account
- Git

## 🚀 Quick Start

### 1. Clone the Repository

```bash
git clone https://github.com/ThanuMahee12/firebase-react-template.git
cd firebase-react-template
```

### 2. Install Dependencies

```bash
npm install
# or
yarn install
```

### 3. Configure Environment Variables

```bash
# Copy the example env file
cp .env.example .env

# Add your Firebase credentials to .env
```

Get your Firebase config from [Firebase Console](https://console.firebase.google.com/) → Project Settings → General → Your apps

### 4. Update Firebase Project ID

Edit `.firebaserc`:

```json
{
  "projects": {
    "default": "your-firebase-project-id"
  }
}
```

### 5. Start Development Server

```bash
npm run dev
```

Visit http://localhost:5173

## 📚 Documentation

Complete documentation available in the [Wiki](https://github.com/ThanuMahee12/firebase-react-template/wiki):

- 📖 **[Setup Guide](https://github.com/ThanuMahee12/firebase-react-template/wiki/Setup-Guide)** - Detailed installation instructions
- 🏗️ **[Project Structure](https://github.com/ThanuMahee12/firebase-react-template/wiki/Project-Structure)** - Understanding the codebase
- 🔥 **[Firebase Configuration](https://github.com/ThanuMahee12/firebase-react-template/wiki/Firebase-Configuration)** - Set up Firebase services
- 🚀 **[Deployment Guide](https://github.com/ThanuMahee12/firebase-react-template/wiki/Deployment-Guide)** - Deploy to Firebase Hosting
- ⚙️ **[GitHub Actions CI/CD](https://github.com/ThanuMahee12/firebase-react-template/wiki/GitHub-Actions)** - Automated deployments
- 📧 **[Email Templates](https://github.com/ThanuMahee12/firebase-react-template/wiki/Email-Templates)** - Customize Firebase auth emails
- 📊 **[Firebase Limitations](https://github.com/ThanuMahee12/firebase-react-template/wiki/Firebase-Limitations)** - Free tier quotas and limits
- 🔌 **[API Reference](https://github.com/ThanuMahee12/firebase-react-template/wiki/API-Reference)** - Complete API documentation

## 🛠️ Tech Stack

| Category | Technology | Version |
|----------|-----------|---------|
| **Frontend Framework** | React | 19.1.1 |
| **Build Tool** | Vite (Rolldown) | 7.1.14 |
| **State Management** | Redux Toolkit | 2.9.1 |
| **Routing** | React Router DOM | 7.9.4 |
| **Backend** | Firebase | 12.4.0 |
| **Icons** | React Icons | 5.5.0 |
| **Linting** | ESLint | 9.36.0 |

## 📁 Project Structure

```
firebase-react-template/
├── public/                   # Static files
├── src/
│   ├── assets/              # Images, icons, fonts
│   ├── components/          # Reusable React components
│   ├── pages/               # Page components
│   ├── layouts/             # Layout wrappers
│   ├── routes/              # Route configuration
│   ├── slices/              # Redux Toolkit slices
│   ├── store/               # Redux store
│   ├── firebase/            # Firebase config
│   │   └── config.js        # Firebase initialization
│   ├── hooks/               # Custom React hooks
│   ├── utils/               # Helper functions
│   ├── styles/              # CSS files
│   ├── App.jsx              # Root component
│   └── main.jsx             # Entry point
├── .env.example             # Environment variables template
├── .firebaserc              # Firebase project config
├── firebase.json            # Firebase hosting config
├── firestore.rules          # Firestore security rules
├── storage.rules            # Storage security rules
├── vite.config.js           # Vite configuration
└── CLAUDE.md                # AI assistant guidance

```

## 🔥 Firebase Services Included

### Authentication
- Email/Password authentication
- Google Sign-in
- Password reset
- Email verification

### Firestore Database
- NoSQL cloud database
- Real-time updates
- Security rules configured

### Storage
- File uploads
- User-specific folders
- Security rules configured

### Hosting
- Fast CDN delivery
- Automatic SSL
- Custom domain support

## 📜 Available Scripts

```bash
# Development
npm run dev              # Start dev server
npm run build            # Build for production
npm run preview          # Preview production build
npm run lint             # Run ESLint

# Firebase
firebase login           # Login to Firebase
firebase deploy          # Deploy everything
firebase deploy --only hosting     # Deploy hosting only
firebase deploy --only firestore   # Deploy Firestore rules
```

## 🚀 Deployment

### Deploy to Firebase Hosting

```bash
# Build the app
npm run build

# Deploy to Firebase
firebase deploy
```

Your app will be live at `https://your-project-id.web.app`

### Automated Deployment with GitHub Actions

Set up automated deployments on every push:

1. Follow the [GitHub Actions guide](https://github.com/ThanuMahee12/firebase-react-template/wiki/GitHub-Actions)
2. Add Firebase secrets to GitHub
3. Push to main branch
4. Automatic deployment!

## 🎯 Use Cases

Perfect for building:

- 📱 SaaS Applications
- 🛒 E-commerce Platforms
- 📊 Dashboard Applications
- 👥 Social Media Apps
- 📝 Content Management Systems
- 🎓 Educational Platforms
- 💼 Business Tools

## 🤝 Contributing

Contributions are welcome! Please read [CONTRIBUTING.md](CONTRIBUTING.md) for details.

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🙏 Acknowledgments

- [React](https://react.dev) - UI framework
- [Vite](https://vitejs.dev) - Build tool
- [Firebase](https://firebase.google.com) - Backend platform
- [Redux Toolkit](https://redux-toolkit.js.org) - State management
- [React Router](https://reactrouter.com) - Routing library

## 🐛 Issues

Found a bug? Please [open an issue](https://github.com/ThanuMahee12/firebase-react-template/issues).

## 💬 Discussions

Have questions? Join the [discussions](https://github.com/ThanuMahee12/firebase-react-template/discussions).

---

**Built with ❤️ for the developer community**

[Documentation](https://github.com/ThanuMahee12/firebase-react-template/wiki) • [Report Bug](https://github.com/ThanuMahee12/firebase-react-template/issues) • [Request Feature](https://github.com/ThanuMahee12/firebase-react-template/issues)
