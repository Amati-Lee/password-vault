# Password Vault

## IMPORTANT: This is a PUBLIC GitHub repo
Repository: `Amati-Lee/password-vault`
Deployed to: GitHub Pages (https://amati-lee.github.io/password-vault/)

## Tech Stack
- Pure frontend PWA (single `index.html` with inline JS/CSS)
- AES-256-GCM encryption with PBKDF2 (600,000 iterations)
- Data stored in browser `localStorage` (never in files or git)
- Service Worker for offline support
- No backend, no API calls, no dependencies

## Security Rules

### Sensitive Information
- NEVER hardcode passwords, keys, tokens, or secrets in source code
- User passwords are stored ONLY in browser localStorage, encrypted with AES-256-GCM
- No `.env` file is needed for this project (pure frontend)
- The encryption algorithm and parameters are safe to be public (Kerckhoffs's principle)

### Before Every Push
1. Run `git status` to verify no unexpected files
2. Confirm no `.env`, `.vault`, or backup files are staged
3. Confirm no real passwords or test credentials in code
4. Review `git diff --staged` for any accidental secrets

### Code Guidelines
- All crypto operations use Web Crypto API (`crypto.subtle`)
- Salt and IV must always be randomly generated (`crypto.getRandomValues`)
- Never reduce PBKDF2 iteration count below 600,000
- Auto-lock timer must remain enabled (currently 5 min)
