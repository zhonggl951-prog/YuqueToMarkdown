<div align="center">

# YuqueToMarkdown

**Convert Yuque .lakebook archives into organized Markdown packages with folder hierarchy and local images**

<!-- badges -->
<p align="center">
  <a href="https://github.com/zhonggl951-prog/YuqueToMarkdown/releases"><img src="https://img.shields.io/github/v/release/zhonggl951-prog/YuqueToMarkdown?style=flat-square&color=blue" alt="Release"></a>
  <a href="https://github.com/zhonggl951-prog/YuqueToMarkdown/actions/workflows/validate.yml"><img src="https://img.shields.io/github/actions/workflow/status/zhonggl951-prog/YuqueToMarkdown/validate.yml?branch=main&style=flat-square" alt="Build Status"></a>
  <a href="https://github.com/zhonggl951-prog/YuqueToMarkdown"><img src="https://img.shields.io/github/stars/zhonggl951-prog/YuqueToMarkdown?style=flat-square&logo=github" alt="Stars"></a>
  <a href="https://github.com/zhonggl951-prog/YuqueToMarkdown/blob/main/LICENSE"><img src="https://img.shields.io/badge/license-MIT-yellow.svg?style=flat-square" alt="License"></a>
  <a href="https://github.com/zhonggl951-prog/YuqueToMarkdown/pulls"><img src="https://img.shields.io/badge/PRs-welcome-brightgreen.svg?style=flat-square" alt="PRs Welcome"></a>
  <img src="https://img.shields.io/badge/platform-browser--only-blue.svg?style=flat-square" alt="Platform">
  <a href="https://zhonggl951-prog.github.io/YuqueToMarkdown/"><img src="https://img.shields.io/badge/online%20demo-GitHub%20Pages-success?style=flat-square" alt="Live Demo"></a>
</p>

<!-- language switcher -->
<p align="center">
  <strong>English</strong> | <a href="README_zh-CN.md">简体中文</a>
</p>

</div>

---

`YuqueToMarkdown` is a lightweight, zero-build, client-side tool that converts Yuque knowledge base exports (`.lakebook` / `.tar`) into structured Markdown packages. It runs entirely inside your web browser without requiring Node.js or Python installations. The tool preserves multi-level folder hierarchies, downloads remote images locally into an `assets/` directory with depth-aware relative paths, and generates MOC index cards for seamless migration to Obsidian, Logseq, and Notion.

<p align="center">
  <img src="assets/preview.svg" alt="YuqueToMarkdown Preview" width="100%">
</p>

## Features

- **Multi-Level Directory Hierarchy**: Recursively parses Yuque's table of contents (`tocYml`) to recreate nested folder trees instead of flattening all documents into a single directory.
- **Offline Asset Localization**: Concurrently downloads remote images into an `assets/` folder and rewrites image markdown links into depth-aware relative paths (e.g., `../../assets/image.png`), preventing broken links and anti-hotlinking blocks.
- **MOC Navigation Cards**: Automatically generates `_index.md` files for directories with subdocuments, embedding internal wikilinks for topological graph navigation in Obsidian.
- **Duplicate Name Protection**: Automatically appends numeric indices to documents with identical titles or unnamed files, preventing unintentional file overwrites.
- **Code Highlighting & GFM Tables**: Preserves language identifiers in code blocks (R, Python, Bash, JSON) and converts table elements into GitHub Flavored Markdown (GFM) tables.
- **Privacy-First & Zero Uploads**: Runs 100% locally in the browser via client-side JavaScript and Web Workers. No personal data or document content is ever sent to an external server.

## Usage

### Option 1: Online Web App (Recommended)
Visit the hosted GitHub Pages application:  
👉 **[zhonggl951-prog.github.io/YuqueToMarkdown](https://zhonggl951-prog.github.io/YuqueToMarkdown/)**

Drag and drop your exported `.lakebook` or `.tar` file into the dashed box. Once processing finishes, a structured `.zip` archive will be generated and automatically downloaded.

### Option 2: Local Offline Execution
Clone the repository and open `index.html` directly in any modern browser:
```bash
git clone https://github.com/zhonggl951-prog/YuqueToMarkdown.git
cd YuqueToMarkdown
open index.html # On Windows: double-click index.html
```

## Options

The tool provides three configurable toggles (enabled by default):

| Option | Default | Description |
| :--- | :--- | :--- |
| **Download Images to assets/** | `Enabled` | Fetches remote images concurrently and rewrites links to local relative paths |
| **Directory Index (_index.md)** | `Enabled` | Creates MOC index notes with internal wikilinks for folders containing child pages |
| **YAML Frontmatter** | `Enabled` | Adds YAML metadata blocks (title, created time) to the top of each Markdown file |

## Project Structure

```
YuqueToMarkdown/
├── index.html                # Single-page client-side application (Tailwind CSS + Vanilla JS)
├── assets/
│   └── preview.svg           # High-resolution vector preview graphic
├── .github/
│   └── workflows/
│       └── validate.yml      # GitHub Actions validation workflow
├── CONTRIBUTING.md           # Contribution guidelines
├── LICENSE                   # MIT License
├── README.md                 # English documentation (default)
└── README_zh-CN.md           # Chinese documentation (Simplified Chinese)
```

## Dependencies

- [Turndown](https://github.com/mixmark-io/turndown) - HTML to Markdown converter
- [turndown-plugin-gfm](https://github.com/laurent22/turndown-plugin-gfm) - GFM table plugin for Turndown
- [js-untar](https://github.com/antelle/js-untar) - In-browser TAR extraction
- [js-yaml](https://github.com/nodeca/js-yaml) - In-browser YAML parser
- [JSZip](https://github.com/Stuk/jszip) - Client-side ZIP compression
- [FileSaver.js](https://github.com/eligrey/FileSaver.js/) - HTML5 saveAs implementation

## License

[MIT License](LICENSE)
