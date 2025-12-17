
<html lang="en">
<head>
    
<!-- Apple Touch Icon (iOS) -->
<link rel="apple-touch-icon" href="apple-touch-icon.png">

<!-- App Icons -->
<link rel="apple-touch-icon" href="apple-touch-icon.png">
    <link rel="icon" type="image/png" sizes="192x192" href="icon-192.png">
    <link rel="icon" type="image/png" sizes="512x512" href="icon-512.png">
    
<!-- iOS Web App Einstellungen -->
<meta name="apple-mobile-web-app-title" content="Notizbuch">
    
<!-- Favicon (Browser-Tab) -->
<link rel="icon" type="image/png" sizes="192x192" href="icon-192.png">
<link rel="icon" type="image/png" sizes="512x512" href="icon-512.png">

<!-- App Name im Home Screen -->
<meta name="apple-mobile-web-app-title" content="Notizbuch">

<!-- Vollbild-Modus (versteckt Safari-Leiste) -->
<meta name="apple-mobile-web-app-capable" content="yes">
<meta name="apple-mobile-web-app-status-bar-style" content="black-translucent">

<!-- Android Chrome -->
<link rel="manifest" href="manifest.json">
<meta name="theme-color" content="#e8d4f0">
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
    <meta name="apple-mobile-web-app-capable" content="yes">
    <meta name="apple-mobile-web-app-status-bar-style" content="black">
    <meta name="apple-mobile-web-app-title" content="Notebook">
    <title>Digital Notebook</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            -webkit-tap-highlight-color: transparent;
        }

```
    body {
        font-family: -apple-system, BlinkMacSystemFont, 'Helvetica Neue', 'Segoe UI', sans-serif;
        background: linear-gradient(135deg, #667eea 0%, #764ba2 50%, #f093fb 100%);
        min-height: 100vh;
        color: #2c3e50;
    }

    .hidden { display: none !important; }

    /* Header */
    .header {
        background: rgba(255, 255, 255, 0.15);
        backdrop-filter: blur(20px);
        -webkit-backdrop-filter: blur(20px);
        padding: 30px 20px;
        box-shadow: 0 4px 30px rgba(0, 0, 0, 0.1);
        border-bottom: 1px solid rgba(255, 255, 255, 0.2);
    }

    .title {
        font-size: 32px;
        font-weight: 300;
        margin-bottom: 8px;
        color: rgba(255, 255, 255, 0.95);
        letter-spacing: -0.5px;
    }

    .subtitle {
        font-size: 14px;
        color: rgba(255, 255, 255, 0.7);
        font-weight: 300;
        margin-bottom: 20px;
    }

    .btn {
        background: rgba(255, 255, 255, 0.25);
        backdrop-filter: blur(10px);
        -webkit-backdrop-filter: blur(10px);
        color: white;
        border: 1px solid rgba(255, 255, 255, 0.3);
        border-radius: 12px;
        padding: 14px 24px;
        font-size: 15px;
        width: 100%;
        cursor: pointer;
        font-weight: 500;
        box-shadow: 0 4px 15px rgba(0, 0, 0, 0.1);
        transition: all 0.3s ease;
    }

    .btn:active {
        transform: translateY(1px);
        box-shadow: 0 2px 8px rgba(0, 0, 0, 0.1);
    }

    /* Grid */
    .grid {
        padding: 25px 20px;
        display: grid;
        grid-template-columns: repeat(2, 1fr);
        gap: 18px;
    }

    .card {
        background: rgba(255, 255, 255, 0.2);
        backdrop-filter: blur(15px);
        -webkit-backdrop-filter: blur(15px);
        border: 1px solid rgba(255, 255, 255, 0.25);
        border-radius: 16px;
        overflow: hidden;
        box-shadow: 0 8px 32px rgba(0, 0, 0, 0.1);
        transition: all 0.3s ease;
    }

    .card:active {
        transform: translateY(-2px);
        box-shadow: 0 8px 30px rgba(0, 0, 0, 0.12);
    }

    .card-cover {
        height: 200px;
        display: flex;
        align-items: center;
        justify-content: center;
        padding: 25px;
        position: relative;
    }

    .card-title {
        color: rgba(90, 74, 111, 0.95);
        font-size: 17px;
        font-weight: 400;
        text-align: center;
        word-break: break-word;
        line-height: 1.5;
        text-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
    }

    .delete-x {
        position: absolute;
        top: 12px;
        right: 12px;
        background: rgba(255, 255, 255, 0.5);
        backdrop-filter: blur(10px);
        border: none;
        color: #5a4a6f;
        width: 32px;
        height: 32px;
        border-radius: 16px;
        font-size: 18px;
        cursor: pointer;
        font-weight: 300;
        transition: all 0.2s ease;
    }

    .card-info {
        padding: 16px;
        background: rgba(255, 255, 255, 0.1);
        backdrop-filter: blur(10px);
        -webkit-backdrop-filter: blur(10px);
    }

    .card-info-title {
        font-size: 13px;
        color: rgba(255, 255, 255, 0.9);
        margin-bottom: 6px;
        font-weight: 500;
    }

    .card-info-meta {
        font-size: 11px;
        color: rgba(255, 255, 255, 0.6);
        font-weight: 400;
    }

    /* Navigation */
    .nav {
        background: rgba(255, 255, 255, 0.15);
        backdrop-filter: blur(20px);
        -webkit-backdrop-filter: blur(20px);
        padding: 20px;
        border-bottom: 1px solid rgba(255, 255, 255, 0.2);
        display: flex;
        align-items: center;
        gap: 15px;
        box-shadow: 0 4px 30px rgba(0, 0, 0, 0.1);
    }

    .back {
        background: rgba(255, 255, 255, 0.2);
        backdrop-filter: blur(10px);
        -webkit-backdrop-filter: blur(10px);
        border: 1px solid rgba(255, 255, 255, 0.25);
        width: 40px;
        height: 40px;
        border-radius: 20px;
        font-size: 20px;
        cursor: pointer;
        color: white;
        font-weight: 300;
        box-shadow: 0 2px 8px rgba(0, 0, 0, 0.1);
    }

    .nav-title {
        font-size: 22px;
        font-weight: 400;
        color: rgba(255, 255, 255, 0.95);
        letter-spacing: -0.3px;
    }

    /* Content */
    .content {
        padding: 25px 20px;
    }

    .preview {
        width: 100%;
        height: 420px;
        border-radius: 16px;
        display: flex;
        align-items: center;
        justify-content: center;
        margin-bottom: 25px;
        padding: 35px;
        box-shadow: 0 8px 30px rgba(0, 0, 0, 0.12);
    }

    .preview-text {
        color: rgba(90, 74, 111, 0.95);
        font-size: 28px;
        font-weight: 300;
        text-align: center;
        word-break: break-word;
        line-height: 1.4;
        text-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
    }

    .label {
        font-size: 13px;
        font-weight: 500;
        margin-bottom: 10px;
        display: block;
        color: rgba(255, 255, 255, 0.9);
        text-transform: uppercase;
        letter-spacing: 0.5px;
    }

    .input {
        width: 100%;
        padding: 14px 16px;
        border: 1px solid rgba(255, 255, 255, 0.25);
        border-radius: 12px;
        font-size: 15px;
        margin-bottom: 25px;
        background: rgba(255, 255, 255, 0.15);
        backdrop-filter: blur(10px);
        -webkit-backdrop-filter: blur(10px);
        color: white;
        box-shadow: 0 4px 15px rgba(0, 0, 0, 0.1);
        transition: all 0.3s ease;
    }

    .input::placeholder {
        color: rgba(255, 255, 255, 0.5);
    }

    .input:focus {
        outline: none;
        border-color: rgba(255, 255, 255, 0.4);
        box-shadow: 0 4px 20px rgba(0, 0, 0, 0.15);
        background: rgba(255, 255, 255, 0.2);
    }

    .colors {
        display: grid;
        grid-template-columns: repeat(4, 1fr);
        gap: 12px;
        margin-bottom: 25px;
    }

    .color {
        aspect-ratio: 1;
        border-radius: 12px;
        border: 3px solid transparent;
        cursor: pointer;
        box-shadow: 0 4px 12px rgba(0, 0, 0, 0.1);
        transition: all 0.3s ease;
    }

    .color:active {
        transform: scale(0.95);
    }

    .color.active {
        border-color: #9b7ab8;
        box-shadow: 0 6px 20px rgba(0, 0, 0, 0.2), 0 0 0 4px rgba(155, 122, 184, 0.2);
        transform: scale(1.05);
    }

    /* Action Buttons */
    .actions {
        display: flex;
        gap: 10px;
        overflow-x: auto;
        padding: 0 20px 20px;
        background: rgba(255, 255, 255, 0.05);
        backdrop-filter: blur(10px);
        -webkit-backdrop-filter: blur(10px);
        -webkit-overflow-scrolling: touch;
    }

    .action-btn {
        background: rgba(255, 255, 255, 0.15);
        backdrop-filter: blur(10px);
        -webkit-backdrop-filter: blur(10px);
        border: 1px solid rgba(255, 255, 255, 0.25);
        border-radius: 10px;
        padding: 10px 16px;
        font-size: 13px;
        white-space: nowrap;
        cursor: pointer;
        color: white;
        font-weight: 500;
        box-shadow: 0 2px 8px rgba(0, 0, 0, 0.1);
        transition: all 0.2s ease;
    }

    .action-btn.primary {
        background: rgba(255, 255, 255, 0.25);
        border: 1px solid rgba(255, 255, 255, 0.35);
    }

    /* Pages */
    .pages {
        padding: 25px 20px;
    }

    .page {
        background: rgba(255, 255, 255, 0.2);
        backdrop-filter: blur(15px);
        -webkit-backdrop-filter: blur(15px);
        width: 100%;
        aspect-ratio: 0.707;
        margin-bottom: 25px;
        border-radius: 12px;
        box-shadow: 0 8px 32px rgba(0, 0, 0, 0.15);
        position: relative;
        overflow: hidden;
        border: 1px solid rgba(255, 255, 255, 0.25);
    }

    .page-num {
        position: absolute;
        top: 16px;
        font-size: 11px;
        color: rgba(255, 255, 255, 0.7);
        z-index: 10;
        font-weight: 400;
        letter-spacing: 0.5px;
    }

    .page-num.left { left: 16px; }
    .page-num.right { right: 16px; }

    .cover {
        display: flex;
        align-items: center;
        justify-content: center;
        height: 100%;
        padding: 45px;
    }

    .cover-title {
        color: rgba(90, 74, 111, 0.95);
        font-size: 36px;
        font-weight: 300;
        text-align: center;
        line-height: 1.3;
        text-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
    }

    /* TOC */
    .toc {
        padding: 45px 30px;
        background: rgba(255, 255, 255, 0.1);
        backdrop-filter: blur(10px);
        -webkit-backdrop-filter: blur(10px);
    }

    .toc-title {
        font-size: 32px;
        font-weight: 300;
        text-align: center;
        margin-bottom: 35px;
        color: rgba(255, 255, 255, 0.95);
        letter-spacing: -0.5px;
    }

    .toc-item {
        display: flex;
        justify-content: space-between;
        padding: 14px 0;
        border-bottom: 1px solid rgba(255, 255, 255, 0.2);
        cursor: pointer;
        font-size: 14px;
        transition: all 0.2s ease;
    }

    .toc-item:active {
        background: rgba(255, 255, 255, 0.15);
        padding-left: 8px;
        padding-right: 8px;
        border-radius: 8px;
    }

    .toc-item-title {
        color: rgba(255, 255, 255, 0.9);
        font-weight: 400;
    }

    .toc-item-page {
        color: rgba(255, 255, 255, 0.95);
        font-weight: 500;
    }

    /* PDF */
    .pdf-content {
        width: 100%;
        height: 100%;
        display: flex;
        align-items: center;
        justify-content: center;
        padding: 25px;
        background: rgba(255, 255, 255, 0.1);
        backdrop-filter: blur(10px);
        -webkit-backdrop-filter: blur(10px);
    }

    .pdf-img {
        max-width: 100%;
        max-height: 100%;
        object-fit: contain;
        border-radius: 4px;
    }

    /* Empty State */
    .empty {
        text-align: center;
        padding: 70px 30px;
        color: rgba(255, 255, 255, 0.8);
    }

    .empty-icon {
        font-size: 56px;
        margin-bottom: 18px;
        opacity: 0.6;
    }

    .empty-text {
        font-size: 15px;
        line-height: 1.6;
        font-weight: 300;
        color: rgba(255, 255, 255, 0.8);
    }

    /* Sections */
    .section {
        background: rgba(255, 255, 255, 0.15);
        backdrop-filter: blur(15px);
        -webkit-backdrop-filter: blur(15px);
        border-radius: 16px;
        padding: 25px;
        margin-bottom: 20px;
        box-shadow: 0 8px 32px rgba(0, 0, 0, 0.1);
        border: 1px solid rgba(255, 255, 255, 0.25);
    }

    .section-title {
        font-size: 17px;
        font-weight: 500;
        margin-bottom: 18px;
        color: rgba(255, 255, 255, 0.95);
    }

    .row {
        display: flex;
        gap: 12px;
        margin-bottom: 15px;
    }

    .row input:first-child { flex: 1; }
    .row input:last-child { width: 80px; }

    .entry {
        display: flex;
        justify-content: space-between;
        align-items: center;
        padding: 14px 16px;
        background: rgba(255, 255, 255, 0.1);
        backdrop-filter: blur(10px);
        -webkit-backdrop-filter: blur(10px);
        border-radius: 12px;
        margin-bottom: 12px;
        font-size: 14px;
        border: 1px solid rgba(255, 255, 255, 0.2);
    }

    .entry-text {
        color: rgba(255, 255, 255, 0.9);
        font-weight: 400;
    }

    .del-btn {
        background: rgba(255, 90, 120, 0.8);
        backdrop-filter: blur(10px);
        -webkit-backdrop-filter: blur(10px);
        color: white;
        border: 1px solid rgba(255, 255, 255, 0.3);
        width: 34px;
        height: 34px;
        border-radius: 17px;
        cursor: pointer;
        font-size: 16px;
        font-weight: 300;
        box-shadow: 0 4px 12px rgba(255, 90, 120, 0.3);
        transition: all 0.2s ease;
    }

    .msg {
        text-align: center;
        padding: 18px;
        color: rgba(255, 255, 255, 0.9);
        font-weight: 400;
        font-size: 14px;
    }

    @media (max-width: 400px) {
        .grid { grid-template-columns: 1fr; }
    }
</style>
```

</head>
<body>
    <div id="app">
        <div class="header">
            <div class="title">Loading...</div>
        </div>
    </div>

```
<script>
    const app = {
        notebooks: [],
        current: null,
        view: 'library',
        editing: { title: '', color: 'pink' }
    };

    // Pastel colors matching the academic schedule
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

    function init() {
        console.log('App starting...');
        loadData();
        render();
        console.log('App ready!');
    }

    function loadData() {
        try {
            const saved = localStorage.getItem('notebooks');
            if (saved) {
                app.notebooks = JSON.parse(saved);
                console.log('Loaded:', app.notebooks.length);
            }
        } catch (e) {
            console.error('Load error:', e);
        }
    }

    function saveData() {
        try {
            localStorage.setItem('notebooks', JSON.stringify(app.notebooks));
        } catch (e) {
            console.error('Save error:', e);
        }
    }

    function render() {
        const container = document.getElementById('app');
        
        if (app.view === 'library') {
            container.innerHTML = renderLibrary();
        } else if (app.view === 'edit') {
            container.innerHTML = renderEdit();
            attachEditEvents();
        } else if (app.view === 'notebook') {
            container.innerHTML = renderNotebook();
        } else if (app.view === 'toc') {
            container.innerHTML = renderTOC();
        }
    }

    function renderLibrary() {
        let cards = '';
        
        for (let nb of app.notebooks) {
            const pages = (nb.pages || []).length;
            const bgColor = colors[nb.color] || colors.pink;
            cards += `
                <div class="card" onclick="openNotebook(${nb.id})">
                    <div class="card-cover" style="background: ${bgColor};">
                        <div class="card-title">${nb.title}</div>
                        <button class="delete-x" onclick="event.stopPropagation(); deleteNotebook(${nb.id})">×</button>
                    </div>
                    <div class="card-info">
                        <div class="card-info-title">${nb.title}</div>
                        <div class="card-info-meta">${pages} ${pages === 1 ? 'page' : 'pages'}</div>
                    </div>
                </div>
            `;
        }

        if (!cards) {
            cards = `
                <div style="grid-column: 1/-1;" class="empty">
                    <div class="empty-icon">📚</div>
                    <p class="empty-text">No notebooks yet<br>Create your first one to get started</p>
                </div>
            `;
        }

        return `
            <div class="header">
                <div class="title">My Notebooks</div>
                <div class="subtitle">Organize your notes beautifully</div>
                <button class="btn" onclick="createNotebook()">+ New Notebook</button>
            </div>
            <div class="grid">${cards}</div>
        `;
    }

    function renderEdit() {
        const bgColor = colors[app.editing.color] || colors.pink;
        
        let colorBtns = '';
        for (let name in colors) {
            const c = colors[name];
            const active = name === app.editing.color ? 'active' : '';
            colorBtns += `<div class="color ${active}" style="background: ${c};" onclick="setColor('${name}')"></div>`;
        }

        return `
            <div class="nav">
                <button class="back" onclick="backToLibrary()">←</button>
                <div class="nav-title">Customize Cover</div>
            </div>
            <div class="content">
                <div class="preview" id="preview" style="background: ${bgColor};">
                    <div class="preview-text" id="previewText">${app.editing.title || 'Untitled Notebook'}</div>
                </div>
                <label class="label">Notebook Title</label>
                <input type="text" class="input" id="titleInput" value="${app.editing.title}" placeholder="Enter your notebook title">
                <label class="label">Cover Color</label>
                <div class="colors">${colorBtns}</div>
                <button class="btn" onclick="saveCover()">Save and Continue</button>
            </div>
        `;
    }

    function renderNotebook() {
        const nb = app.current;
        const hasToc = (nb.toc || []).length > 0;
        const start = hasToc ? 3 : 2;
        const bgColor = colors[nb.color] || colors.pink;

        let pages = `
            <div class="page">
                <div class="cover" style="background: ${bgColor};">
                    <div class="cover-title">${nb.title}</div>
                </div>
            </div>
        `;

        if (hasToc) {
            let items = '';
            for (let t of nb.toc) {
                items += `
                    <div class="toc-item" onclick="scrollTo(${t.page})">
                        <span class="toc-item-title">${t.title}</span>
                        <span class="toc-item-page">${t.page}</span>
                    </div>
                `;
            }

            pages += `
                <div class="page" id="page2">
                    <div class="page-num right">2</div>
                    <div class="toc">
                        <div class="toc-title">Contents</div>
                        ${items}
                    </div>
                </div>
            `;
        }

        const pgs = nb.pages || [];
        for (let i = 0; i < pgs.length; i++) {
            const num = start + i;
            const side = num % 2 === 0 ? 'right' : 'left';
            pages += `
                <div class="page" id="page${num}">
                    <div class="page-num ${side}">${num}</div>
                    <div class="pdf-content">
                        <img src="${pgs[i].data}" class="pdf-img" alt="Page ${num}">
                    </div>
                </div>
            `;
        }

        if (pgs.length === 0 && !hasToc) {
            pages += `
                <div class="empty">
                    <div class="empty-icon">📄</div>
                    <p class="empty-text">No pages yet<br>Add images or PDF files to begin</p>
                </div>
            `;
        }

        return `
            <div class="nav">
                <button class="back" onclick="backToLibrary()">🏠</button>
                <div class="nav-title">${nb.title}</div>
            </div>
            <div class="actions">
                <button class="action-btn" onclick="editNotebookCover()">Edit Cover</button>
                <button class="action-btn" onclick="editTOC()">Edit Index</button>
                <button class="action-btn primary" onclick="document.getElementById('file').click()">+ Add Pages</button>
            </div>
            <div class="pages" id="pagesContainer">
                ${pages}
                <div id="loading" class="msg hidden">Processing...</div>
            </div>
            <input type="file" id="file" accept="image/*,application/pdf" multiple style="display:none" onchange="handleFiles(event)">
        `;
    }

    function renderTOC() {
        const entries = app.current.toc || [];
        
        let list = '';
        for (let e of entries) {
            list += `
                <div class="entry">
                    <span class="entry-text">${e.title} - Page ${e.page}</span>
                    <button class="del-btn" onclick="removeTOC(${e.id})">×</button>
                </div>
            `;
        }

        if (!list) {
            list = '<div class="empty"><p class="empty-text">No entries yet</p></div>';
        }

        return `
            <div class="nav">
                <button class="back" onclick="backToNotebook()">←</button>
                <div class="nav-title">Edit Index</div>
            </div>
            <div class="content">
                <div class="section">
                    <div class="section-title">Add New Entry</div>
                    <div class="row">
                        <input type="text" class="input" id="tocTitle" placeholder="Topic title" style="margin:0">
                        <input type="number" class="input" id="tocPage" placeholder="Page" style="margin:0">
                    </div>
                    <button class="btn" onclick="addTOC()">Add Entry</button>
                </div>
                <div class="section">
                    <div class="section-title">Current Entries</div>
                    ${list}
                </div>
            </div>
        `;
    }

    function attachEditEvents() {
        const input = document.getElementById('titleInput');
        if (input) {
            input.oninput = function() {
                app.editing.title = this.value;
                document.getElementById('previewText').textContent = this.value || 'Untitled Notebook';
            };
        }
    }

    function createNotebook() {
        const nb = {
            id: Date.now(),
            title: 'Untitled Notebook',
            color: 'pink',
            pages: [],
            toc: []
        };
        app.notebooks.push(nb);
        app.current = nb;
        app.editing = { title: nb.title, color: nb.color };
        app.view = 'edit';
        saveData();
        render();
    }

    function openNotebook(id) {
        app.current = app.notebooks.find(n => n.id === id);
        app.view = 'notebook';
        render();
    }

    function deleteNotebook(id) {
        if (confirm('Delete this notebook?')) {
            app.notebooks = app.notebooks.filter(n => n.id !== id);
            saveData();
            render();
        }
    }

    function backToLibrary() {
        app.view = 'library';
        render();
    }

    function setColor(color) {
        app.editing.color = color;
        const c = colors[color];
        document.getElementById('preview').style.background = c;
        document.querySelectorAll('.color').forEach(el => el.classList.remove('active'));
        event.target.classList.add('active');
    }

    function saveCover() {
        app.current.title = app.editing.title || 'Untitled Notebook';
        app.current.color = app.editing.color;
        app.notebooks = app.notebooks.map(n => n.id === app.current.id ? app.current : n);
        saveData();
        app.view = 'notebook';
        render();
    }

    function editNotebookCover() {
        app.editing = { title: app.current.title, color: app.current.color };
        app.view = 'edit';
        render();
    }

    function backToNotebook() {
        app.view = 'notebook';
        render();
    }

    function editTOC() {
        app.view = 'toc';
        render();
    }

    function addTOC() {
        const title = document.getElementById('tocTitle').value.trim();
        const page = document.getElementById('tocPage').value.trim();
        
        if (!title || !page) {
            alert('Enter both title and page');
            return;
        }

        if (!app.current.toc) app.current.toc = [];
        app.current.toc.push({
            id: Date.now(),
            title: title,
            page: parseInt(page)
        });

        app.notebooks = app.notebooks.map(n => n.id === app.current.id ? app.current : n);
        saveData();
        render();
    }

    function removeTOC(id) {
        app.current.toc = app.current.toc.filter(t => t.id !== id);
        app.notebooks = app.notebooks.map(n => n.id === app.current.id ? app.current : n);
        saveData();
        render();
    }

    function scrollTo(pageNum) {
        const el = document.getElementById('page' + pageNum);
        if (el) el.scrollIntoView({ behavior: 'smooth' });
    }

    async function handleFiles(e) {
        const files = Array.from(e.target.files);
        const loading = document.getElementById('loading');
        if (loading) loading.classList.remove('hidden');

        for (let file of files) {
            try {
                const reader = new FileReader();
                reader.onload = function(event) {
                    if (!app.current.pages) app.current.pages = [];
                    app.current.pages.push({
                        id: Date.now() + Math.random(),
                        data: event.target.result,
                        name: file.name
                    });
                    app.notebooks = app.notebooks.map(n => n.id === app.current.id ? app.current : n);
                    saveData();
                    render();
                };
                reader.readAsDataURL(file);
            } catch (err) {
                console.error('File error:', err);
                alert('Error: ' + err.message);
            }
        }

        if (loading) loading.classList.add('hidden');
        e.target.value = '';
    }

    if (document.readyState === 'loading') {
        document.addEventListener('DOMContentLoaded', init);
    } else {
        init();
    }
</script>
```

</body>
</html>
