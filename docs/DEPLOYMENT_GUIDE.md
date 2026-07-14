# Deployment Guide

## Overview

This guide covers various deployment options for the NUGRESS GK website.

## Option 1: Static Host (Recommended for beginners)

### Netlify Deployment
1. Create a Netlify account at https://netlify.com
2. Connect your Git repository
3. Set build settings:
   - Build command: (leave empty)
   - Publish directory: `public`
4. Deploy!

### GitHub Pages
1. Push your code to GitHub
2. Go to repository Settings → Pages
3. Select branch and folder (usually `main` and `/docs` or `/public`)
4. Wait for deployment

### Vercel
1. Create account at https://vercel.com
2. Import project
3. Configure to serve from `public` directory
4. Deploy

## Option 2: Traditional Web Server

### Apache

Create `.htaccess` in `public/` directory:
```apache
<IfModule mod_rewrite.c>
    RewriteEngine On
    RewriteBase /
    
    # Serve index.html for directory requests
    DirectoryIndex index.html
    
    # Handle directory requests
    RewriteCond %{REQUEST_FILENAME} !-f
    RewriteCond %{REQUEST_FILENAME} !-d
    RewriteRule ^(.*)$ index.html [L]
</IfModule>

# Gzip compression
<IfModule mod_deflate.c>
    AddOutputFilterByType DEFLATE text/html text/plain text/xml text/css text/javascript application/javascript
</IfModule>

# Browser caching
<IfModule mod_expires.c>
    ExpiresActive On
    ExpiresByType image/jpeg "access 1 year"
    ExpiresByType image/gif "access 1 year"
    ExpiresByType image/png "access 1 year"
    ExpiresByType text/css "access 1 month"
    ExpiresByType text/javascript "access 1 month"
    ExpiresByType application/javascript "access 1 month"
</IfModule>
```

Upload steps:
1. Connect via FTP/SFTP
2. Upload all files from `public/` to web root
3. Set permissions: `chmod 755` for directories, `chmod 644` for files
4. Verify: Navigate to your domain

### Nginx

In your Nginx configuration:
```nginx
server {
    listen 80;
    server_name example.com;
    
    root /var/www/nugress/public;
    index index.html;
    
    # Gzip compression
    gzip on;
    gzip_types text/html text/css text/javascript application/javascript;
    
    # Browser caching
    location ~* \.(jpg|jpeg|png|gif|ico|css|js)$ {
        expires 365d;
        add_header Cache-Control "public, immutable";
    }
    
    # Directory requests
    location / {
        try_files $uri $uri/ =404;
    }
}
```

Reload Nginx:
```bash
sudo nginx -t
sudo systemctl reload nginx
```

## Option 3: Node.js Server

### Using Express

Create `server.js`:
```javascript
const express = require('express');
const path = require('path');
const app = express();

const PORT = process.env.PORT || 3000;

// Serve static files
app.use(express.static(path.join(__dirname, 'public')));

// Fallback to index.html
app.get('*', (req, res) => {
    res.sendFile(path.join(__dirname, 'public', 'index.html'));
});

app.listen(PORT, () => {
    console.log(`Server running at http://localhost:${PORT}`);
});
```

Install and run:
```bash
npm install express
node server.js
```

### Docker Deployment

Create `Dockerfile`:
```dockerfile
FROM node:16-alpine

WORKDIR /app

COPY package*.json ./
RUN npm install --production

COPY . .

EXPOSE 3000

CMD ["node", "server.js"]
```

Build and run:
```bash
docker build -t nugress-gk .
docker run -p 3000:3000 nugress-gk
```

## Option 4: Cloud Platforms

### AWS S3 + CloudFront
1. Create S3 bucket
2. Upload `public/` contents
3. Enable static website hosting
4. Create CloudFront distribution
5. Point domain via Route 53

### Google Cloud Storage
1. Create bucket
2. Upload files with public access
3. Configure CORS if needed
4. Use Cloud CDN for distribution

### Microsoft Azure
1. Create storage account
2. Upload to blob storage
3. Configure static site hosting
4. Set up Azure CDN

## Performance Optimization Before Deployment

### 1. Minify CSS
```bash
npm install -g cssnano
cssnano public/css/main.css > public/css/main.min.css
```

Update `index.html`:
```html
<link href="css/main.min.css" rel="stylesheet">
```

### 2. Optimize Images
```bash
# Using ImageMagick
convert image.jpg -quality 85 -resize 1920x1080 optimized.jpg

# Using ImageOptim (Mac)
# Using TinyPNG online
```

### 3. Add Compression Headers
Ensure server sends:
- `Content-Encoding: gzip`
- Proper `Cache-Control` headers
- `ETag` headers

### 4. Test Performance
- Use Google PageSpeed Insights
- Use GTmetrix
- Use WebPageTest

## SSL/HTTPS Setup

### Let's Encrypt (Free)

```bash
# Using Certbot with Apache
sudo apt-get install certbot python3-certbot-apache
sudo certbot --apache -d example.com

# Using Certbot with Nginx
sudo certbot --nginx -d example.com
```

### Manual SSL
1. Generate key and certificate
2. Upload to server
3. Configure web server to use SSL
4. Enable redirect from HTTP to HTTPS

## Domain Configuration

### DNS Records (for example.com)

```
Type    Name        Value
A       @           your.ip.address
A       www         your.ip.address
CNAME   www         example.com
```

## Monitoring & Maintenance

### Monitoring
- Set up uptime monitoring (Pingdom, Uptime Robot)
- Configure error logging
- Monitor traffic with Google Analytics

### Regular Tasks
- Update dependencies monthly
- Check for broken links quarterly
- Review analytics monthly
- Backup files quarterly

## Troubleshooting

### 404 Errors on Direct URLs
Solution: Configure server to serve `index.html` for all routes

### Images Not Loading
- Check file permissions
- Verify image paths in HTML/CSS
- Ensure images are in `public/images/`

### Slow Performance
- Minify CSS/JS
- Optimize images
- Enable gzip compression
- Use CDN for assets

### Browser Compatibility Issues
- Test in multiple browsers
- Use polyfills if needed
- Check browser console for errors

## Checklist Before Going Live

- [ ] All images uploaded to `public/images/`
- [ ] All links tested and working
- [ ] CSS and JS optimized/minified
- [ ] SSL certificate installed
- [ ] Domain pointed correctly
- [ ] 301 redirects configured (if moving from old site)
- [ ] Analytics set up
- [ ] Monitoring configured
- [ ] Backup strategy in place
- [ ] Emergency contact list prepared

## Support

For deployment issues:
1. Check your web host documentation
2. Review server logs
3. Consult the platform-specific documentation
4. Contact technical support

---

**Keep this guide handy for deployment and troubleshooting!**
