# NUGRESS GK Website

A professional website for NUGRESS GK, providing IT solutions, technology services, and business logistics services.

## Project Structure

```
nugress/
├── public/                 # Public web files (served by web server)
│   ├── index.html         # Main homepage
│   ├── css/               # Stylesheets
│   │   └── main.css       # Main stylesheet
│   ├── js/                # JavaScript files
│   │   └── flash-detection.js
│   ├── images/            # Image assets
│   └── pages/             # Website pages (organized by section)
│       ├── about/
│       ├── services/
│       ├── products/
│       ├── contact/
│       ├── faq/
│       ├── resources/
│       ├── why/
│       └── japanese/      # Japanese language version
├── docs/                  # Documentation
├── .gitignore            # Git ignore rules
├── package.json          # Project metadata & dependencies
└── README.md             # This file
```

## Features

- **Responsive Navigation Menu** - Main site navigation with hover effects
- **Service Cards** - Showcase of three main service areas
- **Accordion Sections** - Vision, Mission, and Motto sections
- **jQuery UI Integration** - Modern interactive elements
- **Professional Layout** - Clean, organized design
- **Multi-language Support** - Japanese language version available

## Getting Started

### Requirements
- Modern web browser (Chrome, Firefox, Safari, Edge)
- Web server (Apache, Nginx, Node.js, etc.)
- No build process required for basic development

### Installation

1. Clone or download the project:
```bash
git clone <repository-url>
cd nugress
```

2. Start a local web server:
```bash
# Using Python 3
python -m http.server 8000

# Using Python 2
python -m SimpleHTTPServer 8000

# Using Node.js (if installed)
npm install -g http-server
http-server public/ -p 8000
```

3. Open your browser and navigate to:
```
http://localhost:8000
```

## File Organization

### CSS Files
- `public/css/main.css` - Main stylesheet with all layout and styling

### JavaScript Files
- `public/js/flash-detection.js` - Browser/Flash detection (legacy support)
- jQuery and jQuery UI are loaded from CDN for better performance

### Image Assets
All images should be placed in `public/images/` directory:
- `ind01.jpg` - Body background
- `ind02.jpg` - Banner background
- `ind04.jpg` - Footer background
- `ind05.jpg` - Logo
- `ind06.jpg` - Language selector
- And other supporting images...

## Development Notes

### Modern Replacements
- **Flash Content**: The Flash banner (gk.swf) is deprecated. Consider replacing with:
  - HTML5 Video
  - Carousel/Slider library
  - Static image with CSS animations
  
### Accessibility
- All images have alt text
- Semantic HTML structure
- Keyboard navigation support

### Performance Optimization
- CDN-hosted jQuery and jQuery UI
- Minified CSS for production
- Image optimization recommended
- Consider lazy loading for below-the-fold images

## Browser Support

- Chrome (latest)
- Firefox (latest)
- Safari (latest)
- Edge (latest)
- IE 11+ (with some limitations)

## Future Improvements

1. **Modernize HTML** - Convert from XHTML 1.0 Transitional to HTML5
2. **Responsive Design** - Add mobile/tablet breakpoints
3. **Performance** - Implement minification and compression
4. **SEO** - Add schema markup and meta tags
5. **Analytics** - Integrate Google Analytics or similar
6. **CMS Integration** - Consider static site generator or headless CMS
7. **Replace Flash** - Modernize banner with HTML5 alternative

## Deployment

### Static Host (Netlify, GitHub Pages, etc.)
```bash
# Simply upload the contents of public/ directory
```

### Traditional Web Server (Apache/Nginx)
1. Upload `public/` contents to web root
2. Ensure proper permissions (755 for directories, 644 for files)
3. Configure web server to serve index.html for directory requests

### Node.js Server
```bash
npm install express
node server.js
```

## License

Copyright © 2010-2024 NUGRESS GK. All rights reserved.

## Support

For questions or issues, please contact:
- Email: info@nugress.com
- Website: https://nugress.com

---

**Project organized and modernized for better maintainability and scalability.**
