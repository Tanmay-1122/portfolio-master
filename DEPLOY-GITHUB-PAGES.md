# Deploying this project to GitHub Pages

This guide shows how to push this project to GitHub and deploy it to GitHub Pages using the `gh-pages` package.

> Notes:
> - The React app lives in the `Portfolio-master` folder. Run the commands below inside that folder.
> - Replace `YOUR_GITHUB_USERNAME` and `YOUR_REPO_NAME` with your own values.

## 1) Add homepage

Open `package.json` and set the `homepage` field to the URL where the site will live after deployment:

```
"homepage": "https://YOUR_GITHUB_USERNAME.github.io/YOUR_REPO_NAME"
```

If you don't know the repo name yet, set this value later before deploying.

## 2) Install gh-pages

Open a PowerShell terminal in `Portfolio-master` and run:

```powershell
npm install --save-dev gh-pages
```

This project already contains `gh-pages` in `devDependencies` (if you pulled recent updates), but you must run `npm install` locally to install it.

## 3) Build + deploy

From inside `Portfolio-master` run:

```powershell
npm run build
npm run deploy
```

`npm run deploy` calls `gh-pages -d build` to create a branch named `gh-pages` with the production build and push it to GitHub.

## 4) Create a GitHub repo and push

If you haven't already created a repo on GitHub, create one named `YOUR_REPO_NAME` (matching the `homepage` path).

Then push your project (run these from the top-level of the project folder you want to push):

```powershell
# Set your name/email once (only if not already set)
git config --global user.name "Your Name"; git config --global user.email "you@example.com"

# Initialize and push (only if repo is new locally)
git init
git add .
git commit -m "Initial commit"

git remote add origin https://github.com/YOUR_GITHUB_USERNAME/YOUR_REPO_NAME.git
git branch -M main
git push -u origin main
```

If you already have a remote repo, simply do:

```powershell
git add .
git commit -m "Update site"
git push origin main
```

## 5) Final step

- Visit `https://YOUR_GITHUB_USERNAME.github.io/YOUR_REPO_NAME` after the deploy finishes. It may take a minute to go live.
 
## Automatic deploy via GitHub Actions

This repository includes a GitHub Actions workflow (`.github/workflows/deploy-gh-pages.yml`) that builds and deploys the site to the `gh-pages` branch automatically whenever you push to `main`.

To use the automatic workflow:

1. Make sure the file `package.json` has the correct `homepage` set (ex: `https://tanmay-1122.github.io/portfolio-master`).
2. Push your changes to the `main` branch on GitHub. The workflow will run automatically and deploy the result to `gh-pages`.

If you prefer to trigger a manual deploy, you can still run `npm run deploy` locally (this uses `gh-pages`).
- If you chose to deploy from the `main` branch via GitHub Pages settings, use the appropriate method in GitHub UI instead.

---

If you want I can:
- add a workflow file to deploy automatically from GitHub Actions, or
- update `homepage` in `package.json` with your actual GitHub username and repo name, and show the exact commands to run on PowerShell locally.
