# Prompt Engineering with Claude — Course Site

This folder contains everything needed to publish the course as a public website. You do NOT need the terminal for this. Everything happens in GitHub's and Vercel's web interfaces.

Estimated time: **~30 minutes**, split into three short steps.

---

## What you'll end up with

- A real URL you can share anywhere (e.g. `prompt-engineering-course.vercel.app`, or a custom domain if you want one).
- Free hosting forever at the traffic levels a course like this gets.
- Students click the link, the course runs in their browser, their progress saves automatically per-device.
- Updates: change anything in GitHub, Vercel redeploys automatically.

---

## Before you start

You'll need free accounts on two services:

1. **GitHub** — https://github.com/signup (free)
2. **Vercel** — https://vercel.com/signup (sign in with your GitHub account — it's simpler that way)

Set those up first if you don't already have them. Takes 5 minutes.

---

## Step 1 — Put the code on GitHub (10 minutes)

1. Go to **https://github.com/new** (make sure you're signed in).
2. **Repository name:** `prompt-engineering-course` (or whatever you want — this will appear in your URL later).
3. **Public** repository (leave this checked).
4. Check the box: **"Add a README file"** (doesn't matter — we'll replace it).
5. Click **"Create repository"**.

You now have an empty repository. We need to upload this folder's contents to it.

6. On your new repo's page, click **"Add file"** → **"Upload files"**.
7. Drag **every file and folder from this folder** into the browser upload area. Upload ALL of these:
   - `index.html`
   - `package.json`
   - `vite.config.js`
   - `tailwind.config.js`
   - `postcss.config.js`
   - `README.md` (this file)
   - `.gitignore`
   - `src/` folder (contains `App.jsx`, `main.jsx`, `index.css`)

   **Make sure the `src/` folder uploads as a folder, not as three loose files.** When GitHub shows the file tree, you should see a `src` folder at the top level with 3 files inside.

8. At the bottom of the upload page, click **"Commit changes"**.

Your GitHub repo is now ready.

---

## Step 2 — Deploy on Vercel (10 minutes)

1. Go to **https://vercel.com/new**.
2. You'll see a list of your GitHub repositories. Find `prompt-engineering-course` and click **"Import"**.
3. Vercel asks a few questions. Accept all the defaults:
   - **Framework Preset:** Vercel should auto-detect "Vite" — leave it.
   - **Root Directory:** leave as-is (`./`).
   - **Build Command:** should say `npm run build` — leave it.
   - **Output Directory:** should say `dist` — leave it.
4. Click **"Deploy"**.

Vercel will spend 1–2 minutes building the site. When it finishes, you'll see confetti and a preview of the live site.

5. Click **"Continue to Dashboard"** and you'll see your live URL at the top. It'll look like `prompt-engineering-course-xyz.vercel.app`.

**Your course is live. Share that URL with anyone.**

---

## Step 3 — (Optional) Custom domain (10 minutes)

If you want `course.yourname.com` instead of `prompt-engineering-course.vercel.app`:

1. Buy a domain from Namecheap, Google Domains, Porkbun, or similar ($10–15/year).
2. In Vercel, go to your project → **Settings** → **Domains**.
3. Type in your custom domain and click **"Add"**.
4. Vercel will show you DNS records to add. Copy them.
5. In your domain registrar's dashboard, add those DNS records.
6. Wait 10 minutes to a few hours for the DNS to propagate. Vercel will auto-detect when it's ready and serve your site at the custom domain.

---

## Updating the course later

This is the part that'll feel magical.

- Go to your GitHub repo, navigate to any file (e.g., `src/App.jsx`).
- Click the pencil icon (edit).
- Make your change in the browser.
- Scroll down, click **"Commit changes"**.
- Vercel sees the change and auto-redeploys within a minute.

No terminal. No local development setup. The whole content pipeline is browser-only.

---

## What students see

- First visit: clean home page, no sign-in required. They just click a course and start.
- Quiz scores and module-complete status save automatically to their browser (per-device).
- If they clear their browser data or switch devices, progress resets — that's a tradeoff of no-signin.
- Works on phone, tablet, desktop.

---

## What's NOT included (and what you'd need to add)

Intentionally kept simple for the "share with friends" use case. If you later want:

- **User accounts / cross-device sync** — requires a real backend (Supabase, Firebase). Moderate lift.
- **Payments / gated access** — wrap access through Gumroad or Lemonsqueezy; send paying students to a protected URL.
- **Analytics** — add Plausible or Vercel Analytics (click-install from the Vercel dashboard).
- **Discussion / community** — link out to a Discord, Circle, or Substack chat. Don't try to build this in.

For now, shipping the free public course is step one. The rest is only worth building if demand shows up.

---

## Troubleshooting

**Build fails on Vercel:**
Usually means a file didn't upload from the `src/` folder. Go to your repo, check that `src/App.jsx`, `src/main.jsx`, and `src/index.css` all exist. Re-upload any missing ones.

**Site loads but looks unstyled:**
Tailwind didn't compile. Check that `tailwind.config.js`, `postcss.config.js`, and `src/index.css` are all present in your repo at the correct paths.

**Progress isn't saving:**
Students are in private/incognito mode, or have localStorage disabled. This is the one real limitation of the no-signin approach.

**Want to change the course name or blurb on the home page:**
Edit `src/App.jsx` on GitHub. The course data lives in the `SPEC` object near the top of the file. Commit your change and Vercel redeploys automatically.

---

That's the whole thing. Ship it.
