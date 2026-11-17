# Dynasty HQ — GitHub Pages deployment kit

This is a static fan-created dashboard for a fictional College Football 27 dynasty. It is not connected to EA servers or ChatGPT automatically.

## One-time setup

1. Create a **public** repository in your GitHub account (for example, `howard-dynasty-hq`). The contents of a public repository and its GitHub Pages site are public; do not upload private information.
2. Upload all files from this folder to the repository root: `index.html`, `latest-update.json`, and `.nojekyll`. The README is optional. Alternatively, connect that repository to ChatGPT so ChatGPT can publish the supplied files with permission.
3. In the repository, choose **Settings → Pages → Build and deployment → Deploy from a branch → main / (root) → Save**. Publication depends on your repository permissions and plan.
4. Open your published GitHub Pages URL (usually `https://USERNAME.github.io/REPOSITORY/`). Keep using that URL.
5. The app automatically checks `latest-update.json` every time it opens, and applies newly published updates. Your narrative decisions are kept in browser storage on that same origin.

## Every game

- Upload your **postgame autosave** to ChatGPT. ChatGPT can decode the result, scoring summary and player/team stats where accessible, then publish a *postgame update* to `latest-update.json`.
- Upload your **post-advance autosave**. ChatGPT can decode other results, top 25, Heisman and CFP tables, then publish a *week-advance update* to the same file.
- Open/refresh your regular GitHub Pages app URL. There is no replacement HTML download.

## Data model

Update pack: `schema: howard-dynasty-hq-update-v1`, unique `updateId`, `stage: postgame|week-advance|correction`, `week`, and optionally `data`, `national`, `gameNotes`, `stories`, `interactions`, `headlines`, `pressLabel`, `pressIntro`.

For a new week, include `week` equal to the newly active week. For a postgame update, use the current story week so coaching decisions are preserved. Each published pack needs a unique update ID. National tables should only be included when supported by the uploaded save.

**Persistence:** `localStorage` is browser- and origin-specific. Don't switch between a file:// copy and GitHub Pages expecting decisions to migrate automatically. Export your progress from the app before switching and import it on the hosted app. Use the app's Save & Export controls for backups.

**Hosting:** The pages site is public if the repository is public. No server is required; updates are static JSON published through GitHub.