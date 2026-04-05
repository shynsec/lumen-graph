# Contributing to Lumen Graph

Thank you for your interest in contributing. Lumen Graph is a single-file tool — contributions should maintain that constraint.

## Ground rules

- The tool must remain a single `index.html` file with no build step required
- No external runtime dependencies (CDN scripts, npm packages loaded at runtime)
- All new features must not break the existing security mitigations
- Code must pass a basic JS syntax check before submitting

## How to contribute

1. Fork the repository
2. Create a branch: `git checkout -b feature/your-feature-name`
3. Make your changes to `index.html`
4. Test in Chrome and Firefox
5. Open a pull request with a clear description of what you changed and why

## What we welcome

- Bug fixes
- New entity types with appropriate icons and mesh gradient palettes
- Additional MITRE ATT&CK techniques in the technique database
- New edge relationship type suggestions
- UI/UX improvements that don't add visual clutter
- Security improvements
- Documentation improvements

## What to avoid

- Features that require a server or backend
- External API calls (the tool must work fully offline)
- Dependencies that increase the file size significantly without proportional value
- Breaking changes to the JSON export format (or include a migration path)

## Reporting bugs

Open a GitHub Issue with:
- Browser and OS
- Steps to reproduce
- Expected vs actual behaviour
- Screenshot if relevant

## Code style

- Vanilla JS only — no frameworks
- Keep variable names descriptive
- Add a comment for any non-obvious logic
- Follow the existing code structure (state object, draw functions, event listeners at the bottom)
