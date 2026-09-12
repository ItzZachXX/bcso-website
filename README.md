# Buford County Sheriff's Office — Website

A modern, static website for BCSO: a home page, an About/Command Staff page, a Careers page, and a Contact page. No build tools, frameworks, or backend required — it's plain HTML, CSS, and a few lines of JavaScript, so it runs anywhere, including GitHub Pages, for free.

## What's in this folder

```
bcso-website/
├── index.html          Home page
├── about.html           About BCSO / Command Staff
├── careers.html         Careers & open positions
├── contact.html         Contact form + info
├── css/
│   └── styles.css       All site styling (colors, layout, responsive rules)
├── js/
│   └── script.js        Mobile menu toggle + footer year
├── assets/
│   └── badge.png        Your department badge/logo
└── README.md             This guide
```

Every page shares the same header (logo centered between two groups of tabs) and footer, so editing `css/styles.css` updates the look of the whole site at once.

---

## 1. Preview it on your own computer

You don't need to install anything to look at the site, but opening `index.html` directly (double-click) will work for a quick look. For it to behave exactly like it will online (some browsers block a few things when opening files directly), run a tiny local server instead:

**If you have Python installed** (Mac/Linux usually do; Windows can install it from python.org):
```bash
cd bcso-website
python3 -m http.server 8000
```
Then open `http://localhost:8000` in your browser.

**If you have Node.js installed:**
```bash
npx serve bcso-website
```

Either way, edit the HTML/CSS files, save, and refresh your browser to see changes.

---

## 2. Put it on GitHub

1. Create a new repository on GitHub (e.g. `bcso-website`). Don't initialize it with a README — you already have one.
2. On your computer, open a terminal in this folder and run:
   ```bash
   git init
   git add .
   git commit -m "Initial BCSO website"
   git branch -M main
   git remote add origin https://github.com/YOUR-USERNAME/bcso-website.git
   git push -u origin main
   ```
3. Refresh your repository page on GitHub — all the files should now be there.

---

## 3. Publish it for free with GitHub Pages

1. In your repository on GitHub, click **Settings**.
2. In the left sidebar, click **Pages**.
3. Under **Build and deployment → Source**, choose **Deploy from a branch**.
4. Under **Branch**, choose **main** and folder **/ (root)**, then click **Save**.
5. Wait a minute, then refresh the page — GitHub will show a link like:
   ```
   https://YOUR-USERNAME.github.io/bcso-website/
   ```
   That's your live site. Share that link with your department.

Any time you push new changes to `main`, GitHub Pages redeploys automatically within a minute or two.

---

## 4. Customize the content

Everything is written directly in the HTML, so there's no admin panel — you edit the text where you see it:

- **Logo/badge** — replace `assets/badge.png` with your own image (keep the same filename, or update the `src="assets/badge.png"` references in all four HTML files).
- **Sheriff's name, quotes, mission** — edit directly inside `index.html` and `about.html`.
- **Command Staff roster** — in `about.html`, duplicate one `.staff-card` block for each new person, and remove the `vacant` class once a position is filled.
- **Career listings** — in `careers.html`, each opening is one `.card` block inside `#openings`. Copy, paste, and edit to add a new role; delete a block to remove one.
- **Colors** — all colors are defined once at the top of `css/styles.css` under `:root` (look for `--teal-900`, `--gold-600`, etc.). Change a value there and it updates everywhere that color is used.
- **Fonts** — the site uses Google Fonts (`Source Serif 4` for headings, `Public Sans` for body text), loaded via a `<link>` tag in each page's `<head>`. Swap the font names there and in `css/styles.css` (`--font-display` / `--font-body`) to change them.

## 5. Connect the contact form (optional)

Right now, the form on `contact.html` doesn't send anywhere — it just shows a placeholder message so you can see it working. To make it actually deliver messages, without running your own server, the easiest options are:

- **[Formspree](https://formspree.io)** — free tier available. Sign up, create a form, and they give you a URL like `https://formspree.io/f/xxxxxxx`. Then in `contact.html`, change:
  ```html
  <form onsubmit="event.preventDefault(); ...">
  ```
  to:
  ```html
  <form action="https://formspree.io/f/xxxxxxx" method="POST">
  ```
  and delete the `onsubmit="..."` bit. Submissions will start arriving in your email.
- **A Google Form** — simplest option if you already use one (like the Commendation Form this site links to). Just swap the whole form for a link/button to your Google Form, the same way the "Submit a Commendation" button works on the home page.

## 6. A note on custom domains (optional)

If you'd rather use something like `www.bufordcountyso.com` instead of the `github.io` address, buy the domain from any registrar (Namecheap, Google Domains successor Squarespace Domains, etc.), then in your repo's **Settings → Pages**, enter it under **Custom domain**. GitHub will show you the DNS records to add at your registrar. It usually takes effect within an hour or two.

---

## Notes

- This is a fan/roleplay department site inspired by your Google Sites page, rebuilt as a standalone, modern static site — it isn't affiliated with any real government agency.
- Everything is plain HTML/CSS/JS on purpose: no npm install, no build step, easy for anyone on the team to edit a line of text and push it live.
