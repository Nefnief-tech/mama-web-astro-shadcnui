# 🚀 Deployment Guide

This guide covers different ways to deploy Mama's Website to various hosting platforms.

## 📋 Pre-Deployment Checklist

Before deploying, ensure:

- [ ] All pages load correctly in development
- [ ] Mobile navigation works properly
- [ ] Build completes without errors: `npm run build`
- [ ] Preview works correctly: `npm run preview`
- [ ] All links are working
- [ ] Contact form behavior is as expected
- [ ] Meta tags and SEO are properly configured

## 🏗️ Build Process

The website is built as a static site that can be deployed anywhere:

```bash
# Install dependencies
npm install

# Build for production
npm run build

# The dist/ folder contains your deployable site
```

### Build Output

After running `npm run build`, you'll find:
- `dist/` - Static files ready for deployment
- `dist/index.html` - Homepage
- `dist/about/index.html` - About page
- `dist/contact/index.html` - Contact page
- `dist/_astro/` - JavaScript and CSS assets

## 🌐 Hosting Platforms

### 1. Netlify (Recommended)

Netlify is perfect for Astro sites with excellent DX and features.

#### Option A: Git Integration (Recommended)

1. **Connect Repository**:
   - Go to [Netlify](https://netlify.com)
   - Click "New site from Git"
   - Connect your GitHub repository

2. **Configure Build Settings**:
   ```
   Build command: npm run build
   Publish directory: dist
   ```

3. **Environment Variables** (if needed):
   ```
   NODE_VERSION=18
   ```

4. **Deploy**: Netlify automatically builds and deploys on every push

#### Option B: Manual Deploy

1. **Build locally**:
   ```bash
   npm run build
   ```

2. **Upload dist folder** to Netlify:
   - Drag and drop `dist` folder to Netlify dashboard
   - Or use Netlify CLI:
   ```bash
   npm install -g netlify-cli
   netlify deploy --prod --dir=dist
   ```

#### Netlify Features

- **Custom domain**: Add your own domain
- **SSL certificate**: Automatic HTTPS
- **Form handling**: Built-in form processing for contact form
- **Redirects**: Configure in `netlify.toml`:

```toml
[[redirects]]
  from = "/*"
  to = "/index.html"
  status = 404
```

### 2. Vercel

Great performance and developer experience.

#### Option A: Git Integration

1. **Connect Repository**:
   - Go to [Vercel](https://vercel.com)
   - Import your GitHub repository

2. **Auto-detected settings** (Vercel detects Astro automatically):
   ```
   Framework Preset: Astro
   Build Command: npm run build
   Output Directory: dist
   Install Command: npm install
   ```

3. **Deploy**: Automatic deployment on push

#### Option B: Vercel CLI

```bash
# Install Vercel CLI
npm install -g vercel

# Deploy from project root
vercel --prod
```

### 3. GitHub Pages

Free hosting directly from your GitHub repository.

#### Setup Steps

1. **Create GitHub Action**:
   Create `.github/workflows/deploy.yml`:

```yaml
name: Deploy to GitHub Pages

on:
  push:
    branches: [ main ]
  workflow_dispatch:

permissions:
  contents: read
  pages: write
  id-token: write

concurrency:
  group: "pages"
  cancel-in-progress: false

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout
        uses: actions/checkout@v4
      
      - name: Setup Node.js
        uses: actions/setup-node@v4
        with:
          node-version: '18'
          cache: 'npm'
      
      - name: Install dependencies
        run: npm ci
      
      - name: Build site
        run: npm run build
      
      - name: Upload artifact
        uses: actions/upload-pages-artifact@v3
        with:
          path: ./dist

  deploy:
    environment:
      name: github-pages
      url: ${{ steps.deployment.outputs.page_url }}
    runs-on: ubuntu-latest
    needs: build
    steps:
      - name: Deploy to GitHub Pages
        id: deployment
        uses: actions/deploy-pages@v4
```

2. **Enable GitHub Pages**:
   - Go to repository Settings > Pages
   - Source: GitHub Actions
   - Save

3. **Update base URL** (if using subdirectory):
   In `astro.config.mjs`:
   ```javascript
   export default defineConfig({
     site: 'https://yourusername.github.io',
     base: '/repository-name', // if not using custom domain
     // ... other config
   })
   ```

### 4. Cloudflare Pages

Fast global CDN with excellent performance.

#### Setup Steps

1. **Connect Repository**:
   - Go to [Cloudflare Pages](https://pages.cloudflare.com)
   - Connect your GitHub repository

2. **Build Settings**:
   ```
   Framework preset: Astro
   Build command: npm run build
   Build output directory: dist
   Root directory: /
   ```

3. **Environment Variables**:
   ```
   NODE_VERSION=18
   ```

### 5. Firebase Hosting

Google's hosting platform with global CDN.

#### Setup Steps

1. **Install Firebase CLI**:
   ```bash
   npm install -g firebase-tools
   ```

2. **Initialize Firebase**:
   ```bash
   firebase login
   firebase init hosting
   ```

3. **Configure `firebase.json`**:
   ```json
   {
     "hosting": {
       "public": "dist",
       "ignore": [
         "firebase.json",
         "**/.*",
         "**/node_modules/**"
       ],
       "rewrites": [
         {
           "source": "**",
           "destination": "/index.html"
         }
       ]
     }
   }
   ```

4. **Deploy**:
   ```bash
   npm run build
   firebase deploy
   ```

### 6. AWS S3 + CloudFront

Enterprise-grade hosting on AWS.

#### Setup Steps

1. **Create S3 Bucket**:
   - Enable static website hosting
   - Upload `dist` contents

2. **Configure CloudFront**:
   - Create distribution pointing to S3
   - Configure custom error pages

3. **Deploy with AWS CLI**:
   ```bash
   aws s3 sync dist/ s3://your-bucket-name --delete
   aws cloudfront create-invalidation --distribution-id YOUR_DISTRIBUTION_ID --paths "/*"
   ```

## 🔧 Environment-Specific Configuration

### Production Optimizations

In `astro.config.mjs`:

```javascript
export default defineConfig({
  // Production site URL
  site: 'https://your-domain.com',
  
  // Optimize for production
  vite: {
    build: {
      minify: 'terser',
      terserOptions: {
        compress: {
          drop_console: true,
          drop_debugger: true
        }
      }
    }
  },
  
  integrations: [
    vue(),
    tailwind({
      applyBaseStyles: false,
    }),
  ],
})
```

### Custom Domain Setup

#### For Netlify:
1. Add domain in Netlify dashboard
2. Update DNS records as instructed

#### For Vercel:
1. Add domain in Vercel dashboard
2. Configure DNS records

#### For GitHub Pages:
1. Add `CNAME` file to `public/` folder:
   ```
   your-domain.com
   ```
2. Configure DNS to point to GitHub Pages

## 📧 Contact Form Integration

### Netlify Forms (Recommended for Netlify)

Update `src/pages/contact.astro`:

```html
<form name="contact" method="POST" data-netlify="true" netlify-honeypot="bot-field">
  <input type="hidden" name="form-name" value="contact" />
  <p class="hidden">
    <label>Don't fill this out: <input name="bot-field" /></label>
  </p>
  <!-- Your existing form fields -->
</form>
```

### Formspree (Universal)

1. **Sign up** at [Formspree](https://formspree.io)
2. **Update form action**:
   ```html
   <form action="https://formspree.io/f/YOUR_FORM_ID" method="POST">
     <!-- Your form fields -->
   </form>
   ```

### Custom API Integration

For dynamic backends, you can integrate with:
- Supabase
- Firebase
- Custom Node.js/Python API

## 🚀 Continuous Deployment

### Automatic Deployments

Most platforms support automatic deployment:

1. **Push to main branch** triggers build
2. **Build process** runs automatically
3. **Site updates** when build succeeds

### Deploy Previews

Platforms like Netlify and Vercel create preview deployments for:
- Pull requests
- Feature branches
- Development builds

## 🔍 Monitoring & Analytics

### Add Analytics

1. **Google Analytics**:
   Add to `src/layouts/Layout.astro`:
   ```html
   <!-- Google tag (gtag.js) -->
   <script async src="https://www.googletagmanager.com/gtag/js?id=GA_MEASUREMENT_ID"></script>
   <script>
     window.dataLayer = window.dataLayer || [];
     function gtag(){dataLayer.push(arguments);}
     gtag('js', new Date());
     gtag('config', 'GA_MEASUREMENT_ID');
   </script>
   ```

2. **Plausible Analytics** (Privacy-friendly):
   ```html
   <script defer data-domain="yourdomain.com" src="https://plausible.io/js/script.js"></script>
   ```

### Performance Monitoring

- **Lighthouse** (built into Chrome DevTools)
- **WebPageTest** for detailed analysis
- **Pingdom** for uptime monitoring

## 🔧 Troubleshooting Deployment

### Common Issues

1. **Build fails**:
   ```bash
   # Check local build
   npm run build
   
   # Clear cache and reinstall
   rm -rf node_modules package-lock.json
   npm install
   ```

2. **404 errors**:
   - Configure redirects for SPA-like behavior
   - Check file paths and routing

3. **Assets not loading**:
   - Verify base URL configuration
   - Check asset paths in build output

4. **Environment variables**:
   - Set NODE_VERSION=18 in hosting platform
   - Check if all required env vars are set

### Debugging Steps

1. **Local preview**:
   ```bash
   npm run build
   npm run preview
   ```

2. **Check build output**:
   - Verify `dist/` folder contents
   - Test static files locally

3. **Platform-specific logs**:
   - Check build logs in hosting dashboard
   - Look for specific error messages

## 📊 Performance Optimization

### Pre-deployment Checklist

- [ ] Images are optimized (WebP format)
- [ ] Unused CSS is purged
- [ ] JavaScript is minified
- [ ] Gzip compression is enabled
- [ ] CDN is configured (if applicable)

### Lighthouse Scores

Aim for:
- **Performance**: 90+
- **Accessibility**: 95+
- **Best Practices**: 90+
- **SEO**: 90+

## 🎉 Post-Deployment

### Final Steps

1. **Test all functionality** on live site
2. **Check mobile responsiveness**
3. **Verify contact form** (if applicable)
4. **Test from different devices/browsers**
5. **Set up monitoring** and analytics
6. **Share the site** with stakeholders

### Maintenance

- **Regular updates**: Keep dependencies updated
- **Monitor performance**: Check Lighthouse scores
- **Backup**: Ensure code is backed up in version control
- **Security**: Monitor for vulnerabilities

---

Congratulations! 🎉 Your beautiful website is now live and accessible to the world!