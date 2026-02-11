# Fix "There isn't a GitHub Pages site here"

Follow these steps **in order**:

## 1. Push the workflow and trigger a deploy

Make sure the workflow file is in your repo and run a deploy:

```bash
git add .github/workflows/deploy.yml
git commit -m "Add GitHub Pages deploy workflow"
git push origin main
```

(Use `master` instead of `main` if that’s your default branch.)

## 2. Create `gh-pages` if it doesn’t exist (optional)

If the Actions workflow hasn’t run yet or you prefer to deploy from your machine:

```bash
npm run build
npm run deploy
```

This pushes the contents of `dist` to the `gh-pages` branch.

## 3. Turn on GitHub Pages in the repo

1. Open your repo on GitHub.
2. Go to **Settings** → **Pages** (in the left sidebar).
3. Under **Build and deployment**:
   - **Source**: choose **Deploy from a branch**.
   - **Branch**: select **gh-pages**.
   - **Folder**: select **/ (root)**.
4. Click **Save**.

## 4. Wait and open the site

After 1–2 minutes, open:

**https://YOUR_USERNAME.github.io/YOUR_REPO_NAME/**

Your `vite.config.ts` has `base: '/valentine/'`, so if the repo is `valentine`, the URL is:

**https://YOUR_USERNAME.github.io/valentine/**

If you still see "There isn't a GitHub Pages site here", check:

- **Actions** tab: the "Deploy to GitHub Pages" workflow run completed successfully.
- **Branches**: the `gh-pages` branch exists and has files (e.g. `index.html`, `assets/`).
- **Settings → Pages**: source is "Deploy from a branch", branch is `gh-pages`, folder is `/ (root)`.
