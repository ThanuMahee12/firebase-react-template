# Routes

Route configuration and protected route components.

## Files
- index.jsx - Main route configuration
- ProtectedRoute.jsx - Protected route wrapper for authenticated pages
- PublicRoute.jsx - Public route wrapper (redirects if authenticated)

## Usage
```jsx
import { createBrowserRouter } from 'react-router-dom'

const router = createBrowserRouter([
  { path: '/', element: <Home /> },
  { path: '/dashboard', element: <ProtectedRoute><Dashboard /></ProtectedRoute> }
])
```
