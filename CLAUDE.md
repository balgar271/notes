# CLAUDE.md - AI Assistant Guide

This document provides guidance for AI assistants working with this codebase.

## Project Overview

**Digital Notebook** is a mobile-first web application that allows users to create, organize, and manage digital notebooks. It's designed as a Progressive Web App (PWA) that can be installed on iOS and Android devices.

## Repository Structure

```
notes/
├── README.md           # Main application (single HTML file with embedded CSS/JS)
├── apple-touch-icon.png  # iOS home screen icon (3.3MB PNG)
└── CLAUDE.md           # This file
```

## Tech Stack

- **Frontend**: Vanilla JavaScript (no frameworks or build tools)
- **Styling**: Embedded CSS with CSS Grid and Flexbox
- **Storage**: Browser localStorage
- **Deployment**: GitHub Pages (served directly from README.md as HTML)

## Architecture

### Application State

The app uses a simple global state object:
```javascript
const app = {
    notebooks: [],    // Array of notebook objects
    current: null,    // Currently open notebook
    view: 'library',  // Current view: 'library' | 'edit' | 'notebook' | 'toc'
    editing: {}       // Temporary state for editing cover
};
```

### Notebook Data Model

```javascript
{
    id: number,        // Unix timestamp as ID
    title: string,     // Notebook title
    color: string,     // Color key from colors object
    pages: [{          // Array of page objects
        id: number,
        data: string,  // Base64 data URL
        name: string   // Original filename
    }],
    toc: [{            // Table of contents entries
        id: number,
        title: string,
        page: number
    }]
}
```

### Key Functions

| Function | Purpose |
|----------|---------|
| `init()` | Bootstrap the application |
| `loadData()` / `saveData()` | localStorage persistence |
| `render()` | Main render dispatcher |
| `renderLibrary()` | Home view with notebook cards |
| `renderEdit()` | Cover customization view |
| `renderNotebook()` | Notebook viewer with pages |
| `renderTOC()` | Table of contents editor |
| `handleFiles()` | Process uploaded images/PDFs |

### Color Palette

The app uses a predefined pastel color palette:
- pink, purple, lavender, blue, mint, peach, lilac, sky

## Development Guidelines

### Code Style

1. **No Build Step**: All code is in a single HTML file - no transpilation or bundling
2. **ES6+ Syntax**: Use modern JavaScript features (const, let, arrow functions, template literals)
3. **DOM Manipulation**: Direct DOM updates via innerHTML and getElementById
4. **Event Handling**: Inline event handlers (`onclick`) for simplicity

### Making Changes

When modifying `README.md`:

1. **CSS Changes**: Edit the `<style>` block (lines ~37-506)
2. **JavaScript Changes**: Edit the `<script>` block (lines ~518-909)
3. **HTML Structure**: Edit the static HTML in `<body>` (minimal - most is generated)

### Testing

- **No automated tests**: Manual testing in browser required
- **Test on mobile**: Primary target is iOS Safari and Android Chrome
- **Test localStorage**: Clear localStorage between major data model changes
- **PWA testing**: Test "Add to Home Screen" functionality

### Common Tasks

**Adding a new color:**
1. Add color to the `colors` object in JavaScript
2. The UI automatically renders all colors from this object

**Adding a new view:**
1. Add view name to valid views in state
2. Create `render{ViewName}()` function
3. Add case in `render()` switch

**Modifying notebook structure:**
1. Update the data model (may require migration)
2. Update `saveData()` and `loadData()` if needed
3. Update all render functions that use the data

## PWA Configuration

The app includes:
- Apple touch icon and web app meta tags
- `manifest.json` reference (not included in repo - needs creation for full PWA)
- Mobile viewport and status bar configuration

## Known Limitations

1. **File size**: Large images stored as base64 in localStorage can hit storage limits
2. **No cloud sync**: Data is device-local only
3. **PDF handling**: PDFs are converted to images, not rendered natively
4. **No offline caching**: Service worker not implemented

## Git Workflow

- **Main branch**: Primary development branch
- **Commits**: Descriptive commit messages explaining the change
- **No CI/CD**: Direct deployment via GitHub Pages

## Important Notes for AI Assistants

1. **Single file application**: All code lives in README.md - this is intentional for GitHub Pages hosting
2. **Preserve markdown code blocks**: The CSS and JS are wrapped in markdown code fences (```) - preserve these
3. **Test locally**: Changes should be tested in a browser before committing
4. **Mobile-first**: Always consider mobile UX when making changes
5. **localStorage limits**: Be mindful of data size when adding features
6. **No external dependencies**: Keep the app self-contained with no CDN imports
