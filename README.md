# విజ్ఞాన భారతి (vBharati) - Telugu Literary Magazine

A digital Telugu literary magazine website featuring articles organized by issue, author pages, and a clean editorial design optimized for Telugu typography.

**Live site:** https://vbharati.com (when deployed)

## Table of Contents

- [Project Structure](#project-structure)
- [Design System](#design-system)
- [For Editors: Managing Content](#for-editors-managing-content)
  - [Adding a New Article](#adding-a-new-article)
  - [Creating a New Issue](#creating-a-new-issue)
  - [Adding a New Author](#adding-a-new-author)
  - [Editing Existing Content](#editing-existing-content)
- [For Developers](#for-developers)
- [Conventions & Standards](#conventions--standards)

---

## Project Structure

```
vbharati/
├── index.html              # Homepage with featured article + article grid
├── about.html              # About page
├── search.html             # Search/browse page
├── styles.css              # All CSS styles
├── articles/               # Article pages
│   ├── telugu-sahityam.html
│   ├── bhasha-technology.html
│   └── kavita-vishleshanam.html
├── authors/                # Author profile pages
│   ├── srinivas-rao.html
│   ├── lakshmi-narasimham.html
│   └── padmavati-devi.html
├── .gitignore
└── README.md
```

### Key Files

| File | Purpose |
|------|---------|
| `index.html` | Homepage - contains hero section, subscribe banner, and all article cards |
| `styles.css` | All styling - edit this to change colors, fonts, spacing |
| `articles/*.html` | Individual article pages with full content |
| `authors/*.html` | Author profile pages listing their articles |

---

## Design System

### Fonts
- **Headings:** Noto Serif Telugu (serif, weight 400)
- **Body text:** Noto Sans Telugu (sans-serif)
- **English text:** Inter

### Colors
| Variable | Value | Usage |
|----------|-------|-------|
| `--color-bg` | `#ffffff` | Page background |
| `--color-text` | `#1a1a1a` | Primary text |
| `--color-text-light` | `#404040` | Body text |
| `--color-text-muted` | `#6b6b6b` | Secondary text, dates |
| `--color-accent` | `#2563eb` | Blue accent (left borders, links) |
| `--color-dark` | `#1a1a1a` | Buttons, dark elements |

### Article Types (Tags)
Use these standard tags for consistency:
- `దీర్ఘ వ్యాసం` - Long Read
- `అన్వేషణ` - Exploration/Investigation
- `విమర్శ` - Criticism/Review
- `సంస్కృతి` - Culture
- `చరిత్ర` - History
- `పుస్తక పరిచయం` - Book Review
- `సంపాదకీయం` - Editorial
- `ప్రత్యేకం` - Special Feature

---

## For Editors: Managing Content

### Adding a New Article

#### Step 1: Create the article file

Create a new HTML file in the `articles/` directory. Use a URL-friendly filename in English (lowercase, hyphens instead of spaces).

**Filename format:** `articles/[topic-in-english].html`

**Example:** `articles/new-poetry-trends.html`

#### Step 2: Copy the article template

Copy an existing article (e.g., `articles/telugu-sahityam.html`) and modify:

```html
<!-- Update in <head> -->
<title>[Article Title in Telugu] | విజ్ఞాన భారతి</title>

<!-- Update article header -->
<div class="article-meta">
    <span class="tag-pill">[Article Type]</span>
    <span class="tag-pill">సంచిక [Issue Number]</span>
</div>
<h1 class="article-page-title">[Article Title in Telugu]</h1>
<p class="article-byline">Words by <a href="/authors/[author-slug].html">[Author Name]</a></p>
<p class="article-date">[Month] [Day], [Year]</p>

<!-- Update hero placeholder text -->
<div class="article-hero-placeholder">[Short Label]</div>

<!-- Replace article content -->
<div class="article-content">
    <p><span class="drop-cap">[First Letter]</span>[Rest of first paragraph...]</p>

    <h2>[Section Heading]</h2>
    <p>[Paragraph text...]</p>

    <blockquote>[Quote text...]</blockquote>

    <ul>
        <li>[List item]</li>
    </ul>
</div>

<!-- Update related articles -->
<section class="related-articles">
    <h3>సంబంధిత వ్యాసాలు</h3>
    <div class="related-list">
        <a href="[related-article].html" class="related-item">
            <span class="related-item-title">[Related Article Title]</span>
            <span class="related-item-meta">[Type] • సంచిక [Number]</span>
        </a>
    </div>
</section>
```

#### Step 3: Add to homepage

Open `index.html` and add an article card in the `<div class="articles-grid">` section:

```html
<article class="article-card">
    <a href="articles/[filename].html" class="article-link">
        <div class="article-tags">
            <span class="tag-pill">[Article Type]</span>
            <span class="tag-pill">సంచిక [Issue Number]</span>
        </div>
        <h2 class="article-title">[Article Title]</h2>
        <p class="article-author">Words by <a href="/authors/[author-slug].html">[Author Name]</a></p>
        <p class="article-excerpt">
            [First 2-3 sentences of the article as preview...]
        </p>
    </a>
</article>
```

**Card placement:** Newer articles should appear first. Articles are displayed in a 2-column grid.

#### Step 4: Update author page

Add the article to the author's page in `authors/[author-slug].html`:
- Add to the articles grid
- Update the article count

---

### Creating a New Issue

Issues are represented by the `సంచిక [Number]` tag on articles. To create a new issue:

1. **Decide the issue number** (e.g., `సంచిక 04`)

2. **Update the hero section** in `index.html` if featuring an article from the new issue:
   ```html
   <section class="hero-featured">
       <div class="hero-content">
           <h1 class="hero-title">
               <a href="articles/[new-featured-article].html">[New Featured Title]</a>
           </h1>
           ...
       </div>
   </section>
   ```

3. **Add new articles** with the new issue tag

4. **Update search page** (`search.html`) to include the new issue in the browse section:
   ```html
   <a href="/" class="issue-card">
       <span class="issue-number">04</span>
       <p class="issue-info">[Month] [Year] • [N] వ్యాసాలు</p>
   </a>
   ```

---

### Adding a New Author

#### Step 1: Create author page

Create a new file in `authors/` directory.

**Filename format:** `authors/[firstname-lastname].html` (transliterated to English)

**Example:** `authors/ramakrishna-rao.html`

#### Step 2: Use the author template

```html
<!DOCTYPE html>
<html lang="te">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>[Author Name Telugu] | విజ్ఞాన భారతి</title>
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700&family=Noto+Sans+Telugu:wght@400;500;600;700&family=Noto+Serif+Telugu:wght@400;500;600;700&display=swap" rel="stylesheet">
    <link rel="stylesheet" href="../styles.css">
</head>
<body>
    <header class="header">
        <div class="container">
            <nav class="nav">
                <a href="/" class="logo">విజ్ఞాన భారతి</a>
                <div class="nav-links">
                    <a href="/" class="nav-link">వ్యాసాలు</a>
                    <a href="/about.html" class="nav-link">మా గురించి</a>
                    <a href="/search.html" class="nav-link">వెతుకు</a>
                </div>
            </nav>
        </div>
    </header>

    <main class="main author-page">
        <div class="container">
            <section class="author-header">
                <div class="author-avatar">[First Letter of Name]</div>
                <div class="author-info">
                    <h1 class="author-name">[Author Name in Telugu]</h1>
                    <p class="author-bio">[2-3 sentence bio in Telugu]</p>
                    <p class="author-articles-count">[N] వ్యాసాలు</p>
                </div>
            </section>

            <hr class="section-divider">

            <section class="author-articles">
                <h2 class="section-title">వ్యాసాలు</h2>
                <div class="articles-grid">
                    <!-- Add article cards here -->
                </div>
            </section>
        </div>
    </main>

    <footer class="footer">
        <!-- Copy footer from another page -->
    </footer>
</body>
</html>
```

#### Step 3: Link from articles

Update any articles by this author to link to their page:
```html
<p class="article-byline">Words by <a href="/authors/[author-slug].html">[Author Name]</a></p>
```

---

### Editing Existing Content

#### To edit an article's content:
1. Open `articles/[article-name].html`
2. Edit the text within `<div class="article-content">`
3. If changing the title, also update it in:
   - The `<title>` tag
   - The `<h1 class="article-page-title">`
   - The article card in `index.html`
   - Any "related articles" sections that reference it

#### To change the featured article on homepage:
1. Open `index.html`
2. Update the `<section class="hero-featured">` section with new article link and title

#### To reorder articles:
1. Open `index.html`
2. Move the `<article class="article-card">` blocks to desired positions
3. Articles display left-to-right, top-to-bottom in a 2-column grid

---

## For Developers

### Local Development

Serve the site locally with any static file server:

```bash
# Python
python3 -m http.server 8888

# Node.js (if you have npx)
npx serve

# Then open http://localhost:8888
```

### Deployment

This is a static site. Deploy to any static hosting:
- **Netlify:** Drop the folder or connect to Git
- **Vercel:** Connect to Git repository
- **GitHub Pages:** Push to `gh-pages` branch
- **Cloudflare Pages:** Connect to Git repository

### Adding Images

When adding images to articles:

1. Create an `images/` directory if it doesn't exist
2. Use descriptive filenames: `images/article-name-description.jpg`
3. In article HTML, replace the placeholder:
   ```html
   <!-- Replace this -->
   <div class="article-hero-placeholder">Label</div>

   <!-- With this -->
   <img src="/images/your-image.jpg" alt="Description in Telugu">
   ```

### Future Enhancements

Potential improvements for later:
- [ ] Add actual images for articles and authors
- [ ] Implement search functionality with JavaScript
- [ ] Add RSS feed
- [ ] Create issue archive pages
- [ ] Add newsletter signup backend
- [ ] Convert to a static site generator (11ty, Hugo) for easier content management

---

## Conventions & Standards

### File Naming
- **Articles:** `articles/[english-topic-slug].html` (lowercase, hyphens)
- **Authors:** `authors/[firstname-lastname].html` (transliterated, lowercase, hyphens)
- **Images:** `images/[article-slug]-[description].jpg`

### Telugu Text
- All user-facing content should be in Telugu
- Use `lang="te"` on the `<html>` tag
- Dates in Telugu: `జనవరి 15, 2026`

### HTML Structure
- Every page must include the standard header and footer
- Use semantic HTML (`<article>`, `<section>`, `<nav>`, `<header>`, `<footer>`)
- Maintain consistent indentation (4 spaces)

### Git Commits
- Write clear commit messages describing what changed
- Commit related changes together (e.g., new article + homepage update + author page update)

---

## Content Checklist for New Articles

Before publishing a new article, verify:

- [ ] Article file created in `articles/` with correct filename
- [ ] Title updated in `<title>` and `<h1>`
- [ ] Correct issue number in tag pill
- [ ] Author name links to correct author page
- [ ] Date is accurate
- [ ] Drop cap on first paragraph
- [ ] Related articles section updated
- [ ] Article card added to `index.html`
- [ ] Author's page updated with new article
- [ ] Article count on author page is correct
- [ ] All internal links work

---

## Support

For questions about content management, contact the editorial team at contact@vbharati.com.

For technical issues, open an issue in the repository.
