# How to Add Gallery Photos

## Step 1 — Upload your image

Drop the image file into the `gallery/` folder.

Supported formats: `.jpg`, `.jpeg`, `.webp`, `.png`

Recommended: JPG or WebP, any size (they scale automatically in the masonry grid).

## Step 2 — Add the filename to `gallery/index.json`

Open `gallery/index.json` and add the filename to the array:

```json
["photo1.jpg", "himalaya-trek.jpg", "conference-nairobi.jpg"]
```

## Step 3 — Refresh

Reload the website. Your photo will appear in the gallery grid automatically.

## Tips

- Name files descriptively — the filename (minus extension) appears as a caption on hover.
- Use hyphens instead of spaces in filenames: `langtang-sunrise.jpg` not `langtang sunrise.jpg`.
- Vertical and horizontal photos both work — the masonry grid handles mixed orientations.
