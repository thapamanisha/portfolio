# How to Add Blog Posts

## Step 1 — Add entry to `blogs/index.json`

Open `blogs/index.json` and add a new object to the array:

```json
{
  "slug": "your-post-slug",
  "title": "Your Post Title",
  "date": "2025-12-01",
  "category": "Travel",
  "excerpt": "A short 1-2 sentence preview shown on the homepage.",
  "cover": "blogs/covers/your-image.jpg"
}
```

Categories: `Travel`, `Advocacy`, `Art`, `Research`, `Reflection`

## Step 2 — Add cover image

Drop your cover image into `blogs/covers/` and name it to match the `cover` field above.

Recommended size: 800×500px, JPG or WebP.

## Step 3 — Create the post HTML file

Copy `blogs/sample-post.html` and rename it to `blogs/your-post-slug.html`.

Edit the title, date, category, and body content inside.

## That's it

The homepage automatically loads the 3 most recent posts from `index.json` (sorted by date).
The `blogs/index.html` listing page loads all posts.
