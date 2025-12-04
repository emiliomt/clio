# Clio

A minimal, lightweight personal note-taking app inspired by Obsidian. Write notes, create wiki-style links between them, and see backlinks—all in a clean, distraction-free interface.

![Clio Screenshot](https://via.placeholder.com/800x450/f5f5f5/333333?text=Clio+Note-Taking+App)

## ✨ Features

- **Plain Text Notes** - Simple, fast note-taking with no formatting distractions
- **Wiki-Style Links** - Use `[[Note Title]]` to link between notes
- **Automatic Backlinks** - See which notes link to your current note
- **Instant Search** - Filter notes by title or content in real-time
- **Auto-Save** - Your changes are saved automatically as you type
- **Zero Setup** - Single HTML file, no installation or build process required
- **Offline-First** - Works completely offline, stores data in your browser
- **Privacy-Focused** - All data stays on your device, no servers or tracking

## 🚀 Quick Start

### Desktop Usage

1. Download `clio.html` from this repository
2. Double-click the file to open it in your web browser
3. Start taking notes!

That's it. No installation, no dependencies, no configuration.

### Mobile Usage (iPhone/iPad)

1. Host the HTML file on GitHub Pages or any web server
2. Open the URL in Safari on your iPhone
3. Tap the Share button → "Add to Home Screen"
4. Launch Clio like a native app from your home screen

## 📖 How to Use

### Creating Notes

- Click **"+ New Note"** to create a new note
- Give it a title and start writing

### Linking Notes

Create connections between notes using wiki-style links:

```
I'm learning about [[JavaScript]] and [[Web Development]].

Check out my [[Project Ideas]] for inspiration.
```

- Click inside a `[[link]]` in the editor to navigate to that note
- If the linked note doesn't exist, Clio will create it automatically

### Finding Notes

- Use the **search box** at the top to filter notes by title or content
- View **backlinks** at the bottom to see which notes reference the current one

### Deleting Notes

- Click **"Delete Note"** in the editor
- Confirm the deletion when prompted

## 🛠️ Technical Details

### Built With

- Pure HTML, CSS, and vanilla JavaScript
- No frameworks, no dependencies
- Single file under 10KB

### Data Storage

- Uses browser `localStorage` for data persistence
- Notes are stored as JSON with the following structure:

```javascript
{
  id: 1234567890,
  title: "My Note",
  content: "Note content with [[wiki links]]",
  createdAt: 1234567890,
  updatedAt: 1234567890
}
```

### Browser Compatibility

Works in all modern browsers:
- Chrome/Edge 80+
- Firefox 75+
- Safari 13+
- Opera 67+

## 📱 Deployment Options

### GitHub Pages (Free)

1. Fork this repository
2. Rename `clio.html` to `index.html`
3. Go to Settings → Pages
4. Enable Pages from main branch
5. Access at `https://yourusername.github.io/clio`

### Netlify (Free)

1. Sign up at [Netlify](https://netlify.com)
2. Drag and drop `clio.html` into Netlify Drop
3. Get an instant URL like `random-name.netlify.app`

### Self-Hosting

Simply place `clio.html` on any web server and access via URL.

## ⚠️ Important Notes

### Data Persistence

- Notes are stored in browser localStorage
- Data persists between sessions
- Clearing browser data will delete your notes
- Each browser maintains its own separate database

### Backup Your Notes

Since data is stored locally:
- Regularly export your browser data
- Consider copying the HTML file to multiple locations
- Use the same browser and URL to maintain access to your notes

### Limitations

- No cloud sync (by design)
- No collaboration features
- No markdown rendering (plain text only)
- Storage limited by browser localStorage (~5-10MB)

## 🎯 Use Cases

Perfect for:
- Personal knowledge base
- Quick note-taking and idea capture
- Zettelkasten-style note systems
- Offline journaling
- Linking thoughts and concepts
- Distraction-free writing

## 🤝 Contributing

This is a simple, self-contained project. Feel free to fork and modify for your own needs!

Suggestions for improvements:
- Add export/import functionality
- Implement markdown rendering
- Add tags or categories
- Create mobile-optimized styles
- Add keyboard shortcuts

## 📄 License

MIT License - Feel free to use, modify, and distribute as you wish.

## 🙏 Inspiration

Inspired by [Obsidian](https://obsidian.md) and the concept of networked note-taking, with a focus on simplicity and zero dependencies.

---

**Made with ❤️ for simple, distraction-free note-taking**
