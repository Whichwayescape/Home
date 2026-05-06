# How to Update Your Website — The Simple Version

This is written assuming you're not a developer. No jargon. Just steps in plain English.

---

## What you've got

You actually have **TWO things** that need to live online, and they need different homes:

1. **Your main website** (the landing page + Office Escape) — these are static files, very simple, very cheap to host.
2. **The animal-ranking puzzle** — this needs a real Node.js server because of the multiplayer/real-time stuff. It can't sit in the same place as the main site.

Don't worry — both are free or near-free to host. Read on.

---

# PART 1 — Get the new website files onto GitHub

You already have a repo at **github.com/Whichwayescape/WhichwayEscape**. We're going to replace its contents with the new files.

### Step 1 — Open your repo on GitHub
Go to **https://github.com/Whichwayescape/WhichwayEscape** and sign in.

### Step 2 — Delete the old files
For each old file (index.html, office.html, etc.), click the file name → click the trash can icon (🗑) on the right → scroll down → click the green **"Commit changes"** button.

Repeat for every file. (Yes it's annoying. You only do this once.) Don't delete `.git` or `.gitignore` if you see them — those are GitHub's own files.

> **Shortcut:** if you'd rather just nuke the whole repo and start fresh: Settings → scroll to the bottom → "Delete this repository". Then create a new empty one with the same name.

### Step 3 — Upload the new files
Look for **"Add file" → "Upload files"** at the top of the file list.

Open the `WhichwayEscape-website` folder I gave you on your computer. Drag **everything inside it** (all the files AND the `ballbreaker` folder) into the GitHub upload box.

### Step 4 — Save your changes
Scroll to the bottom of the upload page. Type a message like "uploaded new website" in the box. Click the green **"Commit changes"** button.

✅ **Done.** Your new code is now on GitHub.

---

# PART 2 — Pick where your website lives (HOSTING)

This is where I want to gently push back on the $10/month GitHub thing.

### About that $10/month you're paying GitHub

**GitHub Pages — the actual hosting service — is FREE.** You shouldn't need to pay GitHub anything to keep a website live. You may be paying for:
- **GitHub Pro** ($4/month) — gives you fancier features but doesn't affect hosting
- **A domain you bought through GitHub** (one-time/yearly fee, not monthly)
- **Something else entirely** that you signed up for

> **Action item:** Go to **github.com/settings/billing** and look at exactly what you're being charged for. If it's a plan, you can probably downgrade to free.

### My recommendation: switch to Cloudflare Pages

After looking at the options, here's what I'd recommend for a real business:

| Option | Cost | Why |
|---|---|---|
| **Cloudflare Pages** ⭐ | **$0/month** | Unlimited bandwidth, your own domain, free SSL. Best for a business that might get busy. |
| **Netlify** | Free, but limited | Easier interface, but has bandwidth caps that could surprise you on a busy month. |
| **GitHub Pages** | Free | Works fine, but slower to update and fewer features. |

**Cloudflare Pages is what I'd pick.** It's free forever, has no bandwidth limits, and is faster than the others for visitors around the world. The setup is almost identical to Netlify.

### Setup: Cloudflare Pages (one-time, ~10 minutes)

1. Go to **https://dash.cloudflare.com/sign-up** and create a free account
2. Once logged in, on the left sidebar click **"Workers & Pages"**
3. Click **"Create"** → tab **"Pages"** → **"Connect to Git"**
4. Click **"Connect GitHub"** and approve access to your **WhichwayEscape** repo
5. On the setup page:
   - **Project name:** `whichway-escape` (this becomes your free `.pages.dev` URL)
   - **Production branch:** `main`
   - **Framework preset:** None
   - **Build command:** *(leave blank)*
   - **Build output directory:** *(leave blank or put `/`)*
6. Click **"Save and Deploy"**
7. Wait ~30 seconds. You'll see a green check and a URL like `whichway-escape.pages.dev`

✅ Your site is live. Click the URL to see it.

---

# PART 3 — Connect your custom domain

You said you want to keep your domain. Whether you bought it through GitHub, GoDaddy, Namecheap, or anywhere else, here's how to point it at Cloudflare Pages.

### Step 1 — Add the domain in Cloudflare Pages
In your Pages project → **Custom domains** tab → **"Set up a custom domain"** → type your domain (e.g., `whichwayescape.com`) → click **"Continue"**.

### Step 2 — Cloudflare gives you instructions
It'll show you DNS records you need to add at your domain registrar (the place you bought the domain). It looks like:

```
Type: CNAME    Name: @    Value: whichway-escape.pages.dev
```

### Step 3 — Add those records at your registrar
1. Log in to wherever you bought the domain (GoDaddy / Namecheap / Google Domains / etc.)
2. Find "DNS settings" or "Manage DNS"
3. Add the record Cloudflare told you about
4. Save

### Step 4 — Wait
DNS changes can take **anywhere from 5 minutes to 24 hours** to take effect. Usually it's fast. You'll know it worked when typing your domain into a browser shows your new website.

> **Bonus tip:** If your domain registrar is annoying, you can transfer the domain to Cloudflare itself (they're also a registrar, and they don't mark up the price like GoDaddy does). Then everything is in one place.

---

# PART 4 — Set up the animal-ranking puzzle (Render)

This is a **completely separate** thing from the main website. It gets its own GitHub repo and its own hosting. Render is free.

### Step 1 — Create a new GitHub repo for the puzzle
1. Go to **https://github.com/new**
2. Repo name: `whichway-animals` (or whatever)
3. Set it to **Public**
4. Click **"Create repository"**

### Step 2 — Upload the puzzle files
The animal-ranking package you sent me has these files:
- `package.json`
- `package-lock.json`
- `server.js`
- `README.md`
- a `public` folder with `gm.html`, `play.html`, `assembly.html`

**Upload all of those** to your new `whichway-animals` repo using the same drag-and-drop method as Part 1, Step 3.

### Step 3 — Sign up at Render
1. Go to **https://render.com** → click **"Get Started"** → sign in with GitHub
2. Click **"New +"** at the top → **"Web Service"**
3. Find your `whichway-animals` repo and click **"Connect"**
4. On the setup page:
   - **Name:** `whichway-animals`
   - **Region:** pick closest to you
   - **Branch:** `main`
   - **Build Command:** `npm install`
   - **Start Command:** `npm start`
   - **Instance Type:** **Free**
5. Click **"Create Web Service"**

### Step 4 — Wait for it to deploy
Takes 2-3 minutes the first time. Render will give you a URL like `whichway-animals.onrender.com`.

✅ Test it: visit `whichway-animals.onrender.com/gm` — that's the Game Master page.

> **Heads up about the free tier:** the puzzle "sleeps" after 15 minutes of nobody using it, and takes 30-60 seconds to wake up the first time someone visits. Fine for an escape room because the GM sets up the room before players arrive. If you want it always-on, upgrade to Render's paid tier ($7/month) or use Railway ($5/month).

---

# PART 5 — Connect the animal puzzle to the Office Escape

Right now, if you click the "Conference" icon in the Office Escape, it goes to a placeholder URL. You need to fix that.

### Step 1 — Open `office.html` on GitHub
Go to your **WhichwayEscape** repo → click `office.html` → click the pencil icon (✏️).

### Step 2 — Find this line
Use Ctrl+F (or Cmd+F on Mac) to search for **`YOUR-ANIMAL-PUZZLE-URL`**. You'll find this:

```html
<li><a href="https://YOUR-ANIMAL-PUZZLE-URL.onrender.com/gm" target="_blank">📞 Join Team Conference</a></li>
```

### Step 3 — Replace it with your real Render URL
Change `YOUR-ANIMAL-PUZZLE-URL.onrender.com` to whatever Render gave you (like `whichway-animals.onrender.com`):

```html
<li><a href="https://whichway-animals.onrender.com/gm" target="_blank">📞 Join Team Conference</a></li>
```

### Step 4 — Commit
Scroll to the bottom → green **"Commit changes"** button. Cloudflare will see the change and update your live site within about a minute.

✅ Done. The Conference icon now opens the multiplayer puzzle.

---

# PART 6 — Day-to-day editing

After everything is set up, **updating your site is dead simple:**

1. Go to your repo on GitHub.
2. Click the file you want to change.
3. Click the pencil icon (✏️).
4. Edit the text.
5. Scroll down → click **"Commit changes"**.
6. Wait ~1 minute. Your live site is updated.

That's it. You don't have to touch Cloudflare or Render again unless you want to.

---

# Quick reference: the architecture

```
your-domain.com  →  Cloudflare Pages  →  WhichwayEscape repo  (the main site)
                                               │
                                               │  user clicks Conference icon
                                               ▼
whichway-animals.onrender.com  →  Render  →  whichway-animals repo  (the puzzle)
```

Two repos. Two hosting services. Both free. One domain.

---

# The honest cost breakdown for a real business

If you do exactly what I described above:

| Service | What it does | Monthly cost |
|---|---|---|
| GitHub | Stores your code | **$0** (drop the paid plan) |
| Cloudflare Pages | Hosts the main website | **$0** |
| Render Free | Hosts the multiplayer puzzle | **$0** (with cold-start caveat) |
| Domain registrar | Owns your domain | ~$1-2/month (paid yearly, ~$12-15/yr) |
| **Total** | | **~$1-2/month** |

If you want the puzzle to never have a cold-start delay (recommended once you're running real bookings):

| Service | What it does | Monthly cost |
|---|---|---|
| Render Starter | Always-on puzzle | $7/month |
| **Total with that upgrade** | | **~$8-9/month** |

Either way, **less than what you're currently paying GitHub.**
