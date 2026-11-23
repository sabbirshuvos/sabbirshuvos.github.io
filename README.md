# Sabbir Shuvo portfolio

Astro static site + Sveltia CMS (private admin at `/admin`), hosted free on GitHub Pages.
All content lives in `src/data/*.json`. You normally edit it through `/admin`, not by hand.

## 1. Run it on your computer
1. Install Node.js 22 LTS from nodejs.org.
2. In this folder run: `npm ci` then `npm run dev`.
3. Open http://localhost:4321 . Stop with Ctrl+C.
4. `npm run build` builds the final site into `dist/` (this is what GitHub does for you).

## 2. Publish (only when you approve)
1. Create a **public** repository named exactly `sabbirshuvos.github.io` on GitHub.
2. Upload every file in this folder to it (GitHub web page: Add file > Upload files; drag the
   contents, including the hidden `.github` folder). Do NOT upload `node_modules` or `dist`.
3. Repository Settings > Pages > Source: **GitHub Actions**.
4. The site appears at https://sabbirshuvos.github.io after the Actions run finishes (1-3 minutes).

## 3. Secure CMS sign-in (token method)
Create the token only after the site is live. Never paste it anywhere except the CMS sign-in box.
1. GitHub > Settings > Developer settings > Personal access tokens > **Fine-grained tokens** > Generate new token.
2. Name: `portfolio-cms`. Expiration: **60 to 90 days**.
3. Repository access: **Only select repositories** > `sabbirshuvos.github.io`.
4. Permissions > Repository permissions: **Contents: Read and write**. (Metadata: Read-only is added automatically.)
   Leave everything else, including Pull requests and Workflows, at "No access".
5. Generate, copy the token, open `https://sabbirshuvos.github.io/admin/`, choose sign in with token, paste it.
6. Turn on two-factor authentication on your GitHub account. Revoke the token if a device is lost.
7. When it expires, create a new one the same way. Put a reminder in your phone calendar.

Never commit tokens, passwords or keys. `.gitignore` already blocks `.env` files.

## 4. Updating content
Open `/admin`, choose a section, edit, press Save. The site rebuilds in 1-3 minutes.
- Achievements, Certifications and Gallery show a friendly empty state until you add the first entry.
- The email shows "to be added" until you type it in "Profile and introduction" AND switch on "Show email".
- Replace photo / CV: "Profile and introduction" > Profile photo / CV file.
- Gallery photos can contain hidden GPS data. The CMS re-saves uploads as WebP (resized to 1600px),
  which normally removes it, but check sensitive photos first.
- Do not switch `publish_mode` to `editorial_workflow` in `public/admin/config.yml`; it needs extra
  token permissions.

## 5. Pinned versions
`astro 7.4.13`, `@sveltia/cms 0.270.1`, fonts 5.3.0 (exact versions, no `^`). Update deliberately:
read the release notes, change the version, run `npm ci && npm run build`, then publish.
GitHub Actions use major-version tags (`@v4`, `@v3`).

## 6. Backups
Your GitHub repository keeps full history. Also keep a copy of this folder on a pendrive or Drive.
Original photo: `originals/profile-original.png`.
