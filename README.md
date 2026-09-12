# Buford County Sheriff's Office — Website

A modern, static website for BCSO: a home page, an About/Command Staff page, a Careers page, and a Contact page. Every file sits flat in one folder — no subfolders to worry about — so you can drag-and-drop it straight into GitHub.

## What's in this folder

```
index.html      Home page   (styles + script inlined)
about.html       About BCSO / Command Staff
careers.html     Careers & open positions
contact.html     Contact form + info
badge.png         Your department badge/logo
README.md         This guide
```

Each HTML page carries its own `<style>` and `<script>` block inside it, so there's no separate CSS or JS file to link up — every page works completely on its own. If you edit a style, you'll need to copy that change into all four HTML files (see the note at the bottom).

---

## 1. Preview it on your own computer

Just double-click any `.html` file (start with `index.html`) and it'll open in your browser. Because there are no external files to load, this works even without a local server.

If you'd rather run a quick local server (optional):
```bash
python3 -m http.server 8000
```
then open `http://localhost:8000`.

---

## 2. Upload it to GitHub (no command line needed)

1. On GitHub, create a new repository (e.g. `bcso-website`). Don't add a README — you already have one.
2. On the repo page, click **Add file → Upload files**.
3. Drag in all six files — `index.html`, `about.html`, `careers.html`, `contact.html`, `badge.png`, `README.md` — directly, no folders involved.
4. Scroll down and click **Commit changes**.

That's it — everything's flat, so there's no folder structure to preserve during upload.

### Prefer the command line?
```bash
cd bcso-website
git init
git add .
git commit -m "Initial BCSO website"
git branch -M main
git remote add origin https://github.com/YOUR-USERNAME/bcso-website.git
git push -u origin main
```

---

## 3. Publish it for free with GitHub Pages

1. In your repository, click **Settings**.
2. In the left sidebar, click **Pages**.
3. Under **Build and deployment → Source**, choose **Deploy from a branch**.
4. Under **Branch**, choose **main** and folder **/ (root)**, then **Save**.
5. Wait a minute, refresh, and GitHub will show your live link:
   ```
   https://YOUR-USERNAME.github.io/bcso-website/
   ```

Push any future changes to `main` and the live site updates automatically within a minute or two.

---

## 4. Customize the content

- **Logo/badge** — replace `badge.png` with your own image (keep the same filename, or find-and-replace `badge.png` in all four HTML files).
- **Sheriff's name, quotes, mission** — edit directly inside `index.html` and `about.html`.
- **Command Staff roster** — in `about.html`, duplicate one `.staff-card` block for each new person, and remove the `vacant` class once a position is filled.
- **Career listings** — in `careers.html`, each opening is one `.card` block inside `id="openings"`. Copy, paste, and edit to add a new role; delete a block to remove one.
- **Colors** — search each HTML file for `:root {` near the top of the `<style>` block — that's where `--teal-900`, `--gold-600`, and the rest are defined. Change a value there and it updates everywhere that color is used **on that page**.
- **Fonts** — the site uses Google Fonts (`Source Serif 4` for headings, `Public Sans` for body text), loaded via a `<link>` in each page's `<head>`.

### A note on editing styles across all four pages
Because the CSS is now copied into each HTML file rather than linked from one shared file, a style change needs to be made in all four files to stay consistent. If you're planning to make a lot of style changes, it's worth asking to switch back to a shared `css/styles.css` file — it's less duplication, just one extra folder in the upload.

## 5. Connect the contact form (optional)

The form on `contact.html` doesn't send anywhere yet — it just shows a placeholder message. To make it deliver real messages:

- **[Formspree](https://formspree.io)** (free tier available) — sign up, create a form, and you'll get a URL like `https://formspree.io/f/xxxxxxx`. In `contact.html`, change:
  ```html
  <form onsubmit="event.preventDefault(); ...">
  ```
  to:
  ```html
  <form action="https://formspree.io/f/xxxxxxx" method="POST">
  ```
  and delete the `onsubmit="..."` part.
- **A Google Form** — swap the form for a link/button to your Google Form, the same way the "Submit a Commendation" button works on the home page.

## 6. Custom domain (optional)

Buy a domain from any registrar, then in **Settings → Pages**, enter it under **Custom domain**. GitHub will show you the DNS records to add at your registrar.

---

## Notes

- This is a fan/roleplay department site inspired by your Google Sites page, rebuilt as a standalone, modern static site — it isn't affiliated with any real government agency.
- Everything is plain HTML/CSS/JS on purpose: no npm install, no build step, easy for anyone on the team to edit a line of text and push it live.
