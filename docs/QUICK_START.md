# Quick Start Guide

## 5-Minute Setup

### 1. Install Dependencies (optional)
```bash
npm install
```

### 2. Start Local Server

**Using npm:**
```bash
npm start
```

**Using Python 3:**
```bash
cd public
python -m http.server 8000
```

**Using Python 2:**
```bash
cd public
python -m SimpleHTTPServer 8000
```

### 3. Open in Browser
```
http://localhost:8000
```

Done! 🎉

---

## Project Overview

### What You Have
- ✅ Fully organized project structure
- ✅ Modernized HTML5 homepage
- ✅ Consolidated, corrected CSS
- ✅ jQuery UI for interactive elements
- ✅ Professional documentation
- ✅ Ready for deployment

### What's Next
1. Add content to page subfolders (about, services, products, etc.)
2. Copy image assets to `public/images/`
3. Customize styles in `public/css/main.css`
4. Replace Flash banner with modern content
5. Deploy to production

---

## File Structure at a Glance

```
public/
├── index.html          ← Main homepage (OPEN THIS)
├── css/
│   └── main.css        ← Edit this for styling
├── js/
│   └── flash-detection.js
├── images/             ← Put all images here
└── pages/              ← Create subpages here
    ├── about/
    ├── services/
    ├── products/
    └── [other sections]
```

---

## Common Tasks

### Add a New Page

1. Create folder in `public/pages/` (e.g., `public/pages/services/`)
2. Create `index.html` in that folder
3. Update links in main navigation

**Template:**
```html
<!DOCTYPE html>
<html>
<head>
    <title>Page Title - NUGRESS GK</title>
    <link href="../../css/main.css" rel="stylesheet">
</head>
<body>
    <!-- Your content here -->
</body>
</html>
```

### Change Styling

Edit `public/css/main.css`:
- Colors
- Fonts
- Layout
- Spacing
- Backgrounds

### Add Images

1. Place image in `public/images/`
2. Reference in HTML: `<img src="images/filename.jpg">`
3. Reference in CSS: `background-image: url(../images/filename.jpg);`

### Add JavaScript

1. Create `.js` file in `public/js/`
2. Link in HTML: `<script src="js/filename.js"></script>`
3. Write your code

---

## Useful Resources

### Documentation
- README.md - Project overview
- docs/ORGANIZATION_GUIDE.md - How project is organized
- docs/DEPLOYMENT_GUIDE.md - How to deploy

### Technologies Used
- [jQuery Documentation](https://jquery.com)
- [jQuery UI Documentation](https://jqueryui.com)
- [CSS Reference](https://developer.mozilla.org/en-US/docs/Web/CSS)
- [HTML Reference](https://developer.mozilla.org/en-US/docs/Web/HTML)

### Tools
- [VS Code](https://code.visualstudio.com) - Code editor
- [ColorPicker](https://htmlcolorcodes.com) - Color selection
- [TinyPNG](https://tinypng.com) - Image optimization

---

## Troubleshooting

### Server won't start
```bash
# Port 8000 already in use? Try another port
python -m http.server 9000
```

### Images not showing
- Check paths are correct
- Ensure images are in `public/images/`
- Check browser console for errors (F12)

### CSS not updating
- Hard refresh: `Ctrl+Shift+R` (Windows/Linux)
- Hard refresh: `Cmd+Shift+R` (Mac)
- Clear cache and reload

### Links broken
- Check that paths use `../` to go up directories
- For links: Use relative paths like `../pages/about/`
- Test in browser console: `console.log(window.location)`

---

## Command Reference

```bash
# Start development server
npm start

# Just serve (no auto-open)
npm run serve

# Production serve (no cache)
npm run dev

# Install dependencies
npm install

# Check Node version
node --version

# Check npm version
npm --version
```

---

## Next Steps

1. **Review the files:**
   - Open `public/index.html`
   - Check `public/css/main.css`
   - Look at `README.md`

2. **Add your content:**
   - Create page subfolders
   - Copy/create images
   - Write page content

3. **Customize styling:**
   - Edit colors in CSS
   - Adjust layout
   - Update fonts

4. **Test thoroughly:**
   - Test all links
   - Test in multiple browsers
   - Mobile testing

5. **Deploy:**
   - Follow `docs/DEPLOYMENT_GUIDE.md`
   - Choose a hosting option
   - Go live!

---

## Support

Need help?

1. Check documentation files in `docs/`
2. Review inline comments in code
3. Check browser developer tools (F12)
4. Search online for specific issues
5. Contact your web host

---

**You're all set! Happy coding! 🚀**
