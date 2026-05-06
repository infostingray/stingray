# Sync stingray-landing to GitHub

Quick guide. Pick **Option A (CLI)** if you have `git` and prefer terminal. Pick **Option B (web UI)** if you'd rather drag-and-drop.

## Prerequisites

- A GitHub account
- Your three project files: `index.html`, `README.md`, `LICENSE`
- The `.gitignore` from this drop

Put them all in one folder. Final layout:

```
stingray-landing/
├── .gitignore
├── LICENSE
├── README.md
└── index.html
```

---

## Option A — Command line (recommended)

### 1. Create the repo on GitHub

Go to <https://github.com/new>:

- **Repository name:** `stingray-landing` (or whatever you want)
- **Visibility:** Private or Public — your call
- **Do NOT** check "Add a README", "Add .gitignore", or "Add a license" — you already have those
- Click **Create repository**

GitHub will show you a page with setup commands. Ignore those and use the ones below.

### 2. Push from your machine

Open a terminal in your `stingray-landing/` folder and run:

```bash
# Initialize the repo
git init
git branch -M main

# Stage and commit everything
git add .
git commit -m "Initial commit: stingray landing page"

# Connect to GitHub (replace YOUR_USERNAME and REPO_NAME)
git remote add origin https://github.com/YOUR_USERNAME/stingray-landing.git

# Push
git push -u origin main
```

If GitHub asks for a password, **use a Personal Access Token**, not your account password:

1. Go to <https://github.com/settings/tokens>
2. Generate new token (classic) → check `repo` scope → generate
3. Paste the token as the password

Or set up SSH once and forget about it: <https://docs.github.com/en/authentication/connecting-to-github-with-ssh>

### 3. Future updates

```bash
git add .
git commit -m "describe what you changed"
git push
```

---

## Option B — Web UI (no terminal needed)

1. Go to <https://github.com/new> and create the repo (don't initialize with anything).
2. On the empty repo page, click **"uploading an existing file"**.
3. Drag your `stingray-landing/` folder contents into the upload area: `index.html`, `README.md`, `LICENSE`, `.gitignore`.
4. Scroll down, write a commit message ("Initial commit"), click **Commit changes**.

That's it. For future edits you can use the GitHub web editor or install [GitHub Desktop](https://desktop.github.com/) for a visual git client.

---

## Deploy it (optional)

Once it's on GitHub, the easiest free hosts:

- **GitHub Pages** — Repo → Settings → Pages → Source: `main` branch, `/ (root)`. Takes 1–2 min. URL: `https://YOUR_USERNAME.github.io/stingray-landing/`
- **Vercel** — <https://vercel.com/new> → import the repo → deploy. Custom domain support, auto-deploys on every push.
- **Netlify** — <https://app.netlify.com/start> → connect to GitHub → pick the repo. Same idea as Vercel.
- **Cloudflare Pages** — <https://pages.cloudflare.com/> → connect repo. Fastest CDN of the bunch.

All four are free for this project size and will rebuild automatically every time you push to `main`.

---

## Common gotchas

- **`fatal: remote origin already exists`** → you ran `git remote add` twice. Fix: `git remote set-url origin https://github.com/YOUR_USERNAME/stingray-landing.git`
- **Push rejected, "non-fast-forward"** → GitHub has commits yours doesn't. Usually because you initialized the repo with a README. Pull first: `git pull origin main --rebase`, then push.
- **Large file warning** → `index.html` is ~190 KB because of the embedded base64 emblems. That's fine; GitHub's hard limit is 100 MB per file.
- **Authentication failed** → use a Personal Access Token, not your account password (see step 2 above).
