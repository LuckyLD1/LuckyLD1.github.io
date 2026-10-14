# Floorlink

An interactive factory network map with six example cabinets and 32 devices. Explore panel interiors, inspect IP addresses and connections, and customize equipment on snapping DIN rails.

## Open the project

Open this folder in VS Code:

```text
C:\Users\lucas_f0pwh7q\OneDrive\Desktop\Senior Project IP Mapping Project\LuckyLD1.github.io
```

This is the project's only repository. It is connected to `https://github.com/LuckyLD1/LuckyLD1.github.io.git` on branch `main`.

## Files

| File or folder | Purpose |
| --- | --- |
| `dist/index.html` | Website entry point |
| `dist/app.js` | Map, cabinets, device inspector, and editing interactions |
| `dist/model.js` | Example equipment and layout validation |
| `dist/styles.css` | Styling, animations, and responsive layouts |
| `dist/.nojekyll` | Static-site marker for GitHub Pages |
| `.github/workflows/pages.yml` | Checks and automatic GitHub Pages deployment |
| `tests/model.test.mjs` | IP, connection, import, and rail-placement checks |
| `server.mjs` | Local preview server |
| `package.json` | Commands for previewing and testing |
| `.gitignore` | Excludes local tools and generated archives from Git |

The hidden `.git` folder stores version history and the GitHub connection. The ignored `.vscode` folder contains local Live Server settings.

## Preview locally

With Node.js installed, run from this folder:

```powershell
npm start
```

Open **http://127.0.0.1:4173/**. No installation or build step is needed. Press **Ctrl+C** in that terminal to stop the server.

Alternatively, with the **Live Server** extension by Ritwick Dey in VS Code, click **Go Live** and open **http://127.0.0.1:5500/**. The local settings serve `dist/` and refresh on save. If those ignored settings are unavailable in another checkout, right-click `dist/index.html` and select **Open with Live Server**.

## Use the app

- Click a map marker or panel card to open the cabinet.
- Select a device to inspect its IP, description, model, and connections. Select a connection to navigate to that device.
- Search or expand subnet groups in the IP directory to locate equipment.
- Select **Edit panel** to add or drag equipment onto rails. Equipment snaps into available slots and cannot overlap. Clicking a library item and using **Move rail** are alternatives to dragging.
- Edit device addresses, names, descriptions, statuses, and connections in the inspector. Addresses must be valid and unique.
- Use **Undo** to reverse edits during the current session. Export and import JSON to transfer layouts between browsers or sites.

The app saves edits in the current browser, not in GitHub. Each visitor has a separate layout. All initial equipment, addresses, statuses, and wiring are demonstration data; the app does not scan or control a live network.

## Publish updates

In the GitHub repository, **Settings → Pages → Source** must be **GitHub Actions**. The included workflow checks the project and publishes only `dist/` on each push to `main`.

```powershell
git add .
git commit -m "Update Floorlink"
git push
```

Track deployment in the repository's **Actions** tab. After a successful deployment, the site is available at **https://luckyld1.github.io/**. You can also manually run **Deploy Floorlink to GitHub Pages** from Actions.

The workflow is required for this automatic publishing setup. It is not required to view the app locally. If deployment fails, confirm the Pages source is GitHub Actions, then rerun the workflow. The published URL is shown in Settings → Pages.

To use another static host, upload the contents of `dist/`. Asset paths are relative, so the app can also run under a subdirectory. The preview server and tests are not deployed.

## Check changes

```powershell
npm test
```

The tests cover example data, valid IP addresses, unique addresses, rail collisions and capacity, imported layouts, and device connections.
