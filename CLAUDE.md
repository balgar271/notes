# CLAUDE.md - Digital Notebook App

## Project Overview

This repository contains a **Digital Notebook Web Application** - a progressive web app (PWA) for creating, organizing, and managing digital notebooks with custom covers, pages, and table of contents.

### Key Characteristics
- **Type**: Single-page web application (SPA)
- **Tech Stack**: Vanilla HTML, CSS, JavaScript (no frameworks/dependencies)
- **Storage**: Browser LocalStorage for data persistence
- **Platform**: Mobile-first responsive design, optimized for iOS/Android
- **Language**: Primarily English with some German labels ("Notizbuch")

## Repository Structure

```
/home/user/notes/
├── README.md              # Contains entire HTML/CSS/JS application
├── apple-touch-icon.png   # App icon (192x192+ for iOS/PWA)
└── .git/                  # Git repository metadata
```

### Important Notes
- **Single File Architecture**: The entire application is contained within `README.md` as an HTML file
- This is intentional for easy deployment to GitHub Pages or similar static hosting
- The README.md is not documentation - it IS the application itself

## Application Architecture

### State Management
The app uses a simple global state object:

```javascript
const app = {
    notebooks: [],      // Array of all notebooks
    current: null,      // Currently open notebook
    view: 'library',    // Current view: 'library', 'edit', 'notebook', 'toc'
    editing: { title: '', color: 'pink' }  // Temp data for editing
};
```

### Data Model

**Notebook Object Structure:**
```javascript
{
    id: 1234567890,           // timestamp-based unique ID
    title: "My Notebook",     // user-defined title
    color: "pink",            // color key (pink, purple, lavender, blue, mint, peach, lilac, sky)
    pages: [                  // array of page objects
        {
            id: 1234567890.123,
            data: "data:image/...",  // base64 encoded image/PDF
            name: "filename.jpg"
        }
    ],
    toc: [                    // table of contents entries
        {
            id: 1234567890,
            title: "Chapter 1",
            page: 3
        }
    ]
}
```

### Views/Screens

1. **Library** (`app.view = 'library'`)
   - Grid of notebook cards
   - Each card shows title, color, and page count
   - Create new notebook button
   - Delete notebook option (X button on cards)

2. **Edit** (`app.view = 'edit'`)
   - Customize notebook cover
   - Edit title
   - Choose from 8 pastel colors
   - Live preview of cover

3. **Notebook** (`app.view = 'notebook'`)
   - Display cover page
   - Optional table of contents page (page 2)
   - All added pages with page numbers
   - Actions: Edit Cover, Edit Index, Add Pages

4. **TOC** (`app.view = 'toc'`)
   - Manage table of contents entries
   - Add/remove entries
   - Each entry has title and page number

### Color System

Predefined pastel colors (matching academic/aesthetic theme):
```javascript
const colors = {
    pink: '#f5d7e3',
    purple: '#e8d4f0',
    lavender: '#e0d4f0',
    blue: '#d4e4f5',
    mint: '#d9ede8',
    peach: '#fce4d6',
    lilac: '#ead9f0',
    sky: '#dae8f5'
};
```

### Page Numbering Logic

- **Page 1**: Always the cover (not numbered visibly)
- **Page 2**: Table of contents (if entries exist)
- **Page 3+**: User-added pages
- Page numbers alternate left/right based on even/odd
- If no TOC exists, user pages start at page 2

## Key Functions Reference

### Core Navigation
- `init()` - App initialization, loads data and renders
- `render()` - Main render function, switches between views
- `loadData()` - Loads notebooks from localStorage
- `saveData()` - Saves notebooks to localStorage

### Library Functions (README.md:580-617)
- `renderLibrary()` - Renders notebook grid
- `createNotebook()` - Creates new notebook with defaults
- `openNotebook(id)` - Opens specific notebook
- `deleteNotebook(id)` - Deletes notebook after confirmation

### Edit/Cover Functions (README.md:619-644)
- `renderEdit()` - Renders cover editor
- `setColor(color)` - Updates preview color
- `saveCover()` - Saves cover changes to notebook
- `editNotebookCover()` - Opens cover editor for current notebook

### Notebook View Functions (README.md:647-722)
- `renderNotebook()` - Renders full notebook with all pages
- `handleFiles(e)` - Processes image/PDF uploads
- `scrollTo(pageNum)` - Smooth scrolls to specific page

### TOC Functions (README.md:724-761)
- `renderTOC()` - Renders TOC editor
- `addTOC()` - Adds new TOC entry
- `removeTOC(id)` - Removes TOC entry

## Development Guidelines for AI Assistants

### Making Changes

**DO:**
- Preserve the single-file architecture (all code in README.md)
- Maintain mobile-first responsive design principles
- Keep the pastel color aesthetic consistent
- Use vanilla JavaScript (no frameworks)
- Test localStorage operations carefully
- Maintain the existing state management pattern
- Keep functions pure and focused on single responsibility

**DON'T:**
- Split the app into multiple files unless explicitly requested
- Add external dependencies or frameworks
- Change the core data model without updating all related functions
- Break the page numbering logic
- Remove mobile optimizations or touch-friendly interactions
- Add complex build processes

### Common Modification Patterns

**Adding a new color:**
1. Add to `colors` object (README.md:527-536)
2. Color will automatically appear in picker
3. Ensure contrast with text remains readable

**Adding new page features:**
1. Extend page object in data model
2. Update `renderNotebook()` to display new features
3. Update `handleFiles()` if needed for upload
4. Save to localStorage via `saveData()`

**Adding new views:**
1. Add new view name to `app.view` logic
2. Create `render[ViewName]()` function
3. Add view to `render()` switch (README.md:565-578)
4. Create navigation functions to/from new view

### Testing Checklist

When making changes, verify:
- [ ] Data persists across page refreshes (localStorage)
- [ ] Mobile touch interactions work smoothly
- [ ] All views render correctly
- [ ] Page numbering remains consistent
- [ ] File uploads (images/PDFs) work
- [ ] TOC navigation scrolls to correct pages
- [ ] Notebook deletion removes data properly
- [ ] Color picker updates preview in real-time
- [ ] No console errors
- [ ] App works offline (after initial load)

### Browser Compatibility

Primary targets:
- iOS Safari (mobile web app capability)
- Android Chrome (PWA support)
- Modern desktop browsers (Chrome, Firefox, Safari, Edge)

Features used:
- LocalStorage (widely supported)
- FileReader API for uploads
- CSS Grid and Flexbox
- ES6 JavaScript (const, let, arrow functions, template literals)
- Touch events and -webkit-overflow-scrolling

### PWA Features

The app includes:
- Apple Touch Icons (README.md:5-11)
- Web App Manifest reference (README.md:28)
- Viewport meta tags for mobile (README.md:31)
- Apple mobile web app meta tags (README.md:21-25, 32-34)
- Theme color for Android (README.md:29)

Note: The manifest.json file is referenced but not included in the repository.

## Git Workflow

### Branch Strategy
- Development happens on feature branches with prefix: `claude/`
- Branch naming pattern: `claude/claude-md-[session-id]`
- Current branch: `claude/claude-md-miezaeo5tei7mtjw-01HTAtJ1BUoLobjMZcQzPduX`

### Commit Guidelines
- Use clear, descriptive commit messages
- Reference what was changed and why
- Examples from history:
  - "Update README with app icons and meta settings"
  - "Add files via upload"
  - "Enhance README with app icons and web app metadata"

### Push Protocol
- Always use: `git push -u origin <branch-name>`
- Branch must start with `claude/` for permissions
- Retry on network failures with exponential backoff (2s, 4s, 8s, 16s)
- Never force push to main/master

## Common Tasks for AI Assistants

### Task: Add a new feature
1. Read README.md to understand current implementation
2. Identify affected functions
3. Update data model if needed
4. Modify/add rendering functions
5. Update event handlers
6. Test in all views
7. Commit with descriptive message

### Task: Fix a bug
1. Locate the buggy code section in README.md
2. Understand the intended behavior
3. Make minimal targeted fix
4. Verify fix doesn't break other features
5. Test edge cases
6. Commit fix

### Task: Improve styling
1. Locate relevant CSS in `<style>` section (README.md:36-506)
2. Maintain pastel aesthetic and mobile-first approach
3. Test on various screen sizes
4. Ensure touch targets remain >= 44x44px
5. Verify color contrast for accessibility

### Task: Update documentation
1. Update this CLAUDE.md file
2. Keep inline code comments minimal (code is self-documenting)
3. Update function references if line numbers shift significantly

## Security Considerations

- **No server-side code**: All data stored client-side only
- **No authentication**: App is local to each browser/device
- **File upload safety**: Only accepts images and PDFs
- **XSS prevention**: User input is escaped in template literals
- **LocalStorage limits**: ~5-10MB depending on browser
- **No sensitive data**: App designed for general note-taking only

## Performance Considerations

- Single-file load keeps initial load fast
- Base64 encoding of images increases localStorage usage
- Large notebooks (many pages) may hit localStorage limits
- Re-rendering entire views on state changes (acceptable for this scale)
- No virtual scrolling (not needed for typical use cases)

## Localization

Current state:
- UI is primarily English
- Some German terms used ("Notizbuch")
- No i18n framework implemented
- Adding translations would require:
  - Creating translation object
  - Replacing hardcoded strings
  - Adding language selector

## Future Enhancement Ideas

Consider these if user requests improvements:
- Export notebooks as PDF
- Add manifest.json for full PWA capability
- Service worker for offline functionality
- Cloud sync (would require backend)
- Rich text editing for pages
- Search functionality
- Notebook categories/folders
- Dark mode theme
- Undo/redo functionality
- Page reordering (drag and drop)
- Share notebooks via link/export

## Troubleshooting Common Issues

**Issue: Data lost after clearing browser**
- Cause: LocalStorage cleared
- Solution: Add export/import functionality or cloud sync

**Issue: Can't upload large PDFs**
- Cause: LocalStorage size limit
- Solution: Implement compression or external storage

**Issue: Page numbers wrong after deleting TOC**
- Cause: Page calculation doesn't update
- Solution: Force re-render or recalculate page offsets

**Issue: App doesn't work on older browsers**
- Cause: ES6 JavaScript features
- Solution: Add transpilation step or graceful degradation

## Questions to Ask Users

When receiving vague requests, clarify:
- What view should this affect? (library, edit, notebook, toc)
- Should this data persist? (add to data model)
- Mobile or desktop focus? (or both)
- Does this replace existing functionality or add to it?
- Should old data migrate to new format?

## File Path References

When discussing code changes, use these line references:
- HTML structure: README.md:2-509
- Styles: README.md:36-506
- JavaScript: README.md:518-909
- State object: README.md:519-524
- Color definitions: README.md:527-536
- Initialization: README.md:538-543
- Data persistence: README.md:545-563
- Main render: README.md:565-578
- Library view: README.md:580-617
- Edit view: README.md:619-644
- Notebook view: README.md:647-722
- TOC view: README.md:724-761
- Event handlers: README.md:763-902

---

**Last Updated**: 2025-11-25
**App Version**: Single-file HTML app with LocalStorage
**Compatible With**: Claude Code, GitHub Copilot, Cursor AI, and similar AI coding assistants
