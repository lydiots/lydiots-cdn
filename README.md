# Lydiots CDN

A content delivery network (CDN) for hosting static assets for Lydiots projects, deployed on Netlify.

## 🌐 Live URL
[https://cdn.lydiots.com](https://cdn.lydiots.com)

## 📁 Directory Structure

```
/
├── assets/    # General static assets and resources
├── css/       # Stylesheets and CSS files  
├── js/        # JavaScript files and libraries
├── images/    # Images, icons, and graphics
├── fonts/     # Web fonts and typography assets
└── index.html # CDN directory listing and documentation
```

## 🚀 Usage

Access any asset using the following URL pattern:
```
https://cdn.lydiots.com/[folder]/[filename]
```

### Examples:
- `https://cdn.lydiots.com/css/main.css`
- `https://cdn.lydiots.com/js/app.js` 
- `https://cdn.lydiots.com/images/logo.png`
- `https://cdn.lydiots.com/fonts/custom-font.woff2`
- `https://cdn.lydiots.com/assets/data.json`

## ✨ Features

- ✅ **CORS Enabled**: Cross-origin requests allowed for all assets
- ✅ **Optimized Caching**: Smart cache headers for different asset types
- ✅ **Global CDN**: Fast delivery worldwide via Netlify's edge network
- ✅ **Custom 404**: Helpful error page for missing assets
- ✅ **Multiple Formats**: Support for all common web asset types

## 🔧 Caching Strategy

| Asset Type | Cache Duration | Notes |
|------------|----------------|--------|
| Images (jpg, png, gif, webp, svg) | 30 days | Static images with monthly refresh |
| Fonts (woff, woff2, ttf, otf) | 1 year | Immutable font files |
| CSS/JS | 30 days | With revalidation for updates |
| Assets folder | 1 year | Immutable versioned assets |

## 📦 Deployment

This CDN is automatically deployed to Netlify when changes are pushed to the main branch.

### Netlify Configuration
- **Build Command**: None (static files only)
- **Publish Directory**: `.` (root)
- **Custom Domain**: `cdn.lydiots.com`
- **Git LFS**: Fully supported for large binary assets

## 🛠️ Local Development

To test locally:

```bash
# Clone the repository (with LFS files)
git clone https://github.com/lydiots/lydiots-cdn.git
cd lydiots-cdn

# Install Git LFS if not already installed
git lfs install

# Pull LFS files (if any)
git lfs pull

# Serve locally (using any static server)
npx serve .
# or
python -m http.server 8000
```

## 📝 Adding Assets

### Regular Assets (< 100MB)
1. Place files in the appropriate directory (`css/`, `js/`, `images/`, `fonts/`, or `assets/`)
2. Commit and push to the main branch
3. Assets will be available at `https://cdn.lydiots.com/[folder]/[filename]`

### Large Assets (> 100MB or binary files)
Large files are automatically tracked by Git LFS based on `.gitattributes`:

1. **Automatic LFS tracking** for:
   - Videos (MP4, WebM, MOV, etc.)
   - Large images (PSD, AI, TIFF, etc.)
   - Audio files (MP3, WAV, FLAC, etc.)
   - Archives (ZIP, TAR, etc.)
   - Large documents (PDF, etc.)

2. **Manual LFS tracking** for specific files:
   ```bash
   git lfs track "path/to/large-file.ext"
   git add .gitattributes
   git add path/to/large-file.ext
   git commit -m "Add large asset via LFS"
   ```

## 🗂️ Git LFS Management

```bash
# Check LFS status
git lfs status

# See tracked file patterns
git lfs track

# See LFS files in repository
git lfs ls-files

# Track additional file types
git lfs track "*.extension"
```

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch
3. Add your assets to the appropriate directories
4. For large files, ensure Git LFS is installed: `git lfs install`
5. Commit with descriptive messages
6. Push and create a Pull Request

---

Powered by [Netlify](https://netlify.com) 🚀
