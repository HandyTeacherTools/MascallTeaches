# mascallteaches.com

A parent resource hub for Mr. Mascall's Grades 4–6 students.  
Built as a static site hosted on GitHub Pages with a custom domain.

---

## Site Structure

```
mascallteaches/
├── index.html          ← Homepage
├── resources.html      ← All resources with subject filter
├── about.html          ← About Mr. Mascall
├── contact.html        ← Contact form
├── css/
│   └── style.css       ← All styles
├── js/
│   └── main.js         ← Nav toggle, filter tabs, scroll animations
└── resources/          ← PDF files go here (upload your own)
    ├── reading-strategies.pdf
    ├── writing-checklist.pdf
    └── ... etc.
```

---

## How to Deploy (GitHub Pages + Custom Domain)

### Step 1 — Create a GitHub repo
1. Go to [github.com](https://github.com) and sign in (or create a free account)
2. Click **New repository**
3. Name it exactly: `mascallteaches.com` (or any name you prefer)
4. Set it to **Public**
5. Click **Create repository**

### Step 2 — Upload files
1. Click **uploading an existing file** on the new repo page
2. Drag all the files from this folder into the upload area (keep the folder structure)
3. Click **Commit changes**

### Step 3 — Enable GitHub Pages
1. In your repo, go to **Settings → Pages**
2. Under **Source**, select **Deploy from a branch**
3. Choose branch: `main`, folder: `/ (root)`
4. Click **Save**
5. GitHub will give you a URL like `https://yourusername.github.io/mascallteaches.com`

### Step 4 — Connect your custom domain
1. Buy `mascallteaches.com` at [Namecheap.com](https://namecheap.com) (~$15 CAD/yr)
2. In Namecheap, go to **Advanced DNS** for the domain and add:
   ```
   Type: A     Host: @    Value: 185.199.108.153
   Type: A     Host: @    Value: 185.199.109.153
   Type: A     Host: @    Value: 185.199.110.153
   Type: A     Host: @    Value: 185.199.111.153
   Type: CNAME Host: www  Value: yourusername.github.io.
   ```
3. Back in GitHub Pages settings, enter `mascallteaches.com` under **Custom domain**
4. Check **Enforce HTTPS** once it verifies (can take up to 24 hours)

---

## Adding Resources (PDFs)

1. Put your PDF files in the `/resources/` folder in your GitHub repo
2. In `resources.html`, update the `href` on each card's download link to match the filename:
   ```html
   <a href="resources/your-file-name.pdf" class="resource-download">↓ Download</a>
   ```
3. Commit the changes — the site updates automatically

---

## Enabling the Contact Form

The contact form is wired up but needs a free backend to send email:

1. Sign up at [formspree.io](https://formspree.io) (free tier sends up to 50 emails/month)
2. Create a new form and copy your form ID (looks like `xpwzabcd`)
3. In `contact.html`, find the `<form>` tag and change:
   ```html
   <form action="#" method="POST">
   ```
   to:
   ```html
   <form action="https://formspree.io/f/YOUR_FORM_ID" method="POST">
   ```
4. In `js/main.js`, delete the contact form submit listener block (lines ~38–45) so the real form submission works

---

## Ongoing Maintenance

- **Add a resource:** Upload PDF to `/resources/`, add a card in `resources.html`
- **Update About text:** Edit `about.html` directly
- **Change colors:** Edit the CSS variables at the top of `css/style.css`

That's it — no server, no plugins, no updates to worry about.
