# 🛰️ Deployment Guide — "Droid" GitHub Profile

This package turns your GitHub profile ([github.com/NnR2D2](https://github.com/NnR2D2)) into an animated, 3D, recruiter-magnet profile. Follow the steps below exactly — it takes about **5 minutes**.

---

## 📦 What's in this package

```
github-profile-readme/
├── README.md                      ← the profile itself (goes in your special repo)
├── SETUP.md                       ← this guide
├── assets/
│   ├── r2-mascot.svg              ← custom animated droid mascot
│   └── r2-divider.svg             ← custom animated "scanning pulse" divider
└── .github/
    └── workflows/
        ├── 3d-contrib.yml         ← GitHub Action: builds the 3D contribution graph
        └── snake.yml              ← GitHub Action: builds the contribution snake
```

---

## Step 1 — Create the special profile repository

GitHub shows a profile README only from a repository named **exactly** like your username.

1. Go to [github.com/new](https://github.com/new)
2. Repository name: **`NnR2D2`** (must match your username, letter for letter)
3. Set visibility to **Public** ✅ (required — private profile repos don't display the README)
4. ✅ Check *"Add a README file"* (so you have something to replace)
5. Click **Create repository**

> GitHub will show a banner: *"You found a secret! NnR2D2/NnR2D2 is a special repository…"* — that's correct.

## Step 2 — Upload the files

**Option A — Web UI (easiest):**

1. Open your new repo → **Add file → Upload files**
2. Drag in `README.md` (this **replaces** the auto-generated one), plus the `assets/` folder contents and the `.github/workflows/` folder contents.
   - Tip: drag the `assets` and `.github` folders directly onto the upload page — GitHub preserves folder structure.
3. Commit with message: `feat: droid profile`

**Option B — Git CLI:**

```bash
git clone https://github.com/NnR2D2/NnR2D2.git
cd NnR2D2
cp -r /path/to/github-profile-readme/. .   # copies README.md, assets/, .github/
git add .
git commit -m "feat: droid profile"
git push
```

## Step 3 — Run the two generators once

The 3D graph and the snake don't exist until their workflows run at least once.

1. In your repo, open the **Actions** tab
2. If you see *"Workflows aren't being run on this repository"* — click **Enable workflows**
3. In the left sidebar select **Generate 3D Contribution Graph** → **Run workflow** → **Run workflow**
4. Select **Generate Contribution Snake** → **Run workflow** → **Run workflow**
5. Wait ~1 minute for both to show green ✅

What each one does:

| Workflow | Result |
|---|---|
| `3d-contrib.yml` | Commits animated 3D isometric SVGs to `profile-3d-contrib/` on `main` (daily at 03:30 UTC, or on every push) |
| `snake.yml` | Pushes light + dark snake SVGs to the `output` branch (daily at 00:00 UTC) |

## Step 4 — Verify

Open [github.com/NnR2D2](https://github.com/NnR2D2) — you should see: waving header → typing animation → about me with droid mascot → tech stack → projects → live stats → **3D contribution graph** → **contribution snake**.

GitHub renders the dark/light variants automatically based on the viewer's theme.

---

## ✏️ Step 5 — Personalize

The profile has already been personalized from your CV (publications, experience, education, honors, coursework, contact links and the 4 CV projects are all accurate).

Only two spots remain that you may want to review — search for `✏️ EDIT` in `README.md`:

1. **Attack on Finances** and **Smart Farming** descriptions — these were inferred from repo names (they're not detailed on the CV).
2. Anything you'd rather phrase differently (e.g., hiding your CGPA or student email is a one-line change).

## 🩺 Troubleshooting

| Symptom | Cause & fix |
|---|---|
| 3D graph section empty / 404 | Run `Generate 3D Contribution Graph` once (Step 3). It commits `profile-3d-contrib/*.svg` to the repo. |
| Snake section empty / 404 | Run `Generate Contribution Snake` once (Step 3). Check the `output` branch exists. |
| Stats / streak cards show an error image | The free Vercel instances cold-start occasionally — wait 30s and refresh. |
| Trophy & activity graph cards missing | Intentional — both services were over quota (HTTP 402) when this package was built. They're included but commented out in `README.md`; uncomment them once the services recover (test by opening the image URLs in a browser). |
| Mascot / dividers not animating | Make sure `assets/` was uploaded with both SVGs, and the repo is public. |
| Workflows fail with permission errors | Repo **Settings → Actions → General → Workflow permissions** → set to **Read and write**. |

## 🚀 Optional upgrades

- **Pin your best repos** on the profile (Pinned section) — Interviewers click those first.
- **Add topics** to your repos (`tensorflow`, `computer-vision`, `iot`) — they power GitHub search and show your stack.
- **Write real READMEs** for the featured projects with screenshots/GIFs — that's what makes an interview go from "nice profile" to "when can you start?".
