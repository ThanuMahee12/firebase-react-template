# Contributing to Firebase React Template

Thank you for considering contributing to this project! We welcome contributions from everyone.

## How to Contribute

### Reporting Bugs

If you find a bug, please open an issue with:
- A clear title and description
- Steps to reproduce
- Expected vs actual behavior
- Screenshots if applicable
- Your environment (OS, Node version, etc.)

### Suggesting Features

Feature requests are welcome! Please open an issue with:
- A clear title and description
- Use case and benefits
- Possible implementation approach

### Pull Requests

1. **Fork the repository**
2. **Create a branch** for your feature/fix
   ```bash
   git checkout -b feature/amazing-feature
   ```

3. **Make your changes**
   - Follow existing code style
   - Keep changes focused and atomic
   - Write clear commit messages

4. **Test your changes**
   ```bash
   npm run dev    # Test locally
   npm run build  # Ensure build works
   npm run lint   # Check for linting errors
   ```

5. **Commit your changes**
   ```bash
   git commit -m "feat: add amazing feature"
   ```

   Use conventional commits:
   - `feat`: New feature
   - `fix`: Bug fix
   - `docs`: Documentation changes
   - `style`: Code style changes (formatting)
   - `refactor`: Code refactoring
   - `test`: Adding tests
   - `chore`: Maintenance tasks

6. **Push to your fork**
   ```bash
   git push origin feature/amazing-feature
   ```

7. **Open a Pull Request**
   - Provide a clear description
   - Reference any related issues
   - Include screenshots if UI changes

## Development Guidelines

### Code Style

- Use ES6+ features
- Follow existing code patterns
- Keep functions small and focused
- Add comments for complex logic

### Commit Messages

Follow conventional commits:

```
type(scope): subject

body (optional)

footer (optional)
```

Examples:
```
feat(auth): add Google sign-in
fix(firestore): resolve query pagination issue
docs(readme): update installation instructions
```

### Testing

- Test all new features locally
- Ensure existing functionality isn't broken
- Test in multiple browsers if UI changes

## Project Structure

- Keep components in `src/components/`
- Keep pages in `src/pages/`
- Keep utilities in `src/utils/`
- Follow existing folder structure

## Questions?

- Open a [Discussion](https://github.com/ThanuMahee12/firebase-react-template/discussions)
- Check existing [Issues](https://github.com/ThanuMahee12/firebase-react-template/issues)
- Read the [Wiki](https://github.com/ThanuMahee12/firebase-react-template/wiki)

## Code of Conduct

- Be respectful and inclusive
- Welcome newcomers
- Focus on constructive feedback
- Help others learn and grow

Thank you for contributing! 🎉
