# Slices

Redux Toolkit slices for state management (alternative to features/).

## Examples
- authSlice.js - Authentication state
- userSlice.js - User data state
- themeSlice.js - UI theme state
- cartSlice.js - Shopping cart state

## Usage
```javascript
import { createSlice } from '@reduxjs/toolkit'

const exampleSlice = createSlice({
  name: 'example',
  initialState: {},
  reducers: {}
})
```
