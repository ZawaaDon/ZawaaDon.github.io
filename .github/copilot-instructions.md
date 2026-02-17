# Copilot Instructions for ZawaaDon Homepage

## Project Overview
This is a Japanese-language personal portfolio and tech blog site hosted on GitHub Pages (`ZawaaDon.github.io`). The site is a static website built with pure HTML/CSS using the MVP.css framework, serving as a hub for showcasing projects and sharing technical articles.

### Content Strategy
- **Purpose**: Portfolio hub for projects (Gallery) and technical blog posts (Blogs)
- **Format**: Static HTML with Markdown support for blog articles
- **Primary focus**: Game engine development (Volatile project - private GitHub repo), technical experiments, and learning notes
- **Update digest**: Homepage shows recent updates in sidebar

## Architecture

### Site Structure
- `index.html` - Main landing page with category cards (Gallery/Blogs) and sidebar
- `Gallery/index.html` - Project portfolio showcase with card grid layout
- `Notes/index.html` - Blog article list (named "Blogs" in UI)
- `posts/` - Individual blog articles
  - `001_hello.html` - Site launch post
  - `template_compact.html` - Template for creating new blog posts

### Content Categories
1. **Gallery** (成果物ギャラリー) - Project portfolio
   - Game development projects (e.g., Volatile Engine)
   - Embedded systems projects
   - AI/ML implementations
   - Card grid layout with project metadata
   
2. **Blogs** (技術記事・メモ) - Technical blog
   - Development notes and research
   - Technology investigations
   - Learning journals
   - List format with article summaries

### Layout System
All pages use a consistent two-column layout (desktop @800px+):
- **Left sidebar** (`<aside>`): Fixed 250px width
  - Links (SNS)
  - About section
  - Recent Updates
- **Right main content** (`.main-content`): Flexible width
- Mobile: Stacks vertically automatically

### Navigation
Unified header across all pages:
- Site title: "ZawaaDon Homepage"
- Navigation: Home | Gallery | Blogs

## Key Conventions

### Language
- All UI text, content, and comments are in **Japanese**
- Use Japanese for new content, descriptions, and documentation

### Styling Approach
- **Base framework**: MVP.css loaded via CDN (`https://unpkg.com/mvp.css`)
- **Markdown parser**: marked.js loaded via CDN (`https://cdn.jsdelivr.net/npm/marked/marked.min.js`)
- **Custom styles**: Defined in `<style>` block within each HTML file
- **Style theme**: Compact style with minimal spacing
  - Header margin-bottom: 10px
  - Tight spacing throughout
  - Article width: max 700px, centered

### Card Grid System
Used in index.html and Gallery/index.html:
```css
.category-grid {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(250px, 1fr));
    gap: 20px;
}
```

### Blog Post Pattern (Markdown Support)
Blog posts use Markdown for content with client-side rendering:

```html
<!DOCTYPE html>
<html lang="ja">
<head>
    <meta charset="UTF-8">
    <title>記事タイトル - ZawaaDon Homepage</title>
    <link rel="stylesheet" href="https://unpkg.com/mvp.css">
    <script src="https://cdn.jsdelivr.net/npm/marked/marked.min.js"></script>
    <style>
        /* Compact style CSS */
    </style>
</head>
<body>
    <header>
        <nav>
            <a href="../index.html">← Top</a>
            <ul>
                <li><a href="../index.html">Home</a></li>
                <li><a href="../Gallery/index.html">Gallery</a></li>
                <li><a href="../Notes/index.html">Blogs</a></li>
            </ul>
        </nav>
    </header>
    <main>
        <article>
            <h1>記事タイトル</h1>
            <div class="post-meta">📅 YYYY/MM/DD <span class="tag">タグ</span></div>
            
            <!-- Markdown content (hidden) -->
            <div id="markdown-content" style="display:none;">
## 見出し
本文をMarkdownで記述
            </div>
            
            <!-- Rendered HTML -->
            <div id="article-content"></div>
        </article>
        <hr style="margin: 30px 0;">
        <nav><a href="../Notes/index.html">← Blogs一覧に戻る</a></nav>
    </main>
    <script>
        document.addEventListener('DOMContentLoaded', function() {
            const markdownContent = document.getElementById('markdown-content').textContent;
            const htmlContent = marked.parse(markdownContent);
            document.getElementById('article-content').innerHTML = htmlContent;
        });
    </script>
</body>
</html>
```

### File Naming
- Posts: Sequential numbering `001_`, `002_`, etc. with descriptive suffix
- Keep filenames lowercase and use underscores

## Development Workflow

### Local Preview
Since this is static HTML, simply open files in a browser:
- Use Live Server extension or similar for hot reload
- Or directly open `index.html` in browser (file:// protocol)

### Deployment
- Push to `main` branch → automatically published to `https://ZawaaDon.github.io/`
- No build step required (pure HTML/CSS/JS)

### Git Commit Messages
- **Always write commit messages in English**
- Use conventional format: brief summary line + detailed description
- Example:
  ```
  Add compact style template and update documentation
  
  - Add posts/template_compact.html as new blog post template
  - Update posts/001_hello.html to compact style (minimized spacing)
  - Update .github/copilot-instructions.md with latest site structure
  ```

## Adding New Content

### New Gallery Project
1. Edit `Gallery/index.html`
2. Add new project card in `.category-grid`:
```html
<div class="category-card">
    <a href="project_details.html">
        <h3>Project Name</h3>
        <span class="status-badge status-planning">準備中</span>
        <p>Project description</p>
        <div class="project-meta">
            <span class="category-tag">カテゴリ</span>
            <span class="tech-tag">Tech1</span>
            <span class="tech-tag">Tech2</span>
        </div>
        <div class="project-links">
            <a href="https://github.com/..." target="_blank">GitHub</a>
        </div>
    </a>
</div>
```

### New Blog Post
1. Copy `posts/template_compact.html` to `posts/00X_title.html`
2. Update title, date, tags, and Markdown content
3. Add entry to `Notes/index.html` article list
4. Add to "Recent Updates" in sidebar (index.html, Gallery/index.html, Notes/index.html)

### Template Usage
Use `posts/template_compact.html` as the base template for all new blog posts. It includes:
- Compact style spacing
- Markdown support with marked.js
- Consistent navigation
- Proper styling for headings and content

## Technical Stack
- **HTML/CSS**: Pure static files
- **MVP.css**: Classless CSS framework
- **marked.js**: Client-side Markdown parser
- **GitHub Pages**: Hosting platform
- **No build process**: Files are served as-is

## Project References
- Volatile Engine: https://github.com/Yura0326/Volatile (Private repository)
- SNS Links: X (Twitter), GitHub, Qiita, YouTube
