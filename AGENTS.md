# AGENTS.md

## Project type

Static HTML site — no build system, no package manager, no framework. Pure HTML/CSS/JS.

## Target audience

Elementary school (小学) math teachers and students. All content should be appropriate for grades 1-6.

## Structure

- `index.html` — Landing page with tool cards, search, and category filtering
- `toolshtml/` — Individual tool pages (one HTML file per tool)
- `images/` — Screenshots/thumbnails for tool cards

## Conventions

- Language: Chinese (zh-CN). All UI text, labels, and comments are in Chinese.
- Icons: Font Awesome 6.5 via CDN (`cdnjs.cloudflare.com`)
- Fonts: Noto Sans SC, DM Mono via Google Fonts (commented out in tool pages)
- Each tool page is self-contained: inline CSS + inline JS, no shared dependencies between tools
- Tool cards in `index.html` reference pages via relative paths (e.g. `toolshtml/dkjsq.html`)

## Existing tools

| File | Name | Category |
|------|------|----------|
| `dkjsq.html` | 贷款计算器 | 数学 |
| `jhhb.html` | 几何画板 | 数学 |
| `hstx.html` | 函数图像 | 数学 |
| `sjdm.html` | 随机点名 | 课堂 |
| `cjtj.html` | 成绩统计 | 课堂 |
| `jssb.html` | 计时秒表 | 课堂 |
| `dwhs.html` | 单位换算 | 数学 |
| `gssc.html` | 公式手册 | 数学 |
| `xghdqy.html` | 小狗活动区域 | 数学 |

## Design system

Each tool page uses CSS variables for consistent theming. Accent color varies per tool but the pattern is identical:
- `--accent` / `--accent-glow` / `--accent-soft` / `--border` for the tool's color
- `--bg: #f5f7fa`, `--card: #fff`, `--fg: #2d3748`, `--fg-muted: #718096` for base palette
- `--radius: 14px`, `--radius-sm: 8px` for rounded corners
- Decorative radial gradient via `body::before`
- Card-based layout with subtle box shadows

## Adding a new tool

1. Create `toolshtml/<tool-id>.html` — self-contained HTML with inline `<style>` and `<script>`
2. Add a thumbnail screenshot to `images/<tool-id>.png`
3. Add an entry to the `tools` array in `index.html` with name, desc, category, url, color, icon, image, and isNew fields
4. Icons use Font Awesome classes (e.g. `fa-solid fa-calculator`)
5. Copy the CSS variable pattern from any existing tool page for style consistency

## Testing

No automated tests. Verify by opening `index.html` in a browser.
