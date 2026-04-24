# SSSSSSL.ORG
## Sloped Landscape Organism Research Group — Lina Bondarenko

---

## Folder structure

```
ssssssl/
  index.html                 ← homepage (the S navigation)
  style.css                  ← shared styles — edit once, updates everywhere
  README.md                  ← this file
  CNAME                      ← tells GitHub Pages to use ssssssl.org
  projects/
    project-template.html    ← copy this for every new project
    solstice-slorg.html
    solar-slorg.html
    slope-scene.html
    ... etc
  media/
    solstice-slorg-01.jpg    ← put images and videos here
    solstice-slorg-02.jpg
    ... etc
```

---

## Adding a new project

1. Copy `projects/project-template.html`
2. Rename it to match the project, e.g. `projects/new-project.html`
3. Open it and edit:
   - `<title>` and `<meta name="description">` at the top
   - `project-category` span (the vermillion label)
   - `project-title` h1
   - The media grid (swap placeholder divs for real images/video)
   - The metadata on the left (year, location, duration, collaborators)
   - The text paragraphs on the right
   - The prev/next links at the bottom
4. Add the new project link to `index.html` in the relevant S section

---

## Adding images or video

Put your files in the `media/` folder. Then in the project page replace:

```html
<div class="media-item placeholder" data-label="image or video"></div>
```

with:

```html
<div class="media-item">
  <img src="../media/your-image.jpg" alt="Brief description of image">
</div>
```

For video:
```html
<div class="media-item">
  <video src="../media/your-video.mp4" autoplay muted loop playsinline></video>
</div>
```

For Vimeo:
```html
<div class="media-item" style="aspect-ratio: 16/9;">
  <iframe src="https://player.vimeo.com/video/YOUR_VIDEO_ID"
    width="100%" height="100%" frameborder="0"
    allow="autoplay; fullscreen" allowfullscreen></iframe>
</div>
```

---

## Hosting on GitHub Pages + Cloudflare

### First time setup

1. Create a GitHub account at github.com if you don't have one
2. Create a new repository — name it anything (e.g. `ssssssl`)
3. Upload all these files (drag and drop works in the GitHub interface)
4. Go to repository Settings → Pages
5. Under "Source" select: Deploy from branch → main → / (root)
6. GitHub will give you a URL like `yourusername.github.io/ssssssl`

### Connecting your Cloudflare domain

1. In your GitHub repo, make sure the `CNAME` file contains just: `ssssssl.org`
2. In Cloudflare DNS, add these records:
   - Type: `CNAME` | Name: `@` | Target: `yourusername.github.io`
   - Type: `CNAME` | Name: `www` | Target: `yourusername.github.io`
3. In Cloudflare SSL/TLS settings, set to "Full"
4. Wait up to 24 hours for DNS to propagate

### Updating the site after changes

1. Make your edits to the HTML/CSS files on your computer
2. Go to your GitHub repository
3. Click the file you changed, then the pencil (edit) icon — or drag and drop new files
4. The site updates within a minute or two

---

## Editing global styles

Open `style.css`. The tokens at the top control the whole site:

```css
:root {
  --bg:         #080f09;   /* background — near-black green */
  --sand:       #E6D9B8;   /* main text colour */
  --vermillion: #D44B1A;   /* highlight / hover colour */
}
```

Change these and every page updates at once.

---

## Replacing the S navigation with your Illustrator SVG

When your section drawing is ready:

1. Export from Illustrator as SVG
2. Open `index.html`
3. Find the comment `<!-- SVG SECTION DRAWING GOES HERE -->` (you or I will add this)
4. Paste your SVG there
5. Give each clickable zone in the SVG an `id` matching the zone names
6. The existing hover JavaScript will wire up automatically

---
