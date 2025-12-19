# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Repository Purpose

Documents repository for Marp presentations. Currently contains `src/architecture-presentation.md` (LT on architecture fundamentals for junior developers).

## Build Commands

All generated files output to `dist/` directory (gitignored).

```bash
# Generate all formats (HTML, PDF, PowerPoint)
npm run build:all

# Individual formats
npm run build        # HTML + images sync (rsync for efficiency)
npm run build:pdf    # PDF (requires Chromium + Japanese fonts)
npm run build:pptx   # PowerPoint (requires Chromium + Japanese fonts)

# Development
npm run preview      # Live preview server at localhost:8080
```

**Important**: `npm run build` uses rsync to copy images incrementally. Only changed files are copied to `dist/images/`.

## Environment Setup

### WSL/Linux (First-time setup)
```bash
# Install Chromium browser
sudo apt-get update && sudo apt-get install -y chromium-browser

# Install Japanese fonts (critical for PDF/PPTX)
sudo apt-get install -y fonts-noto-cjk fonts-noto-cjk-extra

# Update font cache
fc-cache -fv
```

**Without Japanese fonts**: PDF/PPTX will show □ (tofu) instead of Japanese text.

### macOS/Windows
Japanese fonts pre-installed. Only need Chrome/Edge/Firefox for PDF/PPTX generation.

## File Structure

```
src/
  architecture-presentation.md  # Marp presentation source
  images/                        # Presentation images (partially gitignored)
    gemini-image-prompts.txt     # Image generation prompts (tracked)
    README.md                    # Image setup instructions (tracked)
    title-architecture.png       # Placeholder image (tracked)
    *.png                        # Other images (gitignored until added)
dist/                            # Generated files (gitignored)
  *.html, *.pdf, *.pptx
  images/                        # Copied from src/images/ during build
```

## Marp File Format

- YAML frontmatter: `marp: true`, `theme`, `paginate`, `style` (for fonts)
- Slides separated by `---`
- Images: `![bg right:40%](images/filename.png)` for background placement (relative to .md file)
- Font specification in frontmatter prevents Japanese text issues in PPTX

## Image Workflow

1. Edit prompts in `src/images/gemini-image-prompts.txt`
2. Generate images with Gemini (10 images defined)
3. Save to `src/images/` folder (overwrite placeholders)
4. Add to git: Edit `.gitignore` to unignore specific images:
   ```gitignore
   # Add this line for each new image:
   !src/images/your-new-image.png
   ```
5. Rebuild: `npm run build:all`

**Note**: Images are gitignored by default. Only `README.md`, `gemini-image-prompts.txt`, and `title-architecture.png` are tracked initially.

## Git Workflow

- Main branch: `main`
- Feature branches: `feature/[description]`
