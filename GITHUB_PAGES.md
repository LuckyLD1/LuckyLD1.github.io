# Publish Floorlink with GitHub Pages

This project is ready to publish from your **LuckyLD** GitHub account. These instructions use **floorlink** as the repository name; another name works too.

## 1. Open the correct folder

In VS Code, select **File → Open Folder** and open:

```text
C:\Users\lucas_f0pwh7q\OneDrive\Desktop\Senior Project IP Mapping Project\floorlink
```

Use this inner `floorlink` folder as the repository root. It already contains a Git repository on the `main` branch. Do not initialize another repository in the parent folder.

Your GitHub repository should have this structure:

```text
.github/
  workflows/
    pages.yml
dist/
  .nojekyll
  index.html
  app.js
  model.js
  styles.css
tests/
package.json
server.mjs
README.md
GITHUB_PAGES.md
```

## 2. Create an empty repository

1. Open https://github.com/new and sign in as **LuckyLD**.
2. Select **LuckyLD** as the owner and enter **floorlink** as the repository name.
3. Choose **Public** for GitHub Pages on GitHub Free. This makes the source and demo publicly accessible. Private-repository Pages availability depends on your plan.
4. Leave the README, `.gitignore`, and license initialization options off; the local project already has files and history.
5. Click **Create repository**.

If you already have an empty repository with a different name, use its URL below instead.

## 3. Upload the project

In VS Code, open **Terminal → New Terminal**. Run these commands from the `floorlink` folder:

```powershell
git add .
git commit -m "Prepare Floorlink for GitHub Pages"
git remote add origin https://github.com/LuckyLD/floorlink.git
git push -u origin main
```

Complete GitHub sign-in if prompted. The local repository had no configured remote when these instructions were prepared. If `origin` already exists, run `git remote -v` to check it instead of adding it again. Use your actual repository name if it differs from `floorlink`.

If Git asks for your commit identity, configure your preferred name and GitHub email in this repository, then repeat the commit and push. Your GitHub-provided no-reply email is available in your GitHub email settings.

## 4. Enable Pages

1. In the GitHub repository, go to **Settings → Pages**.
2. Under **Build and deployment → Source**, choose **GitHub Actions**.
3. Open the **Actions** tab and select **Deploy Floorlink to GitHub Pages**.
4. Click **Run workflow**, choose `main`, and run it. If the first automatic run failed because Pages was not enabled yet, this new run handles deployment.
5. Wait for the run to turn green. Its deployment link also appears under **Settings → Pages**.

For a repository named `floorlink`, the expected website address is:

**https://luckyld.github.io/floorlink/**

This address becomes available only after you create the repository, enable Pages, and complete a successful deployment. No custom domain or API key is required.

## Update the website later

Edit the files in `dist/`, preview with Live Server, and commit and push:

```powershell
git add dist
git commit -m "Update Floorlink"
git push
```

Every push to `main` runs the checks and deploys `dist/`. There is no build or dependency-install step. The workflow publishes only website assets, not the preview server, tests, or Sites hosting configuration. Keep HTML asset URLs and JavaScript imports relative so they work under the repository path.

Local preview remains available with **Go Live** at http://127.0.0.1:5500/ or `npm start` at http://127.0.0.1:4173/.

## Your saved layouts

The hosted app keeps edits in each browser's local storage. GitHub Pages does not synchronize panel edits between visitors or write them back to the repository. To transfer your current localhost layout to GitHub Pages, use **Export layout** locally, then **Import** on the hosted site. The existing examples are fictitious demonstration data.

## Troubleshooting

- **Pages workflow is missing:** `.github/workflows/pages.yml` must be at the repository root, alongside `dist/`, not inside another `floorlink` folder.
- **Pages setup fails:** choose **GitHub Actions** as the Pages source, confirm Pages is available for your repository visibility and plan, and rerun the workflow.
- **404:** check that the workflow succeeded and use the repository path, such as `/floorlink/`. The definitive published URL appears in Settings → Pages.
- **Old content:** wait for the latest workflow to finish, then refresh. Locally saved panel edits are separate from the example data in the deployed source.

Official references: [GitHub Pages publishing sources](https://docs.github.com/en/pages/getting-started-with-github-pages/configuring-a-publishing-source-for-your-github-pages-site) and [custom Pages workflows](https://docs.github.com/en/pages/getting-started-with-github-pages/using-custom-workflows-with-github-pages).
