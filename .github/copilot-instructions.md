# Copilot Instructions for Yura Homepage

## Project Overview
This is a Japanese-language personal Tech Note site hosted on GitHub Pages (`Yura0326.github.io`). The site is a static website built with pure HTML/CSS using the MVP.css framework, serving as a knowledge base for technical documentation and development progress.

### Content Strategy
- **Purpose**: Share technical details and assets from ongoing development projects
- **Format**: Wiki-style documentation (not blog-style chronological posts)
- **Primary focus**: Game engine development (Volatile project - private GitHub repo)
- **Update digest**: Homepage shows summaries of latest content updates

## Architecture

### Site Structure
- `index.html` - Main landing page with sidebar profile and update digest feed
- `posts/` - Update digest entries (naming: `001_hello.html`, `002_...`, etc.)
- `Game/` - Wiki pages for game/game engine development content
- `Techs/` - Wiki pages for embedded systems and AI technology
- `Notes/` - Wiki pages for miscellaneous technical notes
- `yura_icon.png` - Profile image displayed in sidebar

### Content Categories
1. **Game** - ゲーム・ゲームエンジン開発
   - Primary: Volatile game engine (C++ project at `E:\dev\MyCppGame`)
   - GitHub: https://github.com/Yura0326/Volatile (Private repository)
2. **Techs** - 組み込み技術、AI技術
3. **Notes** - その他の技術メモ

### Layout System
The homepage uses a two-column flexbox layout (desktop only):
- **Left sidebar** (`<aside>`): Fixed 250px width, profile info and links
- **Right main content** (`.main-content`): Flexible width, article feed
- Mobile: Stacks vertically automatically

## Key Conventions

### Language
- All UI text, content, and comments are in **Japanese**
- Use Japanese for new content, descriptions, and documentation

### Styling Approach
- **Base framework**: MVP.css loaded via CDN (`https://unpkg.com/mvp.css`)
- **Custom styles**: Defined in `<style>` block within each HTML file
- Key customizations in index.html:
  - Tight spacing with reduced padding/margins
  - Flexbox layout for sidebar + main content
  - Articles stacked vertically with dashed dividers

### Blog Post Pattern
New posts follow this structure:
```html
<!-- In index.html updates section -->
<article>
    <h3><a href="posts/00X_title.html">Japanese Title</a></h3>
    <p>Brief description</p>
    <small>YYYY/MM/DD - Category</small>
</article>
```

Individual post files (`posts/00X_*.html`):
- Full standalone HTML with MVP.css
- Back link to `../index.html` in nav
- Date and category in header
- Use `<pre><code>` for code snippets

### Wiki Page Pattern
Wiki pages are organized by category folders (Game/Techs/Notes):
```html
<!-- Wiki page structure -->
<!DOCTYPE html>
<html lang="ja">
<head>
    <meta charset="UTF-8">
    <title>Page Title - Category</title>
    <link rel="stylesheet" href="https://unpkg.com/mvp.css">
</head>
<body>
    <nav><a href="../index.html">← Top</a></nav>
    <h1>Page Title</h1>
    <!-- Content with sections, code examples, images -->
</body>
</html>
```

**Wiki page guidelines**:
- Topic-focused, not chronological (unlike posts/)
- Can be updated/expanded over time without date stamps
- Cross-link related wiki pages within same or different categories
- Use descriptive filenames (e.g., `entity_component_system.html`)

### Update Digest (posts/)
- `posts/` directory contains update summaries, not full content
- Each post announces new/updated wiki content with brief description
- Links to relevant wiki pages in Game/, Techs/, or Notes/
- Maintains chronological update history on homepage

### File Naming
- Posts: Sequential numbering `001_`, `002_`, etc. with descriptive suffix
- Keep filenames lowercase and use underscores

## Development Workflow

### Local Preview
Since this is static HTML, simply open files in a browser:
- Use Live Server extension or similar for hot reload
- Or directly open `index.html` in browser (file:// protocol)

### Deployment
- Push to `main` branch → automatically published to `https://yura0326.github.io/`
- No build step required (pure HTML/CSS)

## Adding New Content

### New Wiki Page
1. Create page in appropriate category folder: `Game/`, `Techs/`, or `Notes/`
2. Use descriptive filename (e.g., `volatile_engine_architecture.html`)
3. Follow wiki page structure with back link to top
4. Add cross-references to related wiki pages

### New Update Digest
1. Create `posts/00X_title.html` with next sequential number
2. Copy structure from `001_hello.html` as template
3. Add article entry to `index.html` in the Update section
4. Link to new/updated wiki pages from the digest
5. Update date and category appropriately (Game/Techs/Notes)

### Navigation Updates
Update the nav menu in `index.html` when adding new sections (currently placeholders: Games, Techs, Notes, Contact)
