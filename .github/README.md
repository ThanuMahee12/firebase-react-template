# GitHub Actions Workflows

This directory contains automated workflows for CI/CD, releases, and versioning.

## Available Workflows

### 1. Deploy to Firebase Hosting (`deploy.yml`)

**Trigger**: Push to `main` branch

**Steps**:
1. Format check with Prettier
2. Lint check with ESLint
3. Build project with Vite
4. Deploy to Firebase Hosting

**Required Secrets**:
- `FIREBASE_SERVICE_ACCOUNT` - Firebase service account JSON
- `FIREBASE_PROJECT_ID` - Firebase project ID

### 2. Auto Release and Tag (`release.yml`)

**Trigger**: Push to `main` branch

**Steps**:
1. Analyze commit message for version bump type
2. Calculate new version (v1.0.0 → v1.0.1)
3. Update `package.json` version
4. Create Git tag
5. Build project
6. Create release archives (source + build)
7. Generate release notes
8. Publish GitHub Release

**Version Bump Rules**:
- `breaking:` or `major:` → Major version (v1.0.0 → v2.0.0)
- `feat:` or `minor:` → Minor version (v1.0.0 → v1.1.0)
- All other commits → Patch version (v1.0.0 → v1.0.1)

## Scripts

### bump-version.sh

**Location**: `.github/scripts/bump-version.sh`

**Purpose**: Calculate next semantic version based on bump type

**Usage**:
```bash
bash .github/scripts/bump-version.sh [major|minor|patch]
```

**Examples**:
```bash
# Current tag: v1.2.3

bash .github/scripts/bump-version.sh patch
# Output: v1.2.4

bash .github/scripts/bump-version.sh minor
# Output: v1.3.0

bash .github/scripts/bump-version.sh major
# Output: v2.0.0
```

## Workflow Execution

### Both Workflows Run in Parallel

When you push to `main`:

```
Push to main
    ├── deploy.yml (Firebase deployment)
    │   ├── Format check
    │   ├── Lint check
    │   ├── Build
    │   └── Deploy to Firebase
    │
    └── release.yml (Versioning & Release)
        ├── Calculate version
        ├── Create tag
        ├── Build
        ├── Create archives
        └── Publish release
```

## Commit Message Convention

Use conventional commit format for automatic version bumping:

```
<type>: <description>

[optional body]
```

### Types and Version Impact

| Type | Version Impact | Example |
|------|---------------|---------|
| `breaking:` | Major (2.0.0) | `breaking: change API structure` |
| `major:` | Major (2.0.0) | `major: remove deprecated methods` |
| `feat:` | Minor (1.1.0) | `feat: add dark mode` |
| `feature:` | Minor (1.1.0) | `feature: add user profiles` |
| `minor:` | Minor (1.1.0) | `minor: enhance UI` |
| `fix:` | Patch (1.0.1) | `fix: resolve login bug` |
| `docs:` | Patch (1.0.1) | `docs: update README` |
| `chore:` | Patch (1.0.1) | `chore: update dependencies` |
| `style:` | Patch (1.0.1) | `style: format code` |
| `refactor:` | Patch (1.0.1) | `refactor: optimize auth flow` |

## Troubleshooting

### Workflow Permissions

If workflows fail with permission errors:

1. Go to **Settings** → **Actions** → **General**
2. Under "Workflow permissions":
   - Select "Read and write permissions"
   - Check "Allow GitHub Actions to create and approve pull requests"
3. Click **Save**

### Failed Deploy Workflow

Common issues:

1. **Format check fails**: Run `npm run format` locally
2. **Lint check fails**: Run `npm run lint` locally and fix errors
3. **Build fails**: Run `npm run build` locally to debug
4. **Firebase deployment fails**: Check `FIREBASE_SERVICE_ACCOUNT` and `FIREBASE_PROJECT_ID` secrets

### Failed Release Workflow

Common issues:

1. **Tag already exists**: Delete and recreate the tag
2. **Build fails**: Test `npm run build` locally
3. **Archive creation fails**: Check disk space and permissions

## Documentation

For detailed documentation, see:
- [GitHub Actions Wiki](https://github.com/ThanuMahee12/firebase-react-template/wiki/GitHub-Actions)
- [Versioning & Releases Wiki](https://github.com/ThanuMahee12/firebase-react-template/wiki/Versioning-and-Releases)
