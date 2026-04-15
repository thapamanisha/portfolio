# Manisha Thapa — Portfolio Website: Complete Guide

This is your personal portfolio website. It is a **static site** — meaning it runs entirely from HTML/CSS/JS files with no server, no database, and no paid hosting needed. It is hosted on **GitHub Pages**, which is free.

---

## Table of Contents

1. [How the site is structured](#structure)
2. [How to publish and update on GitHub Pages](#github)
3. [How to write a new blog post](#blogs)
4. [How to add photos to the gallery](#gallery)
5. [How to add a new video / talk](#media)
6. [How to add a new award](#awards)
7. [How to add a new research publication](#publications)
8. [How to update any other section](#other-sections)
9. [Can I avoid GitHub entirely?](#no-github)
10. [Tips for writing good blog posts](#writing-tips)

---

## 1. Site Structure {#structure}

```
manishathapa.github.io/
│
├── index.html              ← The entire portfolio (all sections live here)
├── assets/
│   ├── resume.pdf          ← Upload your latest CV here
│   └── photo.jpg           ← Your hero portrait (replace placeholder)
│
├── blogs/
│   ├── index.json          ← List of all blog posts (title, date, slug, excerpt)
│   ├── index.html          ← Blog listing page (auto-reads index.json)
│   ├── sample-post.html    ← TEMPLATE — copy this for every new post
│   ├── covers/             ← Cover images for each blog post
│   │   └── langtang.jpg
│   └── images/             ← Mid-post inline images (body of blog posts)
│       └── trail-morning.jpg
│
└── gallery/
    ├── index.json          ← List of photo filenames for the gallery grid
    └── photo1.jpg, photo2.jpg, ...
```

---

## 2. Publishing on GitHub Pages {#github}

### First-time setup
1. Create a free GitHub account at github.com if you don't have one.
2. Create a new repository. Name it `your-username.github.io` (replace `your-username` with your GitHub username). This makes the site available at that URL automatically.
3. Upload all the files from this package by clicking **Add file → Upload files**.
4. Go to **Settings → Pages**. Under "Source", select **Deploy from a branch**, choose `main`, click Save.
5. Wait 1–2 minutes. Your site will be live at `https://your-username.github.io`.

### Updating the site later
Whenever you want to change something:
1. Open the file in GitHub (click on the filename).
2. Click the pencil icon (Edit) in the top right.
3. Make your changes.
4. Click **Commit changes** at the bottom. The site updates automatically within 1–2 minutes.

For uploading new images or files: click **Add file → Upload files** in the relevant folder.

---

## 3. Writing a New Blog Post {#blogs}

### The process (step by step)

**Step 1 — Create your post file**
- In GitHub, navigate to the `blogs/` folder.
- Click **Add file → Create new file**.
- Name it: `your-post-slug.html` (use lowercase, hyphens not spaces — e.g. `nepal-climate-panel-2025.html`).
- Copy the entire content of `blogs/sample-post.html` and paste it into the new file.

**Step 2 — Edit the content**
Inside the new file, update:
- `<title>` tag at the top → your post title
- `.post-cat` → your category: `Travel`, `Advocacy`, `Art`, `Research`, or `Reflection`
- `h1.post-title` → your post title
- `.post-date` → the date, e.g. `December 3, 2025`
- Everything inside `<div class="post-body">` → your actual writing

**Step 3 — Add a cover image**
- Upload your cover photo to `blogs/covers/` (click Add file → Upload files inside that folder).
- In your post file, find the `<div class="post-hero">` tag and add:
  ```html
  style="background-image:url('../blogs/covers/your-photo.jpg');background-size:cover;background-position:center;"
  ```
  So it reads: `<div class="post-hero" style="background-image:url('../blogs/covers/langtang.jpg');background-size:cover;background-position:center;">`

**Step 4 — Add mid-post images (optional)**
- Upload images to `blogs/images/`.
- In your post, use the template blocks (already shown in the sample post):

  Single image:
  ```html
  <figure class="post-image">
    <img src="../blogs/images/your-photo.jpg" alt="Brief description of photo">
    <figcaption>Caption text shown at the bottom of the image</figcaption>
  </figure>
  ```

  Two side-by-side images:
  ```html
  <div class="post-image-pair">
    <figure class="post-image">
      <img src="../blogs/images/photo-left.jpg" alt="Left photo description">
      <figcaption>Caption for left image</figcaption>
    </figure>
    <figure class="post-image">
      <img src="../blogs/images/photo-right.jpg" alt="Right photo description">
      <figcaption>Caption for right image</figcaption>
    </figure>
  </div>
  ```

**Step 5 — Register the post in the index**
Open `blogs/index.json`. Add a new entry at the **top** of the array (so it appears first/most recent):

```json
[
  {
    "slug": "nepal-climate-panel-2025",
    "title": "Speaking at the Nepal Climate Panel",
    "date": "2025-12-03",
    "category": "Advocacy",
    "excerpt": "What I said, what I heard, and what still needs to change.",
    "cover": "blogs/covers/climate-panel.jpg"
  },
  ...existing entries...
]
```

The slug must exactly match your filename (without `.html`).

The homepage will automatically show the 3 most recent posts from this file.

### Image tips for blog posts
- Cover image: recommended 1200×700px or wider, JPG or WebP
- Body images (single): any width — max height is capped at 520px on screen
- Body images (pair): portrait or square work well for side-by-side
- Name files clearly: `langtang-trail-morning.jpg` not `IMG_4892.jpg`
- You can upload many images to `blogs/images/` in one go and reference them in different posts

---

## 4. Adding Photos to the Gallery {#gallery}

**Step 1** — Upload your photos to the `gallery/` folder via GitHub (Add file → Upload files).

**Step 2** — Open `gallery/index.json` and add the filenames:
```json
["himalaya-sunrise.jpg", "conference-nairobi.jpg", "kyanjin-gompa.jpg"]
```

The gallery auto-loads and shows a masonry grid. Photos are displayed in the order listed. On hover, the filename (without extension) appears as a caption — so `himalaya-sunrise.jpg` shows as "himalaya sunrise".

**Tips:**
- Mix portrait (tall) and landscape (wide) photos — the masonry grid handles both.
- Recommended: compress images to ~500KB each for fast loading (use squoosh.app).
- You can remove a photo by deleting it from the array in `index.json` (no need to delete the file).

---

## 5. Adding a New Video / Talk {#media}

All videos are in `index.html`, inside the `<!-- ═══ MEDIA / TALKS ═══ -->` section.

**Step 1** — Get the YouTube embed URL.
- On YouTube, go to the video → click Share → Embed.
- Copy just the video ID (the part after `v=`), e.g. `dQw4w9WgXcQ`.
- Your embed URL will be: `https://www.youtube.com/embed/dQw4w9WgXcQ`

**Step 2** — In `index.html`, find the comment that says:
```html
<!-- ADD MORE VIDEOS HERE — copy a video-card block above -->
```
Paste a new video card block just before that comment:
```html
<div class="video-card">
  <div class="video-wrapper">
    <iframe src="https://www.youtube.com/embed/YOUR_VIDEO_ID" title="Your Video Title" allowfullscreen loading="lazy"></iframe>
  </div>
  <div class="video-info">
    <div class="video-title">Your Video Title</div>
    <div class="video-desc">One or two sentences describing this talk or podcast.</div>
  </div>
</div>
```

**The grid auto-adjusts:**
- 3 videos → 3 columns in one row
- 4 videos → 2×2 grid
- 5 videos → 3 on top, 2 on bottom
- 6 videos → 3×2 grid

**To add a new "As Seen In" entry:**
Find the `media-mentions-row` div and add:
```html
<a href="https://link-to-article.com" target="_blank" class="media-mention-pill">
  <i class="fas fa-newspaper"></i> Publication Name
</a>
```
Icon options: `fa-newspaper`, `fa-award`, `fa-globe`, `fa-microphone`, `fa-tv`, `fa-podcast`

---

## 6. Adding a New Award {#awards}

The awards section is a **looping marquee** — cards scroll automatically from right to left.

Because the animation works by duplicating the row, you must add your new card in **two places**. In `index.html`, find the `<!-- ═══ AWARDS ═══ -->` section. There are two `<div class="awards-row">` blocks — one labeled "FIRST COPY" and one "SECOND COPY". Add your card to both.

Copy and paste this block into both rows:
```html
<div class="award-card">
  <div class="award-icon"><i class="fas fa-trophy"></i></div>
  <div class="award-title">Award Name</div>
  <div class="award-org">
    <!-- To link: <a href="URL" target="_blank" style="color:inherit;text-decoration:none;">Organization Name</a> -->
    Organization Name
  </div>
  <div class="award-year">2025</div>
</div>
```

Icon options: `fa-trophy`, `fa-star`, `fa-graduation-cap`, `fa-palette`, `fa-users`, `fa-globe`, `fa-newspaper`, `fa-medal`, `fa-award`, `fa-certificate`, `fa-map-marked-alt`

---

## 7. Adding a New Research Publication {#publications}

In `index.html`, find the `<!-- ═══ PUBLICATIONS ═══ -->` section. Copy and paste a `pub-card` block inside `<div class="pubs-grid">`:

```html
<!-- ADD NEW PUBLICATION: copy this block -->
<div class="pub-card">
  <span class="pub-badge">Research</span>
  <!-- Badge options: class="pub-badge" (orange/Research), class="pub-badge policy" (green/Policy), class="pub-badge blog" (gold/Blog) -->
  <h4>Full Title of Your Publication</h4>
  <div class="pub-meta">Organization · Year</div>
  <p class="pub-desc">One or two sentences describing what the publication covers and why it matters.</p>
  <a href="https://link-to-publication.pdf" target="_blank" class="pub-link">Read Report <i class="fas fa-arrow-right"></i></a>
</div>
```

---

## 8. Updating Other Sections {#other-sections}

All sections are in `index.html`. The HTML comments in that file (lines starting with `<!--`) explain every section. Use GitHub's file editor to make changes directly.

**About section** — update paragraphs inside `<div class="about-text">`.

**Work / Experience timeline** — each job is a `<div class="timeline-item">`. Copy an existing one and update the year, role, org name, and description.

**Skills** — add or remove `<span class="skill-tag">` elements inside any skill group.

**Instagram section** — update follower count in `.ig-stat`, niche tags in `.ig-niche-tags`, and the editorial paragraph text.

**Hero rotating words** — find the `<div class="hero-roles">` section and add/edit `<span class="hero-role">` items.

**Stat pills (About section)** — add or remove `<span class="pill">` elements inside `.stat-pills`.

---

## 9. Can I Avoid GitHub Entirely? {#no-github}

**Short answer:** For blogs and gallery, not easily without a paid tool. For everything else, yes — GitHub's web editor is the simplest option.

**Options without coding:**

Option A — **GitHub web editor (recommended, free)**
You never need to install anything. Just:
- Go to your repository on github.com
- Click a file → click the pencil icon to edit
- Commit changes when done
This is essentially a simple CMS. Takes about 2 minutes per update.

Option B — **GitHub Desktop app (easier drag-and-drop)**
Download GitHub Desktop (desktop.github.com). It lets you drag files in, write a short note, and click "Push" to publish. Better for uploading multiple photos at once.

Option C — **Future upgrade: Netlify CMS / Decap CMS (free, adds a visual editor)**
If you want a proper dashboard where you can write posts in a rich text editor without touching code, you can add Decap CMS (formerly Netlify CMS) to this site. It adds a `/admin` page where you log in and get a WordPress-like editor. This requires a one-time setup of about 30 minutes. Worth doing if you plan to post frequently. Ask a developer friend or search "Decap CMS GitHub Pages setup".

Option D — **Paid tools: Forestry.io / TinaCMS**
These add visual dashboards to static sites, including image uploads and blog editors. They have free tiers. Ask a developer to connect one of these to this repo if you want a fully no-code editing experience.

---

## 10. Writing Tips {#writing-tips}

- The `<blockquote>` element is your highlight line — use it for one memorable sentence per post. Not a direct quote necessarily, just the line you most want a reader to remember.
- You can add as many inline images as you want — just repeat the `<figure class="post-image">` block.
- Keep body images under 800KB each. Use squoosh.app (free, browser-based) to compress.
- The post title and category are shown on the homepage card — make the title specific and the excerpt conversational, not formal.
- Add new posts to the top of `blogs/index.json` so the most recent one appears first everywhere.

---

*This guide covers everything you need to manage and grow this portfolio independently. For any questions not covered here, the HTML comments throughout `index.html` and `blogs/sample-post.html` provide section-by-section instructions inline.*
